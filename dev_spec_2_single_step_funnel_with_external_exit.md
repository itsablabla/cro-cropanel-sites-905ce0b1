# Single-Step External Funnel — dev spec
Site: example.com · Priority 2 · High · Effort: Medium (2-5 days)

## Problem
The homepage offers only one CTA that exits to an external domain, creating a shallow funnel with no internal next step.

## Evidence (from the live site)
> The only call to action on the page is “Learn more”.
> [Learn more](https://iana.org/domains/example)

## Current state
h1: Example Domain; cta: Learn more (external link); notes: Only one CTA, no internal path.

## Required change
h1: Example Domain; cta: Primary: [Benefit-oriented CTA] Secondary: Learn more; notes: Add an internal conversion-oriented CTA (e.g., Sign up, Request demo) and keep Learn more as secondary.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add an internal conversion-oriented CTA (e.g., Sign up, Request demo) and keep Learn more as secondary.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_single_step_funnel_with_external_exit` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
