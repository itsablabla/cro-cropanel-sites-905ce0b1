# CTA Disconnected Offering — dev spec
Site: example.com · Priority 5 · Medium · Effort: Medium (2-5 days)

## Problem
The only CTA links to a documentation site and does not reference any product or value, leaving the visitor without a clear next step.

## Evidence (from the live site)
> The only call to action on the page is “Learn more”.
> [Learn more](https://iana.org/domains/example)

## Current state
h1: Example Domain; cta: Learn more (external); notes: CTA not tied to offering.

## Required change
h1: Example Domain; cta: [Benefit-oriented CTA]; notes: Replace generic Learn more with benefit-oriented CTA that names the offering and value.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Replace generic Learn more with benefit-oriented CTA that names the offering and value.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_cta_disconnected_from_offering` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
