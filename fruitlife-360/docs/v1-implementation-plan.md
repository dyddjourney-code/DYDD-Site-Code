# FruitLife 360 V1 Implementation Plan

## V1 Product Shape

The first version should be called either:

- Fruit of the Spirit Reflection
- FruitLife 360 Self Reflection

Use the 360 name when the peer/observer version is ready.

## V1 Inputs

Participant fields:

- Name
- Email
- Optional DesignID status
- Optional self-selected DesignID reflection

Assessment fields:

- 27 fruit rating questions
- Most visible fruit 1-3
- Growth focus fruit 1-3
- Optional final reflection: "Which fruit do you most desire the Holy Spirit to grow in you during this season?"

Optional future fields:

- Pressure/stress rating for each fruit
- Peer reviewer relationship
- Peer comments
- DesignID email lookup result

## V1 Output Sections

1. Welcome and theological frame
2. FruitLife snapshot
3. Most visible fruit
4. Steady developing fruit
5. Growth invitation fruit
6. Fruit-by-fruit score summary
7. Personal growth focus
8. Optional DesignID expression lens
9. Prayer/reflection prompts
10. Suggested next steps

## Google Sheet Work

1. Confirm final intake fields.
2. Complete per-fruit score formulas in `Report_Data`.
3. Populate `Report_Export` from the selected participant/self row.
4. Add report language lookups from `Assessment_Config`.
5. Add optional DesignID fields and fallback language.
6. Complete `PDFMonkey_Payload`.
7. Add a sample participant response for testing.

## Make Work

Do not wire Make until the Sheet payload is stable.

Once stable:

1. Trigger on form submission or queued report row.
2. Read the selected row from `PDFMonkey_Payload`.
3. Send payload to PDFMonkey.
4. Store returned PDF URL.
5. Email or deliver the report.

## PDFMonkey Work

Build the template after the payload field names are locked.

Use a clean report design similar to the existing DYDD assessment reports, with careful language that avoids shame, labels, or spiritual ranking.

## DesignID Integration

DesignID should enrich the report, not gate the report.

Priority:

1. Email lookup from DesignID result data, if available.
2. Self-selected DesignID reflection.
3. No DesignID, standalone FruitLife report.

Fallback language:

> Your FruitLife report is complete on its own. If you complete DesignID later, you can unlock an added layer showing how this fruit may uniquely express through the way God designed you.
