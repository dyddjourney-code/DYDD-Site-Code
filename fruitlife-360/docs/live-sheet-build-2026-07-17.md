# FruitLife 360 Live Sheet Build

Date: 2026-07-17

Workbook:

`Fruit of the Spirit Reflection - Master Workbook`

Google Sheet ID:

`1V39OQTm-yzdYogq-qv8me5f_LCOVKUur26mURfQSMc8`

## Backup

A fresh live workbook export was saved before edits:

`fruitlife-360/source/fruitlife360-live-backup-20260717T180646Z.xlsx`

## Live Sheet Changes

The existing workbook tabs were preserved. The 360 build was added beside them.

Tabs added or refreshed:

- `Reviewer_Roster_360`
- `Score_Aggregates_360`
- `Fruit_Aggregates_360`
- `Open_Feedback_360`
- `Final_Reflection_360`
- `Report_Data_360`
- `Report_Export_360`
- `Report_Control_360`
- `PDFMonkey_Payload_360`

The existing `Response_Intake` tab was extended with 360-ready fields:

- `Reviewer_Group`
- `Response_ID`
- `Invite_Token`
- `DesignID_Status`
- `DesignID_Primary`
- `DesignID_Secondary`
- pressure ratings for all nine fruit
- final reflection fields
- observer encouragement / growth invitation fields

## Sample Data

Sample participant:

`FL360-SAMPLE`

The sample includes:

- 1 self response
- 3 observer responses
- observer groups: close relationship, ministry / team, mentor / leader

## Verification

Read-back verification confirmed:

- `Response_Intake` has 70 columns through `BR`.
- `Reviewer_Roster_360` has sample self and observer rows.
- `Score_Aggregates_360` calculates question-level self and observer averages.
- `Fruit_Aggregates_360` calculates all nine fruit rows.
- `Report_Data_360` resolves the sample report row.
- `Report_Export_360` resolves 75 report fields.
- `PDFMonkey_Payload_360` resolves 75 payload fields through `self_final_reflection`.

Sample calculated results:

- response count: 4
- observer count: 3
- self overall: 3.925925926
- observer overall: 4.160493827
- ready for report: Yes
- most visible fruit: Faithfulness, Kindness, Love

## Production Notes

This build is ready for report-template planning and one controlled PDFMonkey payload test.

The Sheet is not yet wired to Jotform, Make, or PDFMonkey. The next production steps are:

1. Finalize the website/Jotform intake fields.
2. Confirm whether observer labels should stay generic or include organization-specific labels.
3. Build the PDFMonkey report template against `PDFMonkey_Payload_360`.
4. Wire Make only after the payload contract is stable.

