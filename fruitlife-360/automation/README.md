# FruitLife 360 Automation Build Pack

Date: 2026-07-17

This folder defines the first wiring plan for moving FruitLife 360 from website/Jotform responses into Google Sheets, then into PDFMonkey.

## Current Build State

- Google Sheet brain is live and has the 360 tabs.
- PDFMonkey HTML template exists in `fruitlife-360/templates/pdfmonkey/fruitlife-360-report.html`.
- This automation pack provides the Jotform field maps, Make scenario blueprint, PDFMonkey request body, and sample payload.
- Live check on 2026-07-29: the PDFMonkey template `FruitLife 360` exists and renders successfully from `FL360-SAMPLE`.
- Superseded live check on 2026-07-29: no Make scenario referenced FruitLife / FL360 / the live FruitLife Sheet ID at that time, so Make was still at blueprint stage.
- Live build on 2026-07-29: `Participant_Setup` and `Report_Queue` now include a controlled `FL360-SAMPLE` row for report-generation testing.
- Live build on 2026-07-29: created FruitLife Jotform forms:
  - Self assessment: `FruitLife 360 Self Assessment`, ID `262096536690162`, URL `https://form.jotform.com/262096536690162`
  - Observer reflection: `FruitLife 360 Observer Reflection`, ID `262096700619156`, URL `https://form.jotform.com/262096700619156`
- Live build on 2026-07-29: patched the live Sheet top-level 360 summary formulas and the `Report_Export_360` handoff so `Encouragement_Others_See`, `Growth_Invitations`, and `Pressure_Vulnerabilities` generate report-ready summary language instead of blanks.
- Live PDFMonkey sample on 2026-07-29: document `18f5aa92-3143-43d7-89e1-e483da48c836` generated successfully from the corrected live Sheet export.
- Live update on 2026-07-31: added `Fruit_Rank_1` through `Fruit_Rank_9` as far-right columns on `Response_Intake` so the full Sortable List order can be preserved without disturbing existing report formulas. Make should parse Jotform `typeA` into those columns and derive the legacy top/growth fields from the same ordered list.
- Live wiring audit on 2026-07-31: the current PDFMonkey template uses 168 payload variables, and all 168 now exist in `PDFMonkey_Payload_360`. `Report_Export_360` formation-library and DesignID copy formulas were filled down through row 500, and `Pressure_Vulnerabilities` now returns fallback language when no major pressure gap exists. A fresh live Sheet payload render for `FL360-6612531259974069585` succeeded as PDFMonkey document `e2a07c7d-c2b0-4fca-9a38-5c77022e1eb5`.
- Live tiered-formation pass on 2026-07-31: added `Fruit_Tier_Formation_360` with 27 tier-specific formation rows. `Report_Export_360` rows 2-500 now pull maturity, growth invitation, practice, and prayer copy by each fruit's assigned tier while keeping scripture/definition fields stable. PDFMonkey document `f3e7f5b9-e6e2-4427-95df-94e545941a5f` rendered successfully from the live payload.
- Free tripwire automation build started on 2026-07-31. Added right-side support headers to `Participant_Setup` and `Report_Queue`; created Make scenario `5823420` named `FruitLife 360 - Report Queue Runner - DRAFT`, with all current named payload fields mapped into PDFMonkey template `84de6c4d-e279-42e5-a5cc-28248d1149dd`. John created the signup form manually after Jotform API creation was blocked; live signup form `262116654473054` is connected to Make hook `2642649`, and Make scenario `5823630` writes signup rows to `Participant_Setup` and `Report_Queue` and emails the self/observer links. See `make/free-tripwire-flow-contract.md`.
- Live launch on 2026-07-31: activated the FruitLife signup intake (`5823630`), self intake (`5823856`), observer intake (`5823857`), and report queue runner (`5823420`) Make scenarios. Jotform webhooks are attached for signup, self, and observer forms. Controlled Michael Willoughby test `FL360-6613479139972243544` completed end-to-end: signup row, self response, two observer responses, workbook payload, PDFMonkey document `df4a9947-282d-498d-9565-9649372a76d0`, Dropbox upload `/FruitLife 360 Reports/FruitLife 360 - Michael Willoughby - FL360-6613479139972243544.pdf`, and report email status `SENT`.

## Files

- `jotform/self-assessment-field-map.md`
- `jotform/observer-assessment-field-map.md`
- `jotform/jotform-field-spec.json`
- `make/make-scenario-blueprint.md`
- `make/make-scenario-modules.json`
- `make/free-tripwire-flow-contract.md`
- `pdfmonkey/create-document-request.sample.json`
- `samples/fl360-sample-payload.json`

## Recommended Build Order

1. Keep the live Jotform signup URL published where leads should enter.
2. Watch `Participant_Setup`, `Response_Intake`, and `Report_Queue` for the first few real submissions.
3. Confirm one real non-test participant receives the signup email, self link, observer link, and final PDF.
4. If the report template changes, run another controlled PDFMonkey test before leaving the runner active.

## Important IDs To Collect

- Jotform self form ID: `262096536690162`
- Jotform observer form ID: `262096700619156`
- Jotform signup form ID: `262116654473054`
- Google Sheet ID: `1V39OQTm-yzdYogq-qv8me5f_LCOVKUur26mURfQSMc8`
- PDFMonkey template ID: `84de6c4d-e279-42e5-a5cc-28248d1149dd`
- Make signup intake scenario ID: `5823630`
- Make self intake scenario ID: `5823856`
- Make observer intake scenario ID: `5823857`
- Make report queue runner scenario ID: `5823420`

## Safety

Keep monitoring after launch:

- The sample PDF renders cleanly.
- One real test dataset works end-to-end.
- The observer invite/link behavior is confirmed.
- The Make scenarios remain active and do not leave rows stuck in `PROCESSING`.
