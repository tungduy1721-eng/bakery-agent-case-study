# Operating model

Three parties: the customer, the agent and the owner. The agent talks to both sides by message. The order book sits behind it.

## What reaches the owner's phone

Each of these arrives as a card carrying a short order code (for example `#B7K`), so she can answer several at once without mixing them up.

| Trigger | What she sees | What she does |
|---|---|---|
| Draft order complete | Order, address, two preset fee buttons | Taps a fee, or types one |
| Customer accepts the total | Approve / Edit / Reject | One tap |
| Allergy or ingredient question | The customer's question, word for word | Types an answer; the agent forwards it to the customer word for word |
| Item with no price in the menu | The item and the customer's question | Types the price |
| Day's capacity would be exceeded | "Not confirmed yet", with what's left | Decides; the agent has not promised anything |
| Delivered | Reminder to check the bank once the customer sends the transfer screenshot | Checks |

The agent never answers an allergy question itself and never invents a price. Both rules are enforced in code, not left to the prompt.

## Commands she can type

- `đơn` lists open orders waiting on her
- `vào` takes over the conversation; the agent goes quiet
- `trả lại` hands it back to the agent
- `B9T 14cm` edits order B9T; the agent reads the new order back to the customer and sends her a fresh approval card

## What goes to the order book

One row per confirmed order: product, size, quantity, unit price, total including delivery, district, delivery date and time, order code and delivery fee. Rows are only ever appended at the end; columns are never inserted in the middle of a sheet she's already using.

## Capacity

The shop bakes up to 20 whole cakes a day and keeps 6 back for same-day sales, so up to 14 can be pre-ordered. The agent checks this while talking to the customer, not only when writing the order, so nobody hears "confirmed" for a cake that can't be baked. Cups and slices have their own daily limits and don't count against the 20. All of these numbers are placeholders until the owner confirms them.

At 22:00 the system plans the next day's bake; at 05:30 it confirms the plan and opens same-day sales.
