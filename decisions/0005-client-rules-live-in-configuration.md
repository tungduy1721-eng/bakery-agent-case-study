# 0005 · Client-specific rules live in a domain pack, never in the core

**Decided:** at the platform's design, reaffirmed on every release
**Status:** in force

## Decision

The core (the conversation engine, the reply worker, the webhook handler, the operator dashboard) must not know what a cake, a size or a delivery fee is. Everything specific to one client lives in a domain pack and a configuration file: menu, prices, FAQ in the owner's own words, tone of voice, capacity rules, hand-off rules.

## Why this is a business rule, not a coding preference

Every time someone writes a bakery rule into the core, the next client becomes a custom project instead of a new configuration file. For a small implementation team, that's the difference between a service that scales and one that doesn't. A second domain pack (a music school) runs on the same core as the check that the boundary holds.

## How we enforce it

In review, a search for bakery vocabulary in the core services should return nothing. One fallback still writes shop-specific Vietnamese text from the core; removing it is on the backlog.

## Example of it paying off

Selling by the cup and the slice (15 September) needed a capacity exemption: eight slices from one cake shouldn't use up eight of the day's 20 cakes. It was added as a flag on the size in configuration, read by the pack. The core didn't change.
