# Missing Value Proposition — dev spec
Site: example.com · Priority 2 · High · Effort: Low (0.5-2 days)

## Problem
The homepage copy fails to clearly articulate a customer-centric value proposition and differentiation.

## Evidence (from the live site)
> This domain is for use in documentation examples without needing permission.
> Avoid use in operations.
> Example Domain

## Current state
h1: Example Domain; notes: The page's primary copy includes 'This domain is for use in documentation examples without needing permission.' and 'Avoid use in operations.', indicating a technical, administrative focus rather than a customer-facing value proposition or differentiation.

## Required change
h1: A clear, benefit-driven headline; cta: A primary call to action relevant to the stated value; notes: Rewrite headline and body copy to clearly state the product/service, its unique benefits, and differentiation using customer-centric language. Remove technical jargon and administrative notes, replacing them with compelling reasons for the visitor to engage.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Rewrite headline and body copy to clearly state the product/service, its unique benefits, and differentiation using customer-centric language. Remove technical jargon and administrative notes, replacing them with compelling reasons for the visitor to engage.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_missing_value_proposition_differentiation` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
