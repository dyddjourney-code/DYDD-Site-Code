# FruitLife 360 Back-Map From DC3 Leadership Design 360

Date: 2026-07-17

## Source Pattern

The DC3 Leadership Design 360 prototype gives us the right production pattern:

- a setup tab for the person being reviewed
- a raw intake tab for every respondent
- a standardized bridge layer
- a question bank
- score aggregation by reviewer group
- section/category aggregation
- open feedback grouping
- final reflection grouping
- report-ready data
- PDFMonkey payload fields
- a report queue

The DC3 report uses reviewer groups:

- Self
- Supervisor
- Peer
- Direct Report

The FruitLife product should keep the same engine, but change the public language. FruitLife is spiritual formation, not a workplace performance review, so the default reviewer language should be:

- Self
- Observers
- Close Relationships
- Ministry / Team Relationships
- Optional Mentor / Leader

For a church or organization version, we can still map these to supervisor, peer, and direct-report internally, but the report should feel like reflection and formation rather than evaluation.

## What Transfers Directly

The following DC3 mechanics transfer cleanly into FruitLife 360:

- one report subject per report
- multiple respondents tied to the same subject
- one row per respondent in intake
- question codes that make formulas stable
- averages by category
- self score separated from observer averages
- gap logic between self and others
- highlighted awareness patterns
- grouped written feedback
- final reflection prompts
- PDFMonkey payload generated from one selected report row

## What Changes For FruitLife

DC3 sections become the nine fruit:

1. Love
2. Joy
3. Peace
4. Patience
5. Kindness
6. Goodness
7. Faithfulness
8. Gentleness
9. Self-control

DC3 "blind strength" and "blind spot" language should become softer:

- `Encouragement Others See`: observers score a fruit higher than self.
- `Growth Invitation`: self score is higher than observers, or both self and observers show lower visibility.
- `Awareness Gap`: self and observer ratings differ enough to warrant reflection.
- `Shared Strength`: self and observers both see a fruit as consistently visible.
- `Pressure Vulnerability`: consistency is strong, but pressure score drops.

Recommended awareness-gap threshold:

- DC3 used 2.0+ on a 1-5 scale because leadership questions were direct performance indicators.
- FruitLife should start with 1.0+ as a "notice this" gap and 1.5+ as a major gap.
- The report language should never say the fruit is absent or that the person is spiritually deficient.

## Report Shape To Emulate

FruitLife 360 should follow the DC3 report flow:

1. Cover page
2. How to read this report
3. Reviewer mix and response count
4. Overall FruitLife snapshot
5. Fruit summary table
6. Most visible fruit
7. Encouragement others see
8. Growth invitations
9. Fruit-by-fruit detail pages
10. Written encouragement and reflection responses
11. Optional DesignID expression lens
12. Prayer, next steps, and growth plan

## Core Report Tables

The main report table should show one row per fruit:

- Fruit
- Self consistency
- Observer consistency
- Self under pressure
- Observer under pressure
- Awareness gap
- Report language category

The detail page for each fruit should show:

- three statements from the question bank
- self average
- observer average
- pressure average
- top observer comments, if collected
- a short formation prompt
- a short prayer or next step

## Reviewer Mix Recommendation

For the first full product, require:

- 1 self response
- 3 observer responses minimum

Optional labels for observers:

- Spouse / family
- Close friend
- Ministry teammate
- Leader / mentor
- Person I serve or lead
- Other

This gives the user a true 360 feel without forcing workplace hierarchy onto a discipleship tool.

## DesignID Integration

DesignID should enrich FruitLife after the core FruitLife result is stable.

The report should use DesignID to answer:

- How might this fruit naturally express through this person's design?
- Where could this design overuse or underuse the fruit?
- What kind of practice would fit this person's wiring?

DesignID should not change the fruit scores.

