# FruitLife 360

FruitLife 360 is the Discover Your Divine Design assessment/report experience built around the fruit of the Spirit in Galatians 5:22-23.

The first build should produce a complete self-assessment report. The later build can add peer/observer feedback so it becomes a true 360 experience.

## Current Source

- `docs/working-brief.md` preserves the existing FruitLife 360 product and build brief.
- `docs/google-sheet-audit-2026-07-17.md` summarizes the current Google Sheet state.
- `docs/v1-implementation-plan.md` gives the recommended build order.
- `source/fruitlife360-google-sheet-export-2026-07-17.xlsx` is a read-only export snapshot of the current Google Sheet.

## Core Guardrail

This assessment should not sound like it is grading holiness or telling someone they are deficient. The report language should emphasize visible fruit, steady development, and current growth invitations from the Holy Spirit.

## Recommended Build Path

1. Finalize the v1 assessment model.
2. Complete the Google Sheet calculation/report tabs.
3. Lock the `PDFMonkey_Payload` field names.
4. Build the PDFMonkey report template.
5. Wire Make only after the Sheet and payload contract are stable.
6. Generate and review one complete sample report.
