# FruitLife 360 Free Tripwire Automation Contract

Created: 2026-07-31

## Product Flow

FruitLife 360 free report should run as a lightweight signup-first 360 flow:

1. Participant completes a short setup/signup form.
2. Setup creates a `Participant_ID`, `Invite_Token`, expected observer count, and two prefilled links:
   - self assessment link
   - observer reflection link
3. Participant receives an email with the self link and the shareable observer link.
4. Self assessment submission writes one `Self` row into `Response_Intake`.
5. Observer submissions use the shared URL parameters to attach each observer row to the same participant.
6. When the participant has one self response and the expected observer count, the queue status becomes `QUEUED`.
7. Report runner generates the PDF, stores it, emails it, and writes the document URL/status back to `Report_Queue`.

This avoids the DPG-style due date/roster requirement. For the free tripwire, the user's chosen observer count is the completion rule.

## Needed Forms

### Setup / Signup Form

Status: needed. Jotform API creation was blocked by HTTP 429 during the 2026-07-31 build session.

Recommended fields:

- `participant_name` - full name, required
- `participant_email` - email, required
- `expected_observer_count` - number, required, default/recommended `3`
- `signup_source` - hidden, default `website-free-tripwire`

### Existing Self Assessment

- Form ID: `262096536690162`
- URL: `https://form.jotform.com/262096536690162`
- Hidden URL parameters expected:
  - `participant_id`
  - `invite_token`
  - `assessment_mode=FruitLife 360`
  - `review_type=Self`
  - `reviewer_group=Self`

### Existing Observer Reflection

- Form ID: `262096700619156`
- URL: `https://form.jotform.com/262096700619156`
- Hidden URL parameters expected:
  - `participant_id`
  - `invite_token`
  - `review_type=Peer`

## Google Sheet Changes Added

Live workbook ID: `1V39OQTm-yzdYogq-qv8me5f_LCOVKUur26mURfQSMc8`

Added right-side headers without moving existing columns:

### `Participant_Setup`

- `Expected_Observer_Count`
- `Invite_Token`
- `Signup_Source`

### `Report_Queue`

- `PDFMonkey_Document_ID`
- `PDF_URL`
- `Dropbox_File_Path`
- `Error_Message`
- `Expected_Observer_Count`

## Scenario Architecture

### Scenario A: Setup / Signup Intake

Trigger:

- Jotform setup/signup submission

Actions:

1. Generate `Participant_ID`: `FL360-{{submissionID}}`
2. Generate `Invite_Token`: `INV-{{right(submissionID; 8)}}` or Make random string
3. Build self link:
   - `https://form.jotform.com/262096536690162?participant_id={{Participant_ID}}&invite_token={{Invite_Token}}&assessment_mode=FruitLife%20360&review_type=Self&reviewer_group=Self`
4. Build observer link:
   - `https://form.jotform.com/262096700619156?participant_id={{Participant_ID}}&invite_token={{Invite_Token}}&review_type=Peer`
5. Add row to `Participant_Setup`
6. Add row to `Report_Queue` with:
   - `Self_Complete=No`
   - `Peer_Response_Count=0`
   - `Report_Status=WAITING_FOR_SELF`
   - `Expected_Observer_Count` from setup form
7. Email participant with both links.

### Scenario B: Self Assessment Intake

Trigger:

- Existing self form submission

Actions:

1. Read `participant_id` and `invite_token` from hidden fields.
2. If missing, fallback to `FL360-{{submissionID}}` for internal testing only.
3. Parse Sortable List widget `typeA` into `Fruit_Rank_1` through `Fruit_Rank_9`.
4. Derive:
   - `Most_Visible_1..3` from ranks 1..3
   - `Growth_Focus_1..3` from ranks 7..9
5. Add the self row to `Response_Intake`.
6. Update matching `Participant_Setup` status to `Self Submitted - Waiting for Observers`.
7. Update matching `Report_Queue`:
   - `Self_Complete=Yes`
   - keep `Report_Status=WAITING_FOR_OBSERVERS` unless enough observer rows already exist.

### Scenario C: Observer Intake

Trigger:

- Existing observer form submission

Actions:

1. Read hidden `participant_id` and `invite_token`.
2. Look up participant in `Participant_Setup`.
3. Parse Sortable List widget `typeA` into `Fruit_Rank_1` through `Fruit_Rank_9`.
4. Derive legacy top/growth fields from the rank list.
5. Add observer row to `Response_Intake`.
6. Count observer rows for the participant.
7. Update `Report_Queue.Peer_Response_Count`.
8. If `Self_Complete=Yes` and peer count is greater than or equal to `Expected_Observer_Count`, set `Report_Status=QUEUED`.
9. Otherwise leave `Report_Status=WAITING_FOR_OBSERVERS`.

### Scenario D: Report Queue Runner

Status: built as inactive/on-demand Make draft.

- Scenario ID: `5823420`
- Name: `FruitLife 360 - Report Queue Runner - DRAFT`
- Current state: inactive/on-demand
- Modules:
  1. Google Sheets: find one `Report_Queue` row where `Report_Status=QUEUED`
  2. Google Sheets: mark row `PROCESSING`
  3. Google Sheets: set `Report_Control_360!B2`
  4. Sleep 8 seconds
  5. Google Sheets: read `PDFMonkey_Payload_360`
  6. PDFMonkey: generate document from template `84de6c4d-e279-42e5-a5cc-28248d1149dd`
  7. HTTP: download generated PDF
  8. Dropbox: upload PDF to `/DesignID Reports/FruitLife 360 Free Reports`
  9. Gmail: email participant the attached report
  10. Google Sheets: mark queue row `SENT` and write document/output fields

## Public-Facing Language

Use this on the webpage:

> FruitLife 360 does not generate a one-size-fits-all report. Each report is assembled from a person's unique fruit ranking, self-reflection, observer feedback, consistency patterns, and pressure responses.

Skeptic-friendly explanation:

> This is not a static report with a few swapped paragraphs. The report has a structured content engine behind it. It looks at how all nine fruits rank, which tier each fruit falls into, whether self and observer feedback agree, and whether each fruit stays steady under pressure. That creates a highly individualized report while keeping interpretation grounded and consistent.

