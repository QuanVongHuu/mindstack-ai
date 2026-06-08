# mindstack-ai Docs

These docs guide you through setting up mindstack-ai. The guide has two tracks.

No-code track: Claude Cowork + Gmail/Calendar/Drive/Sheets connectors + a Markdown storage destination that Obsidian can open. Use this if you want the fastest setup.

Low-code track: OpenCode for local file control and repeatable repo edits, plus MCP/Composio only when you need more flexible external integrations.

## Data Flow

Every routine follows the same end-to-end path:

```
Fetch → Process → Write to destination
```

| Stage | What happens | Where |
|---|---|---|
| Fetch | Claude reads Gmail, Google Calendar, and Google Sheets via connectors | Cloud connectors |
| Process | Claude summarises, filters, and structures the data into a daily note | Claude Cowork |
| Write | Claude saves the finished Markdown note to your Obsidian vault or synced folder | Obsidian / synced Markdown folder |

If the environment cannot write files directly, Claude outputs the complete Markdown and states the exact file path where you should save it.

## Recommended No-Code Order

1. [`00-why-obsidian.md`](00-why-obsidian.md)
2. [`01-getting-started.md`](01-getting-started.md)
3. [`02-claude-cowork-setup.md`](02-claude-cowork-setup.md)
4. [`04-google-sheets-links.md`](04-google-sheets-links.md)
5. [`05-morning-routine.md`](05-morning-routine.md)
6. [`06-evening-reflection.md`](06-evening-reflection.md)
7. [`07-faq.md`](07-faq.md)
8. [`08-troubleshooting.md`](08-troubleshooting.md)

## Optional Low-Code Guide

Use [`03-opencode-mcp-composio-setup.md`](03-opencode-mcp-composio-setup.md) after the no-code routine works or when you need local file edits and external app automation.

## What To Prepare

- A Claude account with access to Claude Cowork or scheduled workflows.
- Gmail and Google Calendar access.
- Google Drive/Sheets access.
- An Obsidian vault or another Markdown folder.
- Optional: OpenCode, MCP tools, and Composio connectors.

## Vietnamese Note

The main Vietnamese README is at [`../README.vi.md`](../README.vi.md). Vietnamese docs can be added as `.vi.md` siblings, for example `01-getting-started.vi.md`.
