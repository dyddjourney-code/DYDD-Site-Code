# FruitLife 360 Google Sheet Audit

Date: 2026-07-17

Sheet reviewed from:
`https://docs.google.com/spreadsheets/d/1V39OQTm-yzdYogq-qv8me5f_LCOVKUur26mURfQSMc8/edit?usp=sharing`

Review mode: read-only export.

## Tabs Found

- `START_HERE`
- `Assessment_Config`
- `Question_Bank`
- `Participant_Setup`
- `Response_Intake`
- `Report_Queue`
- `Report_Data`
- `Report_Export`
- `Report_Control`
- `PDFMonkey_Payload`
- `Version_Notes`

## What Is Strong

- The workbook has a good DPG-style reporting spine.
- The `Question_Bank` includes 27 fruit statements: 9 fruit x 3 statements each.
- The question wording already has self and peer language, which supports the future 360 version.
- The tone is generally aligned with the FruitLife guardrail: visible fruit, reflection, growth focus, and spiritual formation.
- The `PDFMonkey_Payload` tab already mirrors the report export pattern used in other assessment systems.

## Current Gaps

- The later FruitLife brief calls for ranking + consistency + pressure. The current Sheet has the 27 rating questions and simple forced choices for most visible/growth focus, but does not yet include full 1-9 ranking or separate pressure/stress ratings.
- `Report_Data` is still a placeholder.
- `Report_Export` has headers and some partial formulas, but most report fields are not calculated yet.
- `Peer_Overall` currently contains an incomplete formula placeholder.
- `PDFMonkey_Payload` references `Report_Export`, but it is not ready until the report export layer is completed.
- Optional DesignID enrichment fields are not built into the workbook yet.

## Recommendation

Build the first usable version as a self-assessment report, then add peer/360 functionality after one full self-report works end-to-end.

The fastest v1 is:

- Keep the 27 rating questions.
- Keep simple `Most_Visible_1-3` and `Growth_Focus_1-3` fields instead of full drag-and-drop ranking.
- Add pressure/stress ratings only if the first report needs deeper coaching insight.
- Complete `Report_Data`, `Report_Export`, and `PDFMonkey_Payload`.
- Create one sample row and run a PDFMonkey report test.
