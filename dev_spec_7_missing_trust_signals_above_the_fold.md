# Missing Trust Signals — dev spec
Site: example.com · Priority 7 · High · Effort: Medium (2-5 days)

## Problem
The homepage lacks crucial trust signals above the fold, increasing perceived purchase risk for visitors.

## Evidence (from the live site)
> Measured on the live homepage: no match for returns policy, guarantee, reviews, security badge.

## Current state
notes: absent: returns policy, guarantee, reviews, security badge

## Required change
notes: Surface review counts, the returns window and a guarantee near the primary call to action.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Surface review counts, the returns window and a guarantee near the primary call to action.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_missing_trust_signals_above_the_fold` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
