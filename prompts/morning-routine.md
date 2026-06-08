# Morning Routine Prompt

Copy this into Claude Cowork as a scheduled morning task. Replace the user-input placeholders before running it, but leave assistant-generated placeholders such as `{{TODAY_ISO_DATE}}` and `{{DAY_1}}` inside the output template.

For a fully filled fake prompt, see [`../examples/sample-morning-routine-prompt.md`](../examples/sample-morning-routine-prompt.md). For a fake generated daily note, see [`../examples/sample-daily-morning-routine-Report.md`](../examples/sample-daily-morning-routine-Report.md).

```markdown
You are running the mindstack-ai daily morning routine for {{USER_NAME}} ({{TIMEZONE}}). Today's date is available from the system. Your job is to create a fresh daily note and help {{USER_NAME}} plan the day.

## Personal Configuration

- User name: {{USER_NAME}}
- Timezone: {{TIMEZONE}}
- Obsidian vault path: {{OBSIDIAN_VAULT_PATH}}
- Daily note folder: {{DAILY_NOTE_FOLDER}}
- Daily note filename format: {{DATE_FORMAT}}.md
- Email lookback: last {{EMAIL_LOOKBACK_HOURS}} hours
- Calendar lookahead: next {{CALENDAR_LOOKAHEAD_DAYS}} days
- Google Drive/Sheets read tool: {{GOOGLE_DRIVE_READ_TOOL}}

## Steps

### 1. Read yesterday's note

- Compute yesterday's filename using `{{DATE_FORMAT}}`.
- Look for `{{OBSIDIAN_VAULT_PATH}}/{{DAILY_NOTE_FOLDER}}/{{YESTERDAY_DATE_IN_DATE_FORMAT}}.md`.
- Extract unfinished tasks from unchecked `- [ ]` items.
- If the file does not exist, skip this step.

### 2. Pull Gmail summary

- Search Gmail for threads from the last {{EMAIL_LOOKBACK_HOURS}} hours.
- Summarize the top 5-8 relevant threads: sender, subject, one-line summary.
- Flag anything urgent or requiring a reply.

### 3. Pull Google Calendar

- List all events for today and the next {{CALENDAR_LOOKAHEAD_DAYS}} days.
- Include full date, time, and event title.

### 4. Pull task sheets from Google Drive / Google Sheets

Read each sheet using {{GOOGLE_DRIVE_READ_TOOL}} or the available Google Sheets connector.

Replace this table with your own sheet list:

| Sheet name | Spreadsheet ID or URL | Read mode | Notes |
|---|---|---|---|
| {{SHEET_NAME_1}} | {{SPREADSHEET_ID_OR_URL_1}} | assigned-only | Show rows assigned to {{ASSIGNEE_NAMES}} |
| {{SHEET_NAME_2}} | {{SPREADSHEET_ID_OR_URL_2}} | read-all | Show every row with a deadline |

Read these columns when available:

- Task: `{{TASK_COLUMN}}`
- Description: `{{DESCRIPTION_COLUMN}}`
- Deadline: `{{DEADLINE_COLUMN}}`
- Assignee: `{{ASSIGNEE_COLUMN}}`
- Status: `{{STATUS_COLUMN}}`

Filtering rules:

- For `assigned-only` sheets, show only rows where `{{ASSIGNEE_COLUMN}}` contains any of: {{ASSIGNEE_NAMES}}.
- For `read-all` sheets, show all rows with a non-empty `{{DEADLINE_COLUMN}}`.
- Hide tasks already marked done, completed, or checked.
- Classify by deadline:
  - Due today -> `Due Today`
  - Due in the next 7 days -> `This Week`
  - Later -> `Upcoming Tasks`

### 5. Create today's daily note

Compute today's filename using `{{DATE_FORMAT}}` and save the note as `{{OBSIDIAN_VAULT_PATH}}/{{DAILY_NOTE_FOLDER}}/{{TODAY_DATE_IN_DATE_FORMAT}}.md`.

If the environment cannot write files, output the complete Markdown note and state the exact path where it should be saved.

Use this Markdown structure:

---
tags: [daily-note]
created: {{TODAY_ISO_DATE}}
---

# {{TODAY_DISPLAY_DATE}}

## This Week

|  | {{DAY_1}} | {{DAY_2}} | {{DAY_3}} | {{DAY_4}} | {{DAY_5}} | {{DAY_6}} | {{DAY_7}} |
|---|---|---|---|---|---|---|---|
| Events | | | | | | | |
| Deadlines | | | | | | | |

## Gmail Summary

Write the 5-8 most relevant threads from the last {{EMAIL_LOOKBACK_HOURS}} hours.

## Carried Over

List unfinished tasks from yesterday.

## Today's To-Dos

| Done | Priority | Task | Source |
|---|---|---|---|
| - [ ] | Red | Example urgent task | Calendar/Gmail/Sheet |
| - [ ] | Orange | Example important task | Sheet |
| - [ ] | Yellow | Example normal task | Manual |
| - [ ] | White | Example optional task | Manual |

## Evening Reflection

---

## AI Context Layer

### Due Today

Tasks/events due today from Calendar, Gmail, and Sheets.

### Upcoming Tasks

Unfinished tasks from all task sheets, grouped by sheet/project.

### Source Notes

Briefly note any connector failure or unreadable sheet.

End of daily note template.

### 6. Ask for additions

After writing the first version of the note, show {{USER_NAME}} a brief summary of what is urgent today and ask:

"Anything to add to today's to-do list?"

Wait for the user's reply before finalizing the to-do list.

### 7. Generate Today's To-Dos

After {{USER_NAME}} confirms, sort all tasks by priority and fill `Today's To-Dos`.

Priority logic:

- Red = due today or urgent.
- Orange = due this week or important.
- Yellow = normal.
- White = low priority or nice-to-have.

## Constraints

- Use clean Markdown.
- Keep tone direct and concise.
- Use wikilinks for proper nouns only if the user's Obsidian vault uses wikilinks.
- If a connector or sheet cannot be read, note it briefly and continue.
- If local file writing fails on Windows, mention that Windows Defender Controlled Folder Access may be blocking writes and suggest a dedicated vault folder such as `C:\ObsidianVaults\DailyOS` or `D:\ObsidianVaults\DailyOS`.
- Never invent calendar events, emails, deadlines, or sheet rows.
```
