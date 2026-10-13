# 0002 · Deploy on one channel before connecting more

**Decided:** 14 September 2026, by Jayce
**Status:** in force

## Context

The owner sells through Messenger and Instagram. A multi-channel inbox tool (Pancake, widely used by Vietnamese online sellers) would have given the agent every channel at once and given her a familiar screen for taking over conversations.

## Decision

Not yet. Put the agent on a server on the current channel first, lock down how the owner and agent work together, and add the multi-channel layer when we run more than one platform for real.

## Why

Every bug we'd found so far was in the order logic and in how the system remembered a conversation, not in the channel. Adding a third-party layer before the interaction model was settled would have doubled the places a failure could hide, and we'd have been debugging someone else's webhooks instead of our own order flow.

## What we gave up

The owner keeps answering Instagram herself during the pilot, and her takeover screen is Messenger, not a dedicated inbox.

## What this did not touch

No line of the bakery's domain pack, its configuration, its tests or its eval set changed because of this decision. That's the point of keeping channel and business logic apart.
