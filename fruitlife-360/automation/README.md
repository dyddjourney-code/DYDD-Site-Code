# FruitLife 360 Automation Build Pack

Date: 2026-07-17

This folder defines the first wiring plan for moving FruitLife 360 from website/Jotform responses into Google Sheets, then into PDFMonkey.

## Current Build State

- Google Sheet brain is live and has the 360 tabs.
- PDFMonkey HTML template exists in `fruitlife-360/templates/pdfmonkey/fruitlife-360-report.html`.
- This automation pack provides the Jotform field maps, Make scenario blueprint, PDFMonkey request body, and sample payload.

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
3. Paste the PDFMonkey HTML into a new `FruitLife 360 Report` template.
4. Create the Make scenario from the blueprint.
5. Run the `FL360-SAMPLE` PDFMonkey test.
6. Submit one real self response and three observer responses.
7. Confirm the Sheet says the report is ready.
8. Trigger the PDFMonkey document generation.

## Important IDs To Collect

Add these later when accounts are created:

- Jotform self form ID
- Jotform observer form ID
- Google Sheet ID
- PDFMonkey template ID
- Make scenario ID

## Safety

Do not connect the public website until:

- the sample PDF renders cleanly
- one real test dataset works end-to-end
- the observer invite/link behavior is confirmed

