# Out-of-stock notification form — dev spec
Site: allbirds.com · Priority 8 · High · Effort: Medium (2-5 days)

## Problem
The product page for the Anytime Ankle Sock shows a 'Get Notified' CTA, indicating the item is out of stock, but the form likely only captures an email, missing the opportunity to capture size preference and reduce friction for back-in-stock alerts.

## Evidence (from the live site)
> The product page CTAs include 'Get Notified' (from inventory: ctas: ['Shop All', 'Get Notified', 'Learn More', 'Sign Up', 'Shop + -']). The page also has a form with 1 input (likely email) and no labels (from inventory: forms: [{n_inputs: 1, labels: [], submit: 'Sign Up'}]).

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: Single email field for back-in-stock alert, no size selection or product variant capture.

## Required change
h1: Anytime Ankle Sock; cta: Get Notified; notes: Add a size selector (or pre-filled from product page) and a note like 'We'll email you when this size is back in stock' to capture intent and reduce friction for the customer.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a size selector (or pre-filled from product page) and a note like 'We'll email you when this size is back in stock' to capture intent and reduce friction for the customer.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_out_of_stock_notification_form` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
