# 0003 · Google Sheets as the order book for the pilot, Odoo kept ready

**Decided:** 15 September 2026
**Status:** in force for the pilot

## Context

We built two back ends for the order book: Google Sheets, and an Odoo add-on that writes sales orders, customers and a daily capacity record. The Odoo version passed all 18 acceptance checks on 11 September.

## Decision

Run the pilot on Google Sheets. Leave the Odoo code in place and tested.

## Why

The owner already reads a spreadsheet. Odoo is the better system once she wants reports and stock over time, but on day one it's a second thing to learn while she's also learning to trust an agent with her customers. Switching back is one configuration key (`capacity_source`), because the agent talks to the order book through a single interface and neither back end leaks into the bakery logic.

## What we gave up

Proper reporting from day one. End-of-period reports during the pilot come from the sheet.

## Watch out for

Both stores must give the same answers. A capacity rule that worked on Sheets silently failed on Odoo because the two return product names in different shapes. The test for that rule now runs against both shapes.
