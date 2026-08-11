# Free shipping threshold hidden — dev spec
Site: allbirds.com · Priority 4 · Urgent · Effort: Low (0.5-2 days)

## Problem
The homepage hero promotes 'Wildly Comfortable. Super Natural.' without any mention of the $100 free shipping threshold, which is only disclosed in the sitewide banner and cart, creating an expectation gap that may lead to cart abandonment.

## Evidence (from the live site)
> Homepage body sample includes 'Free ground shipping on orders over $100' in the top banner, but the hero H1 is 'Wildly Comfortable. Super Natural.' with CTAs 'SHOP MEN' and 'SHOP WOMEN' that do not reference shipping. The cart drawer shows 'Spend more to earn free shipping! Shipping $5.00'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: No mention of free shipping threshold in hero or CTAs.

## Required change
h1: Wildly Comfortable. Super Natural. Free Shipping Over $100.; cta: SHOP MEN / SHOP WOMEN; notes: Add free shipping threshold to hero or subheadline to set expectations early.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add free shipping threshold to hero or subheadline to set expectations early.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_free_shipping_threshold_hidden` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
