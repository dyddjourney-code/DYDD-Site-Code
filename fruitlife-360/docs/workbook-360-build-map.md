# FruitLife 360 Workbook Build Map

Date: 2026-07-17

## Build Posture

The connected workbook already has a good base:

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

Do not overwrite the live reporting tabs immediately. First add 360-specific build tabs beside the current tabs, test them, then promote them once the report works.

Recommended new tabs:

- `Reviewer_Roster_360`
- `Score_Aggregates_360`
- `Fruit_Aggregates_360`
- `Open_Feedback_360`
- `Final_Reflection_360`
- `Report_Data_360`
- `Report_Export_360`
- `PDFMonkey_Payload_360`

## Participant Setup

`Participant_Setup` should become the control center for the report subject.

Required fields:

- `Participant_ID`
- `Full_Name`
- `Email`
- `Assessment_Mode`
- `Target_Observer_Count`
- `Minimum_Observer_Count`
- `DesignID_Status`
- `DesignID_Primary`
- `DesignID_Secondary`
- `Report_Status`
- `Created_At`
- `Ready_For_Report`

## Reviewer Roster

Add `Reviewer_Roster_360` so each invited observer can be tracked without mixing invite status into response data.

Recommended fields:

- `Participant_ID`
- `Reviewer_ID`
- `Reviewer_Name`
- `Reviewer_Email`
- `Reviewer_Relationship`
- `Reviewer_Group`
- `Invite_Status`
- `Invite_Sent_At`
- `Submitted_At`
- `Response_ID`

Default `Reviewer_Group` values:

- `Self`
- `Observer`
- `Close Relationship`
- `Ministry / Team`
- `Mentor / Leader`

## Response Intake

`Response_Intake` should hold one row per submitted response.

Required fields:

- `Response_ID`
- `Participant_ID`
- `Reviewer_ID`
- `Respondent_Name`
- `Respondent_Email`
- `Review_Type`
- `Reviewer_Relationship`
- `Reviewer_Group`
- `Submitted_At`
- 27 consistency question responses
- 9 pressure question responses
- Most visible fruit choices
- Growth focus choices
- Open encouragement response
- Growth invitation response
- Optional final prayer / formation response

The current workbook already has the basic self and peer wording. The main upgrade is adding stable IDs, normalized reviewer groups, and pressure fields.

## Question Bank

`Question_Bank` should keep the existing 27 questions and add metadata.

Recommended fields:

- `Question_ID`
- `Fruit`
- `Question_Order`
- `Question_Type`
- `Self_Wording`
- `Observer_Wording`
- `Report_Label`
- `Active`

Question types:

- `Consistency`
- `Pressure`
- `Ranking`
- `Open_Response`

If pressure questions are added as separate scored fields, use stable IDs like:

- `LOVE_P1`
- `JOY_P1`
- `PEACE_P1`

## Score Aggregates

Add `Score_Aggregates_360` for question-level math.

One row per participant + question.

Recommended fields:

- `Participant_ID`
- `Question_ID`
- `Fruit`
- `Self_Score`
- `Observer_Avg`
- `Close_Relationship_Avg`
- `Ministry_Team_Avg`
- `Mentor_Leader_Avg`
- `All_Observer_Avg`
- `Awareness_Gap`
- `Gap_Category`

Gap category formulas:

- `Shared Strength`: self and observers both high.
- `Encouragement Others See`: observers exceed self by threshold.
- `Growth Invitation`: self exceeds observers by threshold.
- `Aligned Developing`: self and observers both mid or lower.

## Fruit Aggregates

Add `Fruit_Aggregates_360` for one row per participant + fruit.

Recommended fields:

- `Participant_ID`
- `Fruit`
- `Self_Consistency_Avg`
- `Observer_Consistency_Avg`
- `Self_Pressure_Avg`
- `Observer_Pressure_Avg`
- `Consistency_Gap`
- `Pressure_Gap`
- `Pressure_Drop`
- `Fruit_Category`
- `Rank_Self`
- `Rank_Observer`
- `Report_Order`

## Open Feedback

Add `Open_Feedback_360` to collect observer text without making the payload formulas unmanageable.

Recommended fields:

- `Participant_ID`
- `Reviewer_Group`
- `Reviewer_Relationship`
- `Prompt`
- `Response_Text`
- `Include_In_Report`

Recommended prompts:

- What fruit do you most clearly see in this person?
- Where do you see a growth invitation for this person?
- What encouragement should this person hear from this reflection?

## Report Data And Export

`Report_Data_360` should be the clean calculation layer.

`Report_Export_360` should be one row per participant, ready for Make and PDFMonkey.

Required export sections:

- participant identity
- reviewer mix
- response counts
- overall snapshot
- fruit summary rows
- top visible fruit
- encouragement others see
- growth invitations
- pressure vulnerabilities
- open feedback
- DesignID lens
- next steps

## PDFMonkey Payload

`PDFMonkey_Payload_360` should mirror the DC3 payload shape but with FruitLife names.

Recommended top-level fields:

- `report.title`
- `report.subtitle`
- `report.date`
- `participant.name`
- `participant.email`
- `reviewerMix`
- `scale`
- `overviewNote`
- `fruitSummary`
- `visibleFruit`
- `encouragementOthersSee`
- `growthInvitations`
- `pressureVulnerabilities`
- `fruitDetails`
- `feedback`
- `designIdLens`
- `nextSteps`

## First Live Build Sequence

1. Back up the current workbook export.
2. Add the 360-specific tabs.
3. Add one sample participant and one self response.
4. Add three sample observer responses.
5. Build aggregate formulas.
6. Build `Report_Export_360`.
7. Build `PDFMonkey_Payload_360`.
8. Generate one test payload.
9. Build the PDFMonkey template.
10. Run one end-to-end Make test.

## Google Cloud / Sheet Access Note

No additional Google Cloud setup is needed for additional Sheets right now.

To give this agent access to another specific workbook, share that workbook with:

`openclaw-sheets-access@rich-access-502717-f2.iam.gserviceaccount.com`

Use Viewer for audit-only access and Editor only when live workbook edits are approved.

