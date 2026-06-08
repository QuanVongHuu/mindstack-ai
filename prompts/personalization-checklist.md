# Personalization Checklist

Replace every private user-input value before running or publishing these prompts. Leave assistant-generated placeholders in the output templates unless a prompt explicitly tells you to replace them.

## Personal Details Found In The Original Workflow

| Original type | Why it is private/specific | Public replacement |
|---|---|---|
| User name: `Quan` / `Quân` | Personal identity and assignee matching | `{{USER_NAME}}`, `{{ASSIGNEE_NAMES}}` |
| Timezone: `GMT+7, ICT` | May be wrong for other users | `{{TIMEZONE}}` |
| Real local Obsidian path, for example `C:\Users\YourName\Documents\YourVault\` | Reveals machine username and vault location; may also be blocked by Windows Defender write protection | `{{OBSIDIAN_VAULT_PATH}}` |
| Daily note path: `Daily/DD-MM-YYYY.md` | Depends on the user's vault structure | `{{DAILY_NOTE_FOLDER}}/{{DATE_FORMAT}}.md` |
| Exact Google Sheet IDs | Gives access targets and exposes private workflow names | `{{SPREADSHEET_ID_OR_URL_1}}`, `{{SPREADSHEET_ID_OR_URL_2}}` |
| Subject/project sheet names | Specific to one school/work context | `{{SHEET_NAME_1}}`, `{{SHEET_NAME_2}}` |
| Assignee filter: rows containing `Quân` or `Quan` | Specific to one person's task ownership | `{{ASSIGNEE_NAMES}}` |
| Sheet read mode: assigned-only or read-all | Specific workflow rule | `Read mode` column in the sheet table |
| Vietnamese column names: `Nội dung`, `Mô tả`, `Deadline`, `Phụ trách`, `Trạng thái` | Depends on each user's sheet schema | `{{TASK_COLUMN}}`, `{{DESCRIPTION_COLUMN}}`, `{{DEADLINE_COLUMN}}`, `{{ASSIGNEE_COLUMN}}`, `{{STATUS_COLUMN}}` |
| Tool name: `read_file_content` | Depends on connector/MCP implementation | `{{GOOGLE_DRIVE_READ_TOOL}}` |

## Minimum Fields To Replace

- `{{INSTALL_TARGET}}` - only needed for `one-prompt-installer.md`.
- `{{OUTPUT_MODE}}` - only needed for `one-prompt-installer.md`.
- `{{USER_NAME}}`
- `{{TIMEZONE}}`
- `{{OBSIDIAN_VAULT_PATH}}`
- `{{DAILY_NOTE_FOLDER}}`
- `{{DATE_FORMAT}}` - default daily note filename format: `DD-MM-YYYY`.
- `{{EMAIL_LOOKBACK_HOURS}}`
- `{{CALENDAR_LOOKAHEAD_DAYS}}`
- `{{GOOGLE_DRIVE_READ_TOOL}}`
- `{{ASSIGNEE_NAMES}}`
- `{{SHEET_NAME_1}}`, `{{SHEET_NAME_2}}`
- `{{SPREADSHEET_ID_OR_URL_1}}`, `{{SPREADSHEET_ID_OR_URL_2}}`
- `{{TASK_COLUMN}}`
- `{{DESCRIPTION_COLUMN}}`
- `{{DEADLINE_COLUMN}}`
- `{{ASSIGNEE_COLUMN}}`
- `{{STATUS_COLUMN}}`

## Assistant-Generated Placeholders

Do not replace these before running the prompt. The assistant fills them from the system date, connector results, or user answers:

- `{{TODAY_ISO_DATE}}`
- `{{TODAY_DISPLAY_DATE}}`
- `{{TODAY_DATE_IN_DATE_FORMAT}}`
- `{{YESTERDAY_DATE_IN_DATE_FORMAT}}`
- `{{DAY_1}}` through `{{DAY_7}}`

## Safe Example Sheet List

Use fake IDs in public examples:

```markdown
| Sheet name | Spreadsheet ID or URL | Read mode | Notes |
|---|---|---|---|
| Example Course Tasks | `1fakeSpreadsheetIdExampleA` | assigned-only | Match rows where assignee contains `Linh` or `Linh Nguyen` |
| Team Project Tracker | `https://docs.google.com/spreadsheets/d/1fakeSpreadsheetIdExampleB/edit#gid=0` | read-all | Show all rows with a deadline |
```

## Optional OpenCode And Composio Fields

These are only needed if you follow the low-code setup in [`../docs/03-opencode-mcp-composio-setup.md`](../docs/03-opencode-mcp-composio-setup.md).

- `{{COMPOSIO_USER_ID}}`
- `{{COMPOSIO_MCP_URL}}`
- `COMPOSIO_API_KEY` as a local environment variable, not as public Markdown text.
- `{{GMAIL_ACCOUNT_LABEL}}`
- `{{CALENDAR_ACCOUNT_LABEL}}`
- `{{DRIVE_ACCOUNT_LABEL}}`
- `{{SHEETS_ACCOUNT_LABEL}}`

## Final Privacy Check

Before publishing, search your repo for:

- `C:\Users\`
- `sk-`
- `AIza`
- `docs.google.com/spreadsheets/d/`
- Your real name, email, phone number, and school/work identifiers.
