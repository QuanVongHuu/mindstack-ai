# Morning Routine

The morning routine is one component of mindstack-ai. It creates a daily command center before you start the day.

## Inputs

- Yesterday's daily note.
- Gmail from the last 24 hours.
- Calendar events for today and the next 7 days.
- Google Sheets tasks.
- Manual additions from the user.

## Output

A Markdown daily note with:

- This Week table.
- Gmail Summary.
- Carried Over tasks.
- Today's To-Dos.
- Evening Reflection placeholder.
- AI Context Layer for due-today and upcoming tasks.

For a filled fake prompt, see [`../examples/sample-morning-routine-prompt.md`](../examples/sample-morning-routine-prompt.md). For a complete fake output example, see [`../examples/sample-daily-morning-routine-Report.md`](../examples/sample-daily-morning-routine-Report.md).

## Setup Steps

1. Open [`../prompts/morning-routine.md`](../prompts/morning-routine.md).
2. Replace all user-input placeholders.
3. Paste into Claude Cowork.
4. Run manually.
5. Check the generated note.
6. Adjust the prompt until the output matches your workflow.
7. Schedule it.

## Important Customizations

Change these before running:

- Name and timezone.
- Obsidian vault path or synced Markdown folder path.
- Daily note folder and filename format.
- Gmail lookback window.
- Calendar lookahead window.
- Google Sheet list.
- Assignee names.
- Sheet column names.
- Which sheets are `assigned-only` vs `read-all`.

On Windows, use a vault folder that your AI writing tool can modify. Windows Defender Controlled Folder Access can block writes to protected folders such as `Desktop`, `Documents`, or some synced folders.

## Good First Test

Use only one Google Sheet first. After it works, add the rest.

This makes failures easier to debug.

## Expected Behavior

The assistant should not finalize the to-do list immediately. It should first show urgent items and ask:

```text
Anything to add to today's to-do list?
```

Only after your reply should it sort and finalize `Today's To-Dos`.
