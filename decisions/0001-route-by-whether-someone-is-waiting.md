# 0001 · Route work by whether someone is waiting

**Decided:** 14 September 2026, by Jayce (product owner)
**Status:** in force

## Context

By mid-September the agent could hand the owner a growing list of things: delivery fees, order approvals, allergy questions, edits, payment checks, stock for tomorrow. We also had a working Odoo back office. The open question was where each of these should land. One option put everything in Odoo so she had a single place to look; another put everything in Messenger because that's where she already lives.

Both fail. Everything-in-Odoo means a customer waits while the owner opens a laptop and logs in. Everything-in-Messenger turns her phone into a stream of bookkeeping notifications at 11pm.

## Decision

The dividing line is whether a person is waiting on the answer.

If a customer is waiting mid-conversation, it goes to the owner as a Messenger card with buttons: delivery fee, order approval, allergy, unpriced item, change or cancellation. If nobody is waiting, it goes to the back office: delivery confirmation, payment matching, tomorrow's stock, far-future orders, editing customer details, closing the books.

The phone is where she reacts when someone is waiting. The back office is where she works when she chooses to sit down. Two modes, not two competing tools.

## What we gave up

A single inbox for everything. She has two places to look, and we have to keep the split obvious so nothing sits in the wrong one.

## How we'll know it's right

During the pilot, every hand-off that a customer was waiting on should be answered from her phone, and her answer time on those cards is tracked (see [`docs/pilot-plan.md`](../docs/pilot-plan.md)). If she ends up opening the back office to unblock a waiting customer, the line is in the wrong place.
