# How we test the agent

One file of scenarios drives two layers of testing, so there's only ever one definition of "correct".

The first layer runs on every code change: no model, no network, about a second and a half. It checks the order logic. Does a complete conversation produce a draft order, does the capacity check block at the right moment, does the owner's card go out, can a returning customer place a second order. Scenarios for behaviour we want but haven't built are marked as expected failures, so the scenario file doubles as the backlog: when one starts passing, the test run says so.

The second layer runs when the prompt or the model changes, because it calls the real model and costs money. It scores every generated reply on three things: under 30 words (checked by code), at most one question per turn (checked by code), and whether it sounds like the owner or like a virtual assistant (graded by a model against a rubric). Hard rules from the scenarios are checked on top: never address the customer as "quý khách", never ask for payment before the order is confirmed, never state a delivery fee the owner hasn't given.

As of 15 September the scenario file held 31 scenarios generating 30 model-graded tests, with 508 tests in the first layer.

[`scenarios.md`](scenarios.md) shows three scenarios rewritten for this repository. They are illustrative: the names, phone numbers and addresses are invented, and the replies show the expected shape rather than exact model output.
