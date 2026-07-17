# FruitLife 360 PDFMonkey Template Field Map

Date: 2026-07-17

Template:

`fruitlife-360/templates/pdfmonkey/fruitlife-360-report.html`

Source tab:

`PDFMonkey_Payload_360`

## Core Fields

- `participant_id`
- `participant_name`
- `participant_email`
- `report_date`
- `reviewer_mix`
- `response_count`
- `observer_count`
- `self_overall`
- `observer_overall`
- `overall_gap`
- `most_visible_fruit`
- `encouragement_others_see`
- `growth_invitations`
- `pressure_vulnerabilities`
- `design_id_primary`
- `design_id_secondary`
- `overview_note`

## Fruit Score Fields

Each fruit uses the same six-field pattern:

- `{fruit}_self`
- `{fruit}_observer`
- `{fruit}_self_pressure`
- `{fruit}_observer_pressure`
- `{fruit}_category`
- `{fruit}_summary`

Fruit prefixes:

- `love`
- `joy`
- `peace`
- `patience`
- `kindness`
- `goodness`
- `faithfulness`
- `gentleness`
- `self_control`

## Fruit Formation Fields

Each fruit also uses the expanded formation pattern:

- `{fruit}_tier_label`
- `{fruit}_tier_description`
- `{fruit}_tier_action`
- `{fruit}_scripture`
- `{fruit}_definition`
- `{fruit}_maturity`
- `{fruit}_pressure_pattern`
- `{fruit}_growth_invitation`
- `{fruit}_practice`
- `{fruit}_reflection_question`
- `{fruit}_prayer_prompt`
- `{fruit}_encouragement`

Tier summary fields:

- `most_visible_tier_description`
- `steady_forming_tier_description`
- `growth_invitation_tier_description`
- `most_visible_fruit_list`
- `steady_forming_fruit_list`
- `growth_invitation_fruit_list`

## Written Feedback Fields

- `observer_strength_comments`
- `observer_growth_comments`
- `observer_encouragement_comments`
- `self_final_reflection`

## DesignID / Next-Step Fields

- `design_id_page_title`
- `design_id_page_intro`
- `architect_fruit_lens`
- `artisan_fruit_lens`
- `shepherd_fruit_lens`
- `steward_fruit_lens`
- `design_id_cta`
- `spiritual_gifts_cta`

## First Test Payload

Use the sample participant:

`FL360-SAMPLE`

The live workbook verification confirmed that `PDFMonkey_Payload_360` now resolves 197 payload fields after the FruitLife content expansion.
