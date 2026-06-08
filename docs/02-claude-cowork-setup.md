# Claude Cowork Setup

Use this guide for the no-code setup. It is written for people who do not want to configure MCP servers, local tools, or code.

Button names can change slightly between Claude releases. If your screen uses a different label, look for the closest label such as `Connectors`, `Integrations`, `Tools`, `Add connector`, `Create task`, or `Schedule`.

## Important Account Rule

Claude connectors do not have to use the same email as your Claude account.

Each connector uses its own sign-in flow. For example, you can:

- Log in to Claude with your personal email.
- Connect Gmail from a school account.
- Connect Google Calendar from a work account.
- Connect Google Drive or Sheets from another Google account.

The account that matters is the account you choose on the connector permission screen, usually after clicking `Continue with Google` or `Choose another account`.

If a sheet, calendar, or folder belongs to a different account, either connect that account or share the file with the connected account.

## What You Need Before Starting

- A Claude account with access to Claude Cowork, scheduled tasks, or an equivalent workflow feature.
- The Gmail account you want the assistant to read.
- The Google Calendar account you want the assistant to read.
- The Google Drive or Google Sheets account that can access your task sheets.
- An Obsidian vault, or a synced Markdown folder that Obsidian can open.
- On Windows, a vault path that is not blocked by Windows Defender Controlled Folder Access, or an allowlisted app that can write there.
- The prompts in [`../prompts/`](../prompts/).

## 1. Create The Morning Task

1. Open Claude in your browser or desktop app.
2. Open the area for scheduled work. This may be called `Claude Cowork`, `Tasks`, `Scheduled tasks`, or `Automations`.
3. Click `New`, `Create task`, `New task`, or the `+` button.
4. Name the task `mindstack-ai Morning Routine`.
5. Open [`../prompts/morning-routine.md`](../prompts/morning-routine.md).
6. Copy the prompt text inside the fenced code block.
7. Paste it into the task instruction box.
8. Replace every user-input placeholder with your real private values.
9. Set the schedule to run every morning, for example `7:00 AM` in your timezone.
10. Click `Save`, `Create`, or `Schedule`.

Do not turn on the final schedule until you have run the task manually once.

## 2. Create The Evening Task

1. Go back to the same `Tasks`, `Scheduled tasks`, or `Automations` area.
2. Click `New`, `Create task`, `New task`, or the `+` button.
3. Name the task `mindstack-ai Evening Reflection`.
4. Open [`../prompts/evening-reflection.md`](../prompts/evening-reflection.md).
5. Copy the prompt text inside the fenced code block.
6. Paste it into the task instruction box.
7. Replace every user-input placeholder with your real private values.
8. Set the schedule to run every evening, for example `9:00 PM` in your timezone.
9. Click `Save`, `Create`, or `Schedule`.

The evening task should run after the morning task has already created today's daily note.

## 3. Open The Connector Settings

You usually connect apps from Claude settings or from inside the task editor.

Try this path first:

1. Click your profile picture, initials, or account menu.
2. Click `Settings`.
3. Look for `Connectors`, `Integrations`, or `Connected apps`.
4. Click `Add connector`, `Connect app`, or `Browse connectors`.

If you are inside a task editor, also check for:

- `Tools`.
- `Add tools`.
- `Connect apps`.
- `Attach connector`.

You need to connect Gmail, Google Calendar, and Google Drive or Google Sheets before the workflow can read your real data.

## 4. Connect Gmail

1. In the connector list, choose `Gmail`.
2. Click `Connect` or `Add`.
3. A Google sign-in window should open.
4. Choose the Gmail account you want Claude to read.
5. If the account is not listed, click `Use another account`.
6. Review the permissions.
7. Click `Allow` if the permissions match what you expect.
8. Return to Claude and confirm Gmail shows as connected.

Recommended prompt behavior:

- Read only the last 24 hours by default.
- Summarize 5-8 important threads.
- Flag urgent or reply-needed messages.
- Do not expose sensitive email content in shared examples.

Test message:

```text
Can you check whether the Gmail connector is available? Do not summarize private content yet. Just tell me whether you can access recent email metadata.
```

## 5. Connect Google Calendar

1. In the connector list, choose `Google Calendar`.
2. Click `Connect` or `Add`.
3. Choose the Google account that owns the calendar you want to use.
4. If your calendar is in a different Google account than Gmail, choose that different account here.
5. Review the permissions.
6. Click `Allow`.
7. Return to Claude and confirm Calendar shows as connected.

Recommended prompt behavior:

- Read today and the next 7 days.
- Include date, time, and event title.
- Treat fixed calendar events differently from flexible tasks.

Test message:

```text
Can you check whether the Calendar connector is available? Do not list private events yet. Just tell me whether you can access today's calendar.
```

## 6. Connect Google Drive And Google Sheets

Use this connector for task sheets and, if needed, Markdown files stored in Google Drive.

1. In the connector list, choose `Google Drive`, `Google Sheets`, or `Google Workspace`.
2. Click `Connect` or `Add`.
3. Choose the Google account that can access your task sheets.
4. If your task sheets are owned by another account, either choose that account or share the sheets with the account you are connecting.
5. Review the permissions.
6. Click `Allow`.
7. Return to Claude and confirm Drive or Sheets shows as connected.

Recommended prompt behavior:

- Use exact spreadsheet IDs or URLs instead of Drive search when possible.
- Match rows assigned to your name.
- Define exceptions for team sheets where every row matters.
- Continue even if one sheet fails.

See [`04-google-sheets-links.md`](04-google-sheets-links.md) for how to copy sheet URLs and IDs.

Test message:

```text
Can you check whether the Drive or Sheets connector is available? Do not read private rows yet. Just tell me whether you can access the connector.
```

## 7. Connect Obsidian Or Markdown Storage

Claude cannot automatically write to a random local folder unless your Claude environment has a file connector that supports local files. For most no-code users, the easiest path is to store Markdown files in a synced folder that Obsidian can open.

On Windows, local write tools can be blocked by Windows Defender Controlled Folder Access. If file writing fails even when the path looks correct, create the vault in a dedicated folder such as `C:\ObsidianVaults\DailyOS` or `D:\ObsidianVaults\DailyOS`, or allowlist the app that writes the Markdown files.

Choose one option.

### Option A: Obsidian Vault In A Synced Folder

Use this if you want no-code setup.

1. Create an Obsidian vault in a synced folder such as Google Drive, Dropbox, iCloud, or OneDrive.
2. Open Obsidian.
3. Click `Open folder as vault` or `Create new vault`.
4. Choose the synced folder.
5. Inside the vault, create a folder named `Daily`.
6. Connect Claude to the same storage provider, for example Google Drive.
7. In the prompt, set `{{DAILY_NOTE_FOLDER}}` to `Daily/`.

This lets Claude write Markdown files through the cloud storage connector, then Obsidian reads those files from the synced folder.

### Option B: Local Obsidian Vault Through OpenCode

Use this if you want local file control.

1. Keep your Obsidian vault on your computer, preferably outside Windows Defender protected folders such as `Desktop` or `Documents` if local tools need write access.
2. Use OpenCode to open the vault or this repo folder.
3. Configure MCP or other tools only if needed.
4. Continue with [`03-opencode-mcp-composio-setup.md`](03-opencode-mcp-composio-setup.md).

This is the low-code path. It is more powerful, but it requires local setup.

### Option C: Manual Copy-Paste

Use this if connector writing does not work yet.

1. Run the morning task in Claude.
2. Ask Claude to output the daily note as Markdown.
3. Copy the Markdown.
4. Create the daily note manually in Obsidian.
5. Paste the Markdown.

This is not automated, but it is the safest first test.

## 8. Fill The Required Placeholders

Use placeholders in public docs, but replace them in your private Claude task.

```text
{{USER_NAME}}
{{TIMEZONE}}
{{OBSIDIAN_VAULT_PATH}}
{{DAILY_NOTE_FOLDER}}
{{DATE_FORMAT}}
{{EMAIL_LOOKBACK_HOURS}}
{{CALENDAR_LOOKAHEAD_DAYS}}
{{GOOGLE_DRIVE_READ_TOOL}}
{{ASSIGNEE_NAMES}}
{{SHEET_NAME_1}}
{{SPREADSHEET_ID_OR_URL_1}}
{{TASK_COLUMN}}
{{DESCRIPTION_COLUMN}}
{{DEADLINE_COLUMN}}
{{ASSIGNEE_COLUMN}}
{{STATUS_COLUMN}}
```

Leave assistant-generated placeholders such as `{{TODAY_ISO_DATE}}`, `{{TODAY_DISPLAY_DATE}}`, and `{{TODAY_DATE_IN_DATE_FORMAT}}` in the prompt. The assistant fills them from the system date during each run.

Do not publish your real local path, email address, API key, or private Google Sheet link.

## 9. Run Once Before Scheduling

1. Open the `mindstack-ai Morning Routine` task.
2. Click `Run`, `Run now`, `Test`, or `Preview`.
3. Confirm it can access Gmail, Calendar, and Sheets.
4. Confirm it can create or output today's daily note.
5. Fix any connector error before enabling the schedule.
6. Run the `mindstack-ai Evening Reflection` task on a test daily note.
7. Only then turn on the final schedule.

## Troubleshooting

If Claude reads the wrong Gmail, Calendar, or Drive account:

- Disconnect that connector.
- Connect it again.
- On the Google sign-in screen, click `Use another account`.
- Choose the account that owns the data.

If Claude cannot see a sheet:

- Open the sheet in your browser.
- Click `Share`.
- Share it with the Google account connected to Claude.
- Copy the exact sheet URL again.
- Put the exact URL in the prompt.

If Claude cannot write to Obsidian:

- Use a synced folder that Claude can access through Drive, Dropbox, iCloud, or OneDrive.
- On Windows, check whether Windows Defender Controlled Folder Access blocked the write. Move the vault to a dedicated folder or allowlist the writing app.
- Or use the OpenCode low-code path in [`03-opencode-mcp-composio-setup.md`](03-opencode-mcp-composio-setup.md).
