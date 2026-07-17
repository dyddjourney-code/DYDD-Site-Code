# FruitLife 360 Make Scenario Blueprint

This is the first Make scenario plan. It is written as a build guide, not a direct Make import export.

## Scenario 1: Self Submission Intake

Trigger:

- Jotform watch submissions: FruitLife 360 Self Assessment

Steps:

1. Generate `Participant_ID`
   - Suggested format: `FL360-{{submissionID}}`
2. Generate `Invite_Token`
   - Use Make random string or hash of participant ID + submission ID.
3. Add participant to `Participant_Setup`
   - name, email, assessment mode, status, created date, self form link, observer form link.
4. Add self response to `Response_Intake`
   - `Review_Type` = `Self`
   - `Reviewer_Group` = `Self`
5. Add self row to `Reviewer_Roster_360`
   - status `Submitted`
6. Build observer invite link
   - include `participant_id`
   - include `invite_token`
7. Send confirmation email to participant
   - include observer link to share with trusted reviewers.

## Scenario 2: Observer Submission Intake

Trigger:

- Jotform watch submissions: FruitLife 360 Observer Reflection

Steps:

1. Read hidden `participant_id` and `invite_token`.
2. Look up participant in `Participant_Setup`.
3. Normalize reviewer group from relationship.
4. Add observer response to `Response_Intake`.
5. Add or update reviewer row in `Reviewer_Roster_360`.
6. Count responses for participant.
7. If 1 self + 3 observers are present, mark report ready.
8. Otherwise stop.

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

## Readiness Rule

Minimum for a full report:

- 1 self response
- 3 observer responses

This can later become configurable from `Assessment_Config`.

