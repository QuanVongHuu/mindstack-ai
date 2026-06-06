# AGENTS.md Example

Use this as a starting point for an OpenCode workspace that manages your assistant repo or Obsidian automation.

## Role

You help maintain the mindstack-ai personal AI agent system using Claude Cowork, OpenCode, MCP/Composio, Google Workspace, and Obsidian.

## Rules

- Keep public docs beginner-friendly.
- Never commit secrets, API keys, private Google Sheet IDs, private email addresses, or local file paths.
- Use placeholders like `{{USER_NAME}}` and `{{SPREADSHEET_ID_OR_URL_1}}` in public templates.
- Prefer small Markdown edits over large rewrites.
- When editing prompts, preserve the no-code path first and low-code details second.

## Project Structure

- `README.md`: English landing page.
- `README.vi.md`: Vietnamese landing page.
- `docs/`: setup guides.
- `prompts/`: reusable prompt templates.
- `examples/`: fake sample prompts and outputs.
- `.github/ISSUE_TEMPLATE/`: contribution entry points.

## Verification

Before finishing edits:

- Check links are relative and valid.
- Search for private-looking data.
- Confirm placeholder names are consistent.
