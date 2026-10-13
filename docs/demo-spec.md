# Reviewer sandbox: specification

**Status:** planned. Not built yet.

A reviewer should be able to try the system in a few minutes without a Facebook account and without touching the real shop.

## What gets built

A single web page with two panes. On the left, the reviewer types as a customer. On the right, they see what the owner receives: the draft order card, the delivery-fee buttons, an allergy question being handed off. The right pane is the point. It shows the hand-off design, which a plain chatbot demo can't.

Behind it, a separate demo shop runs as its own tenant on the same platform, with an invented menu and prices, so nothing reaches the real owner's order book or customers. It gets a reply language setting (English as well as Vietnamese), a reset button that wipes and reseeds the demo data, and a monthly token cap so heavy use can't run up a bill (the platform already enforces per-tenant caps).

Access is by link and passcode, with an expiry date. The link goes to reviewers directly, not into this repository.

A three-minute screen recording of the same flow is kept as a fallback in case the server is down.

## Acceptance tests

1. A reviewer with the link and passcode places a complete order in English in under three minutes.
2. The owner pane shows the draft card with an order code and fee buttons before the customer pane shows a total.
3. Tapping a fee in the owner pane makes the total appear in the customer pane.
4. Typing "does this contain peanuts?" produces an owner card and no answer from the agent until the owner replies; the owner's reply appears in the customer pane word for word.
5. Ordering more than the day's remaining capacity gets "only N left" before anything is promised.
6. Reset returns both panes and the demo order book to empty within ten seconds.
7. No request from the sandbox reads or writes the real shop's tenant (checked in the database after a full run).
8. After the expiry date, the link refuses access.
