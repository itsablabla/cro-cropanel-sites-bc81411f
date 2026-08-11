# Hero CTA ambiguity — dev spec
Site: allbirds.com · Priority 6 · High · Effort: Medium (2-5 days)

## Problem
The hero section's CTAs 'SHOP MEN' and 'SHOP WOMEN' are generic and may not guide users to the most relevant products, reducing click-through.

## Evidence (from the live site)
> Hero section contains 'SHOP MEN' and 'SHOP WOMEN' as primary CTAs, with no specific product or collection mentioned.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: CTAs are broad; users may not know what to expect.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop New Arrivals / Shop Bestsellers; notes: Use CTAs that direct to specific high-intent collections to reduce ambiguity and increase click-through.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Use CTAs that direct to specific high-intent collections to reduce ambiguity and increase click-through.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_hero_cta_ambiguity` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
