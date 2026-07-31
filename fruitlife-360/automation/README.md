# FruitLife 360 Automation Build Pack

Date: 2026-07-17

This folder defines the first wiring plan for moving FruitLife 360 from website/Jotform responses into Google Sheets, then into PDFMonkey.

## Current Build State

- Google Sheet brain is live and has the 360 tabs.
- PDFMonkey HTML template exists in `fruitlife-360/templates/pdfmonkey/fruitlife-360-report.html`.
- This automation pack provides the Jotform field maps, Make scenario blueprint, PDFMonkey request body, and sample payload.
- Live check on 2026-07-29: the PDFMonkey template `FruitLife 360` exists and renders successfully from `FL360-SAMPLE`.
- Live check on 2026-07-29: no Make scenario currently references FruitLife / FL360 / the live FruitLife Sheet ID, so Make is still at blueprint stage.
- Live build on 2026-07-29: `Participant_Setup` and `Report_Queue` now include a controlled `FL360-SAMPLE` row for report-generation testing.
- Live build on 2026-07-29: created FruitLife Jotform forms:
  - Self assessment: `FruitLife 360 Self Assessment`, ID `262096536690162`, URL `https://form.jotform.com/262096536690162`
  - Observer reflection: `FruitLife 360 Observer Reflection`, ID `262096700619156`, URL `https://form.jotform.com/262096700619156`
- Live build on 2026-07-29: patched the live Sheet top-level 360 summary formulas and the `Report_Export_360` handoff so `Encouragement_Others_See`, `Growth_Invitations`, and `Pressure_Vulnerabilities` generate report-ready summary language instead of blanks.
- Live PDFMonkey sample on 2026-07-29: document `18f5aa92-3143-43d7-89e1-e483da48c836` generated successfully from the corrected live Sheet export.
- Live update on 2026-07-31: added `Fruit_Rank_1` through `Fruit_Rank_9` as far-right columns on `Response_Intake` so the full Sortable List order can be preserved without disturbing existing report formulas. Make should parse Jotform `typeA` into those columns and derive the legacy top/growth fields from the same ordered list.
- Live wiring audit on 2026-07-31: the current PDFMonkey template uses 168 payload variables, and all 168 now exist in `PDFMonkey_Payload_360`. `Report_Export_360` formation-library and DesignID copy formulas were filled down through row 500, and `Pressure_Vulnerabilities` now returns fallback language when no major pressure gap exists. A fresh live Sheet payload render for `FL360-6612531259974069585` succeeded as PDFMonkey document `e2a07c7d-c2b0-4fca-9a38-5c77022e1eb5`.

## Files

- `jotform/self-assessment-field-map.md`
- `jotform/observer-assessment-field-map.md`
- `jotform/jotform-field-spec.json`
- `make/make-scenario-blueprint.md`
- `make/make-scenario-modules.json`
- `pdfmonkey/create-document-request.sample.json`
- `samples/fl360-sample-payload.json`

## Recommended Build Order

1. Create the Jotform self-assessment form.
2. Create the Jotform observer form.
3. Confirm or refresh the live PDFMonkey `FruitLife 360` template against the repo HTML.
4. Build the Make scenarios from the blueprint.
5. Run another `FL360-SAMPLE` PDFMonkey test after any template changes.
6. Submit one real self response and three observer responses.
7. Confirm the Sheet says the report is ready.
8. Trigger the PDFMonkey document generation.

## Important IDs To Collect

- Jotform self form ID: `262096536690162`
- Jotform observer form ID: `262096700619156`
- Google Sheet ID: `1V39OQTm-yzdYogq-qv8me5f_LCOVKUur26mURfQSMc8`
- PDFMonkey template ID: `84de6c4d-e279-42e5-a5cc-28248d1149dd`
- Make scenario ID: not yet live; Make remains the next wiring stage.

## Safety

Do not connect the public website until:

- the sample PDF renders cleanly
- one real test dataset works end-to-end
- the observer invite/link behavior is confirmed
