# Getting Started

This page gives you the fastest path from zero to a working mindstack-ai system.

## 10-Minute Path

1. Create or choose an Obsidian vault in a folder your tools can write to.
2. Create a `Daily/` folder inside that vault.
3. Connect Claude Cowork to Gmail, Google Calendar, Google Drive, and your note destination.
4. Open [`../prompts/morning-routine.md`](../prompts/morning-routine.md).
5. Replace the user-input placeholders listed in [`../prompts/personalization-checklist.md`](../prompts/personalization-checklist.md).
6. Run the prompt manually.
7. Fix connector/path errors.
8. Schedule it for the morning.
9. Repeat with [`../prompts/evening-reflection.md`](../prompts/evening-reflection.md).

## Choose Your Track

No-code is enough if you want:

- Gmail summary.
- Calendar overview.
- Google Sheets task extraction.
- Markdown daily note generation in a folder Obsidian can open.
- Morning and evening scheduled routines.

Low-code is useful if you want:

- More reliable local file operations with OpenCode.
- Repo editing with OpenCode.
- MCP tools for Google Workspace, web search, or other external apps.
- Composio-managed connectors.

## Windows Folder Recommendation

On Windows, avoid placing the working vault in folders protected by Windows Defender Controlled Folder Access if your AI tool needs to write files. Protected locations can include `Desktop`, `Documents`, and synced folders depending on your settings.

Safer examples for a local Obsidian vault are `C:\ObsidianVaults\DailyOS` or `D:\ObsidianVaults\DailyOS`. If you must use a protected folder, allowlist the app or terminal that writes the Markdown files in Windows Security.

## Safety First

Do not paste secrets into public prompts.

Private values include:

- API keys.
- Google Sheet IDs or private links.
- Personal file paths such as `C:\Users\YourName\...`.
- Email addresses.
- School, company, or client names if the repo will be public.

Use fake examples in public docs, then keep your real configuration in your private Claude Cowork task.

## First Test

Run the morning prompt manually and check:

- Did Claude find yesterday's note?
- Did Gmail return recent threads?
- Did Calendar return events?
- Did every Google Sheet load?
- Did the new daily note appear in the right folder?
- Did the prompt ask for additions before finalizing the to-do list?

If one connector fails, keep the rest running. The prompt should note the failure and continue.
