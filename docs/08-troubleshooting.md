# Troubleshooting

## Claude Cannot Read A Google Sheet

Check:

- The connected Google account has access.
- The spreadsheet ID is correct.
- The sheet is not restricted by an organization.
- The connector supports file content, not only metadata.
- The sheet has a readable tab with task rows.

## Google Sheet Link Does Not Work

Make sure you copied the ID between `/d/` and `/edit`.

Do not include extra spaces.

## Wrong Tasks Appear

Check:

- `{{ASSIGNEE_NAMES}}` includes your exact name variants.
- The assignee column name matches the sheet.
- The sheet read mode is correct: `assigned-only` or `read-all`.
- Completed rows are marked consistently.

## Daily Note Is Written To The Wrong Place

Check:

- `{{OBSIDIAN_VAULT_PATH}}`
- `{{DAILY_NOTE_FOLDER}}`
- filename date format
- file connector permissions

## API Key Error

Check:

- The key is in your private environment/config, not the public prompt.
- The provider/model is configured correctly.
- The key has not expired or been revoked.

## OpenCode Cannot Connect To MCP Server

Check:

- The MCP server process is running.
- The port or stdio config matches your OpenCode config.
- Required environment variables are set.
- Composio connector authentication is complete.

## The Output Is Too Long

Tighten the prompt:

- Reduce Gmail summary to 5 threads.
- Show only the next 7 days.
- Move long task lists into the AI Context Layer.
- Ask the assistant to keep the user-facing section concise.
