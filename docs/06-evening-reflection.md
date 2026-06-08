# Evening Reflection

The evening routine is one component of mindstack-ai. It closes the day and creates continuity for tomorrow.

## Inputs

- Today's daily note.
- Current task checkbox status.
- User answers to four reflection questions.
- Tomorrow's anchor task.

## Output

An updated `Evening Reflection` section in today's note.

## Reflection Flow

The assistant asks one question at a time:

1. How are you feeling right now, mood-wise?
2. How productive did today feel, from 1-10? What made it feel that way?
3. Adaptive follow-up based on mood and productivity.
4. Is there anything you would do differently tomorrow?

Then it asks for one anchor task for tomorrow.

## Why One Question At A Time?

If the assistant asks all questions at once, the reflection becomes shallow. The adaptive third question is where most of the insight comes from.

## Setup Steps

1. Open [`../prompts/evening-reflection.md`](../prompts/evening-reflection.md).
2. Replace all user-input placeholders.
3. Paste into Claude Cowork.
4. Run it on a test daily note.
5. Check whether it updates the right section.
6. Schedule it for your evening routine.

## Anchor Task Rule

The anchor task is one thing you commit to doing first tomorrow.

Keep it small enough to start even on a low-energy morning.
