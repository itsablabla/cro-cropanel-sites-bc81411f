# Half-size guidance hidden — dev spec
Site: allbirds.com · Priority 9 · High · Effort: Medium (2-5 days)

## Problem
The product page for Anytime Ankle Sock does not display a price or size selector in the rendered crawl, and the collection page's size filter note about half sizes is only in fine print, creating a potential expectation gap for customers expecting standard sizing.

## Evidence (from the live site)
> The product page inventory shows no prices or size selector in the body sample, and the direct_signals for the product page are not provided (only for other pages). The collection page body sample includes 'Most of our shoes only come in full sizes. If you're a half size, select your nearest whole size too.' in the filter section, which is not prominent on product pages.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: No price or size selector visible in the rendered crawl; half-size guidance only in collection filter.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: Ensure price and size selector are visible on product page; add half-size guidance near size selection.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Ensure price and size selector are visible on product page; add half-size guidance near size selection.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_half_size_guidance_hidden` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
