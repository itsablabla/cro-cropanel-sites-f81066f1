# Weak Page Metadata — dev spec
Site: example.com · Priority 3 · Medium · Effort: Medium (2-5 days)

## Problem
Search and social previews are degraded due to missing or poorly optimized page metadata.

## Evidence (from the live site)
> Measured on the homepage: title 0 chars (15-60 recommended); description 0 chars (70-160 recommended); og:title missing, og:image missing.

## Current state
notes: page title (absent); meta description; Open Graph tags

## Required change
notes: Write a 15-60 char title and 70-160 char description per page; add og:title and og:image for link previews.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Write a 15-60 char title and 70-160 char description per page; add og:title and og:image for link previews.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_weak_page_metadata` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
