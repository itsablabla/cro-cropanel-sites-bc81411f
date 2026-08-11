# Shipping delay warning — dev spec
Site: allbirds.com · Priority 3 · Urgent · Effort: Medium (2-5 days)

## Problem
The prominent shipping delay notice creates immediate purchase anxiety, undermining the hero's comfort message and increasing cart abandonment.

## Evidence (from the live site)
> Body sample: 'Due to increased demand, orders may take up to 30 days to ship.'

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: Delay notice appears in top bar, above the hero, without any mitigating trust element.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: Soften the delay with a reassurance line: 'Free shipping & 30-day returns' or 'Orders ship within 30 days – free returns if not perfect.'

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Soften the delay with a reassurance line: 'Free shipping & 30-day returns' or 'Orders ship within 30 days – free returns if not perfect.'
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_shipping_delay_warning` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
