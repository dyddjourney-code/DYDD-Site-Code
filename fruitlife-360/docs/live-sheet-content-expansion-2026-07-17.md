# FruitLife 360 Live Sheet Content Expansion

Date: 2026-07-17

Live workbook:

`Fruit of the Spirit Reflection - Master Workbook`

Spreadsheet ID:

`1V39OQTm-yzdYogq-qv8me5f_LCOVKUur26mURfQSMc8`

## Backup

Before changing the live workbook, an XLSX export was saved:

`fruitlife-360/source/fruitlife360-content-expansion-backup-20260717T192800Z.xlsx`

## Tabs Added

- `Fruit_Content_Library`
- `Fruit_Tier_Language`
- `Fruit_DesignID_Lens`
- `Report_Copy_Blocks`

## Content Added

`Fruit_Content_Library` now contains one row for each fruit:

- Love
- Joy
- Peace
- Patience
- Kindness
- Goodness
- Faithfulness
- Gentleness
- Self-control

Each fruit row includes:

- Scripture references
- Short definition
- Maturity description
- Pressure pattern
- Growth invitation
- Practice
- Reflection question
- Prayer prompt
- Encouragement copy

The report intentionally uses Scripture references rather than long quoted Bible text so the template remains flexible and translation-safe.

## Tier Language

The score report now uses three soft formation tiers:

- `MOST_VISIBLE` -> Most Visible Fruit
- `STEADY_FORMING` -> Steady Forming Fruit
- `GROWTH_INVITATION` -> Growth Invitation Fruit

These are based on observer rank in `Fruit_Aggregates_360`, not as fixed identity labels.

## Formula Updates

`Fruit_Aggregates_360` was expanded through column `R` with:

- `Tier_Code`
- `Tier_Label`
- `Tier_Description`
- `Tier_Action`

`Report_Export_360` and `PDFMonkey_Payload_360` were expanded from the original 75-field payload to 197 fields. The new fields pull content from:

- `Fruit_Content_Library`
- `Fruit_Tier_Language`
- `Report_Copy_Blocks`

## PDF Template Updates

The PDFMonkey template now includes:

- A formation guide tier summary page
- Fruit-by-fruit Scripture, maturity, growth, practice, and reflection content
- A richer DesignID expression lens page
- Invitations to continue into DesignID and Spiritual Gifts

## Verification

Live verification after the update:

- `PDFMonkey_Payload_360` field count: 197
- `FL360-SAMPLE` nonblank payload values: 174
- Fruit content rows present: 9 fruit rows plus header
