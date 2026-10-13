# Pilot plan

The pilot answers one question: is this safe to put in front of the owner's real customers? Growth numbers come later. The targets below are proposed; the owner and I agree the final ones before the pilot starts.

## What we measure

**Order accuracy** matters most. For every test order, a person compares what the customer agreed to with the row in the order book: item, size, quantity, price, date, address. Target: zero mismatches, and zero orders accepted beyond the day's capacity. This is checked by hand on an audit sheet, because no database query knows what the customer meant.

**Hand-offs.** How often the agent brings the owner in, how long she takes to answer a card, and any case where it should have brought her in and didn't (an allergy question, an unpriced item). The last one must be zero. Her answer time matters because in this design she's part of the system: if she takes 40 minutes, the customer waits 40 minutes.

**Reliability.** An external uptime check every few minutes, the share of inbound messages that get a reply, and the slowest 5% of reply times. Target: every message answered, no unanswered gaps.

**Conversation quality.** How often the owner edits or overrides a reply, how often replies run over the 30-word limit, and a blind test: mix ten agent replies with ten of hers and see if she can tell which are which.

**Cost and time.** Model tokens per completed order, and the owner's own estimate of time spent in her inbox before and during the pilot.

## Exit criteria

The agent goes live to real customers when all of these hold:

1. The 13-step end-to-end script passes on the real page (draft, fee, approval, recording, delivery, payment check, takeover and hand-back, allergy hand-off, unpriced item, over-capacity, owner edit).
2. Two consecutive weeks of test orders with zero order-book mismatches and zero missed hand-offs.
3. No unanswered conversation in the same two weeks.
4. The owner says yes.

## What's still open before the pilot clock starts

The owner's Messenger ID in the configuration (without it, her approval buttons are rejected), her confirmation of the daily limits, photos for three cake sizes, an email address for the bake plan, and her two most common delivery fees for the preset buttons.
