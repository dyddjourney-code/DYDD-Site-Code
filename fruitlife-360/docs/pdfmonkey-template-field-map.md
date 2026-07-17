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
- `designid_primary`
- `designid_secondary`
- `overview_note`

## Fruit Fields

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

## Written Feedback Fields

- `observer_strength_comments`
- `observer_growth_comments`
- `observer_encouragement_comments`
- `self_final_reflection`

## First Test Payload

Use the sample participant:

`FL360-SAMPLE`

The live workbook verification confirmed that `PDFMonkey_Payload_360` currently resolves 75 payload fields through `self_final_reflection`.

