# FruitLife 360 Make Scenario Blueprint

This is the first Make scenario plan. It is written as a build guide, not a direct Make import export.

## Scenario 1: Self Submission Intake

Trigger:

- Jotform watch submissions: FruitLife 360 Self Assessment
  - Live form ID: `262096536690162`
  - Live form URL: `https://form.jotform.com/262096536690162`

Steps:

1. Generate `Participant_ID`
   - Suggested format: `FL360-{{submissionID}}`
2. Generate `Invite_Token`
   - Use Make random string or hash of participant ID + submission ID.
3. Add participant to `Participant_Setup`
   - name, email, assessment mode, status, created date, self form link, observer form link.
   - recommended status on self submit: `Self Submitted - Waiting for Observers`
4. Add self response to `Response_Intake`
   - `Review_Type` = `Self`
   - `Reviewer_Group` = `Self`
   - copy participant name/email into reviewer name/email for the self row
   - parse the Jotform Sortable List field `typeA` into `Fruit_Rank_1` through `Fruit_Rank_9`
   - also copy `Fruit_Rank_1` through `Fruit_Rank_3` into the legacy `Most_Visible_1` through `Most_Visible_3` fields
   - copy `Fruit_Rank_7` through `Fruit_Rank_9` into the legacy `Growth_Focus_1` through `Growth_Focus_3` fields
5. Add self row to `Reviewer_Roster_360`
   - status `Submitted`
6. Build observer invite link
   - include `participant_id`
   - include `invite_token`
   - live observer base URL: `https://form.jotform.com/262096700619156`
7. Send confirmation email to participant
   - include observer link to share with trusted reviewers.
8. Add or update `Report_Queue`
   - status `WAITING_FOR_OBSERVERS`
   - self complete `Yes`
   - peer response count `0`

## Scenario 2: Observer Submission Intake

Trigger:

- Jotform watch submissions: FruitLife 360 Observer Reflection
  - Live form ID: `262096700619156`
  - Live form URL: `https://form.jotform.com/262096700619156`

Steps:

1. Read hidden `participant_id` and `invite_token`.
2. Look up participant in `Participant_Setup`.
3. Normalize reviewer group from relationship.
4. Add observer response to `Response_Intake`.
   - parse the Jotform Sortable List field `typeA` into `Fruit_Rank_1` through `Fruit_Rank_9`
   - also copy `Fruit_Rank_1` through `Fruit_Rank_3` into the legacy `Most_Visible_1` through `Most_Visible_3` fields
   - copy `Fruit_Rank_7` through `Fruit_Rank_9` into the legacy `Growth_Focus_1` through `Growth_Focus_3` fields
5. Add or update reviewer row in `Reviewer_Roster_360`.
6. Count responses for participant.
7. If 1 self + 3 observers are present, mark report ready.
8. Otherwise stop.
9. Update `Report_Queue`
   - `READY_TO_GENERATE` when 1 self and 3 observers are present
   - otherwise keep `WAITING_FOR_OBSERVERS`

## Scenario 3: Generate Report

Trigger options:

- Runs after observer intake when report is ready.
- Or watches `Report_Queue` for status `Queued`.

Steps:

1. Set `Report_Control_360` to the participant/report row if needed.
2. Read `PDFMonkey_Payload_360`.
3. Send payload to PDFMonkey Create Document.
4. Poll or retrieve document URL.
5. Write PDF URL/status back to `Report_Queue`.
6. Email participant the PDF link.

## Required Connections

- Jotform
- Google Sheets
- PDFMonkey
- Email provider, likely Gmail or SMTP

## Jotform Ranking Normalization

The live self and observer forms both use Jotform's Sortable List widget. Jotform exposes that widget with the generic field name `typeA`, not the planned sheet field names.

- Self form: `typeA`, question ID `84`
- Observer form: `typeA`, question ID `91`

Normalize the submitted ordered list this way before writing `Response_Intake`:

- `Fruit_Rank_1` = first item in `typeA`
- `Fruit_Rank_2` = second item in `typeA`
- `Fruit_Rank_3` = third item in `typeA`
- `Fruit_Rank_4` = fourth item in `typeA`
- `Fruit_Rank_5` = fifth item in `typeA`
- `Fruit_Rank_6` = sixth item in `typeA`
- `Fruit_Rank_7` = seventh item in `typeA`
- `Fruit_Rank_8` = eighth item in `typeA`
- `Fruit_Rank_9` = ninth item in `typeA`

For backward compatibility with the current report formulas, also derive:

- `Most_Visible_1` = `Fruit_Rank_1`
- `Most_Visible_2` = `Fruit_Rank_2`
- `Most_Visible_3` = `Fruit_Rank_3`
- `Growth_Focus_1` = `Fruit_Rank_7`
- `Growth_Focus_2` = `Fruit_Rank_8`
- `Growth_Focus_3` = `Fruit_Rank_9`

## Readiness Rule

Minimum for a full report:

- 1 self response
- 3 observer responses

This can later become configurable from `Assessment_Config`.
