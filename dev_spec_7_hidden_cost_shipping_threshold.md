# Hidden cost: shipping threshold — dev spec
Site: allbirds.com · Priority 7 · High · Effort: Medium (2-5 days)

## Problem
The product page does not display the $100 free shipping threshold, creating a hidden cost that may deter purchase.

## Evidence (from the live site)
> Product page shows 'Get Notified' CTA and no price or shipping information; site-wide banner mentions free shipping over $100 but not on PDP.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: No price or shipping threshold visible on PDP.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: Display price and free shipping threshold (e.g., 'Free shipping over $100') to reduce uncertainty.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Display price and free shipping threshold (e.g., 'Free shipping over $100') to reduce uncertainty.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_hidden_cost_shipping_threshold` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
