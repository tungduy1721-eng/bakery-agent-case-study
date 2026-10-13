# What broke in testing, and what we changed

## The first real-channel test (13 September)

I ran an order end to end as a customer on a real Instagram thread. The first order went through cleanly. The second order from the same customer, a couple of hours later, failed in six ways:

| # | What the customer saw | Cause | Fix |
|---|---|---|---|
| 1 | Asked for a phone number they'd already given, three times | A stale copy of the conversation's details overwrote the current one | Details are written in exactly one place; everything else reads from it |
| 2 | A question about price got the previous order's confirmation message | Nothing closed an order cycle, so order two inherited order one | Confirmed orders move into an order history; the customer's name, phone and address stay, everything about the order resets |
| 3 | No reply for hours | Nothing alerted anyone when the agent stopped replying | Moved to an always-on server; a watchdog flags any conversation left unanswered, and an external uptime check is planned |
| 4 | A size they'd confirmed got changed by a later question ("still have 10cm?") | Two functions applied the model's output in opposite orders of precedence | Once an order is past draft, saved fields win; changes go through an explicit change request |
| 5 | A photo-only message vanished from the agent's view | Messages without text were dropped from the history | Image-only turns are kept as a placeholder the model can see |
| 6 | Long replies, and the same sentence twice | No length limit, and a duplicated reply path | Hard limit of two short sentences and one question, under 30 words; replies over the limit are regenerated |

None of the six came from the language model. The test suite had 393 passing tests at the time, and none of them caught these, because every test started a fresh conversation and placed one order. Real customers come back.

What changed in how we work: every fix started with a test that failed first, written the way a real customer types, and the most important new test runs two orders through the same conversation. 30 tests were added that day.

## The screen mock-ups (9 September)

We set out to mock up the 13 screens the owner and customer would see, to review the flow with the owner. Because the mock-ups used the exact text the system produces (real prices, real formatting), they turned into the best bug-finding tool of the project. They found three places where the owner should have been asked and wasn't (allergies, unpriced items, edits), and 13 bugs that 240 passing tests hadn't touched.

The worst: "chiều mai" (tomorrow afternoon) was being cut to "chiều" (afternoon), so an order for tomorrow was booked, stocked and planned for today. The date logic had been tested over 400 simulated days, but those tests called it with the full phrase, which had already been cut by the time real messages reached it. One older test was asserting the wrong behaviour as correct.

## Prices from the source, not from conversation (15 September)

When the shop started selling a brownie in two flavours, the price went in from a conversation ("same as the lime cake") as a flat 45,000 VND. The owner's cost sheet, opened later the same day, showed one flavour at 55,000. The agent would have quoted and recorded the lower price on every order of that flavour, and nothing would have raised an error. Prices are now set per flavour from her sheet, and if the flavour isn't known the draft order shows no price, so she sees the gap instead of a wrong number.

## The pattern

All three cases fail silently. The system keeps running, the customer gets a fluent reply, and the error only shows up as a wrong order or lost money. For an agent that sells, the risks worth testing for are the quiet ones.
