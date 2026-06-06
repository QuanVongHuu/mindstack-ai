# Google Sheets Links

The original workflow uses exact Google Sheet file IDs so Claude does not need to search Drive. This makes the routine faster and less ambiguous.

## How To Get A Google Sheet Link

1. Open your Google Sheet.
2. Click `Share`.
3. Make sure the Google account connected to Claude/Composio can access it.
4. Click `Copy link`.
5. Paste it into your private prompt or config.

## How To Extract The Spreadsheet ID

A Google Sheets URL usually looks like this:

```text
https://docs.google.com/spreadsheets/d/SPREADSHEET_ID/edit#gid=0
```

The spreadsheet ID is the part between `/d/` and `/edit`.

Example with a fake ID:

```text
URL: https://docs.google.com/spreadsheets/d/1fakeSheetIdABC123/edit#gid=0
ID:  1fakeSheetIdABC123
```

## Full Link Or ID?

Use the value your connector supports.

- Claude Drive file tools often work better with exact file IDs.
- Google Sheets API style tools usually ask for `spreadsheetId`.
- Some no-code connectors accept the full URL.

If unsure, store both in your private version:

```markdown
| Sheet name | URL | Spreadsheet ID | Read mode |
|---|---|---|---|
| Example Tasks | https://docs.google.com/spreadsheets/d/1fakeSheetIdABC123/edit#gid=0 | 1fakeSheetIdABC123 | assigned-only |
```

## How To Put Sheets Into The Prompt

Replace this placeholder table:

```markdown
| Sheet name | Spreadsheet ID or URL | Read mode | Notes |
|---|---|---|---|
| {{SHEET_NAME_1}} | {{SPREADSHEET_ID_OR_URL_1}} | assigned-only | Show rows assigned to {{ASSIGNEE_NAMES}} |
| {{SHEET_NAME_2}} | {{SPREADSHEET_ID_OR_URL_2}} | read-all | Show every row with a deadline |
```

With your real private table:

```markdown
| Sheet name | Spreadsheet ID or URL | Read mode | Notes |
|---|---|---|---|
| Marketing Homework | 1yourPrivateSheetId | assigned-only | Show rows assigned to Minh |
| Team Capstone Tracker | 1yourPrivateTeamSheetId | read-all | Show all rows with a deadline |
```

Do not commit the private table to GitHub.

## Recommended Sheet Columns

Your sheet can use English or Vietnamese. The important thing is to tell the prompt the exact names.

| Meaning | English example | Vietnamese example |
|---|---|---|
| Task | `Task` | `Nội dung` |
| Description | `Description` | `Mô tả` |
| Deadline | `Deadline` | `Deadline` |
| Assignee | `Assignee` | `Phụ trách` |
| Status | `Status` | `Trạng thái` |

## Read Modes

Use `assigned-only` when you only want rows assigned to you.

Use `read-all` when the entire sheet matters, such as a team deadline tracker.

## Access Checklist

- The connected Google account can open the sheet.
- The sheet is not blocked by organization policy.
- The connector can read file content, not only file metadata.
- The tab containing tasks is visible.
- The deadline format is consistent.
