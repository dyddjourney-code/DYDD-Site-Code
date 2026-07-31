# FruitLife 360 Observer Jotform Field Map

Purpose: collects observer feedback and attaches it to an existing participant.

Live Jotform:

- Form title: `FruitLife 360 Observer Reflection`
- Form ID: `262096700619156`
- Base URL: `https://form.jotform.com/262096700619156`

## Required Link Parameters

The observer form should receive these from the invite link:

- `participant_id`
- `invite_token`
- optional `reviewer_id`

Example:

`https://form.jotform.com/FORM_ID?participant_id=FL360-12345&invite_token=abc123`

## Core Fields

- `participant_id` - Hidden, populated from URL
- `invite_token` - Hidden, populated from URL
- `review_type` - Hidden, value `Peer`
- `reviewer_name` - Name
- `reviewer_email` - Email
- `relationship` - Dropdown
- `reviewer_group` - Dropdown or Make-normalized value

Recommended relationship options:

- Spouse / family
- Close friend
- Ministry teammate
- Leader / mentor
- Person I serve or lead
- Other

Recommended reviewer group values:

- Close Relationship
- Ministry / Team
- Mentor / Leader
- Other Observer

## Consistency Rating Fields

Source of truth: `Question_Bank_360`, column `Observer_Wording`.

Use the same 27 keys as the self form.

The wording should refer to the participant:

Example:

`This person moves toward others with genuine care, even when it costs time, comfort, or convenience.`

## Pressure Rating Fields

Use the same nine pressure keys:

- `Love_Pressure`
- `Joy_Pressure`
- `Peace_Pressure`
- `Patience_Pressure`
- `Kindness_Pressure`
- `Goodness_Pressure`
- `Faithfulness_Pressure`
- `Gentleness_Pressure`
- `SelfControl_Pressure`

Observer prompt frame:

How visible is this fruit when this person is under pressure?

## Ranking Fields

The observer form now uses Jotform's Sortable List widget for the full fruit order.
As of 2026-07-31, the live widget field name is `typeA` and the widget question ID is `91`.
Parse the submitted ordered list into `Fruit_Rank_1` through `Fruit_Rank_9` in the Sheet/Make normalization layer.

Allowed fruit values:

- Love
- Joy
- Peace
- Patience
- Kindness
- Goodness
- Faithfulness
- Gentleness
- Self-control

## Written Responses

- `Peer_Comment_Strength`
- `Peer_Comment_Growth`
- `Peer_Comment_Encouragement`

Recommended prompts:

- What fruit do you most clearly see in this person?
- Where do you see a growth invitation for this person?
- What encouragement should this person hear from this reflection?

## Make Mapping Into `Response_Intake`

- `Timestamp` from Jotform submission time
- `Participant_ID` from hidden URL field
- `Participant_Name` looked up from Google Sheets
- `Review_Type` = `Peer`
- `Reviewer_Name` from form
- `Reviewer_Email` from form
- `Relationship` from form
- `Reviewer_Group` normalized from relationship
- consistency, pressure, full ranking, and comment fields map by exact key

## Live Verification

2026-07-31 wording sync:

- Backed up the live form before edits.
- Verified all 27 visibility fields and 9 pressure fields exist by exact scoring key.
- Verified all scored question text matches `Question_Bank_360!Observer_Wording`.
- Fixed the Peace card order so `PEACE_01`, `PEACE_02`, `PEACE_03`, and `Peace_Pressure` appear together before the Peace page break.
