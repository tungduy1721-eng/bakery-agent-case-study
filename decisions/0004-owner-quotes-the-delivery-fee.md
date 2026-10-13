# 0004 · The owner quotes the delivery fee; the agent pauses

**Decided:** August 2026, by Jayce
**Status:** in force

## Context

Before an order can be locked, the owner checks the fee on a delivery app, tells the customer, and ships only once they agree. The obvious automation is to have the agent look up the fee itself.

## Decision

The agent stops before this step. It sends the owner a card with the order code, the address and two preset fee buttons, and waits. When she taps a fee, the agent tells the customer the total and carries on.

## Why

Delivery-app prices change by time of day, weather and distance, and a wrong quote is a promise the shop has to keep or break. The owner can check in ten seconds what would take us weeks to model reliably. More importantly, this pause isn't specific to one bakery: almost every online seller's flow has one step where a human has to look at something outside the system before committing. Designing the pause well is reusable across every client we take on; automating one courier's pricing isn't.

## What we gave up

The customer waits for the owner's tap. During the pilot we track how long that takes.

## Later

After six to eight weeks of real orders, the order book will hold enough fee-by-district history for the agent to say "usually 25–30k" up front while the owner confirms. Whether to move to a flat delivery price is her business decision, not ours.
