# OpenCode + MCP + Composio Setup

This is the optional low-code layer. Skip it if Claude Cowork connectors already read Gmail, Calendar, Sheets, and write your daily notes well enough.

Use OpenCode when you want local file control or direct Obsidian vault edits. Add MCP/Composio only when you also need a repeatable way to connect external apps.

## What Each Tool Does

- OpenCode: local AI workspace assistant for editing files, prompts, docs, and Obsidian Markdown notes.
- MCP: Model Context Protocol, a standard way for AI tools to call external tools and data sources.
- Composio: connector platform that can expose apps such as Gmail, Google Calendar, Google Drive, Google Sheets, GitHub, Slack, and others through tools or MCP.

Important account rule: OpenCode, Composio, Claude, and Google can all use different accounts. The account that controls Gmail, Calendar, or Drive access is the account you choose during the connector authorization flow, not necessarily the account you used to sign in to Claude or OpenCode.

## When To Add This Layer

Add OpenCode when you want to:

- Write directly into local Obsidian files.
- Maintain this GitHub repo with AI help.

Add MCP/Composio when you want to:

- Use Google Workspace tools from a local assistant.
- Connect multiple external apps through one MCP-style interface.
- Add more apps later without rewriting your entire prompt.

## Useful Official References

- OpenCode intro and install: `https://opencode.ai/docs/`
- OpenCode config: `https://opencode.ai/docs/config/`
- OpenCode MCP servers: `https://opencode.ai/docs/mcp-servers/`
- Composio docs: `https://docs.composio.dev/`
- Composio MCP docs: `https://docs.composio.dev/docs/mcp`
- Composio dashboard MCP clients: `https://dashboard.composio.dev/~/org/connect/clients`

Use this guide as the beginner path, then use the official docs if a button or config option has changed.

## 1. Install OpenCode

Choose one install path.

### Option A: Terminal Install

1. Open Terminal, PowerShell, or Windows Terminal.
2. Run the official install command from the OpenCode docs.
3. If you use Node.js, you can install with:

```bash
npm i -g opencode-ai@latest
```

4. Check that it installed:

```bash
opencode --version
```

On Windows, OpenCode recommends WSL for the best terminal experience. If you are not comfortable with WSL, start with the Claude Cowork no-code path first.

### Option B: Desktop Or IDE Extension

If you use an OpenCode desktop app or IDE extension:

1. Install it from the official OpenCode website.
2. Open the app or extension.
3. Sign in or connect your model provider when prompted.
4. Open this repo folder or your Obsidian vault folder.

## 2. Connect An LLM Provider In OpenCode

OpenCode needs a model provider before it can help you.

1. Open your project folder in a terminal.
2. Run:

```bash
opencode
```

3. In the OpenCode interface, type:

```text
/connect
```

4. Choose the provider you want to use.
5. Follow the on-screen sign-in or API-key steps.
6. Return to OpenCode after the connection succeeds.

This model provider account is separate from your Google connector accounts. It only pays for or serves the AI model.

## 3. Open The Right Folder

Choose the folder based on what you want OpenCode to edit.

For this repo:

```bash
cd /path/to/mindstack-ai
opencode
```

For your Obsidian vault:

```bash
cd /path/to/your/obsidian-vault
opencode
```

If you want OpenCode to edit both this repo and your vault, start with this repo first. Add vault access only after you are comfortable with file edits.

On Windows, put writable Obsidian vaults and automation workspaces outside folders commonly protected by Windows Defender Controlled Folder Access, such as `Desktop`, `Documents`, or protected synced folders. Dedicated paths such as `C:\ObsidianVaults\DailyOS` or `D:\ObsidianVaults\DailyOS` are easier to debug. If you must use a protected folder, allowlist OpenCode, your terminal, or the app that writes Markdown files in Windows Security.

## 4. Initialize Project Rules

OpenCode can create an `AGENTS.md` file that tells the assistant how to behave in the folder.

1. In OpenCode, type:

```text
/init
```

2. Let OpenCode inspect the folder.
3. Review the generated `AGENTS.md` before trusting it.
4. For this repo, you can also copy from [`../examples/AGENTS.example.md`](AGENTS.example.md).

The purpose of `AGENTS.md` is to remind the assistant to keep docs beginner-friendly, avoid secrets, use placeholders, and prefer small Markdown edits.

## 5. Decide How Obsidian Files Will Be Edited

You have two practical choices.

### Option A: Open The Vault As The Project

Use this if the main goal is editing Obsidian notes.

1. Open a terminal.
2. Go to your vault folder.
3. Run `opencode`.
4. Ask OpenCode to create or edit files under `Daily/`.

This is the simplest local-file path because OpenCode can see the files in the folder you opened.

### Option B: Keep This Repo As The Project

Use this if the main goal is editing this GitHub repo.

1. Open this repo in OpenCode.
2. Keep real Obsidian paths out of public docs.
3. Use placeholders such as `{{OBSIDIAN_VAULT_PATH}}`.
4. Only give OpenCode the real vault path in private conversations.

## 6. Understand MCP Before Adding It

OpenCode already has local file tools for the folder you open. You do not need MCP just to edit Markdown files in the current folder.

Add MCP only when you need external tools, such as:

- Gmail.
- Google Calendar.
- Google Drive or Google Sheets.
- GitHub.
- Web or documentation search.
- Other SaaS apps.

Each MCP server adds tools and context. Add one server at a time and test it before adding more.

## 7. Create A Composio Account

1. Open `https://dashboard.composio.dev/`.
2. Sign up or log in.
3. Open the dashboard.
4. Look for `Connect`, `Toolkits`, `Apps`, `MCP`, or `Clients`.
5. If the UI offers `MCP clients`, open `https://dashboard.composio.dev/~/org/connect/clients`.

Composio is the account that manages connector access. It can connect to Google accounts that are different from your Claude account, OpenCode model account, or Composio login email.

## 8. Connect Google Apps In Composio

Connect only the apps you actually need.

1. In Composio, search for `Gmail`.
2. Click `Connect`, `Add`, or `Enable`.
3. A Google sign-in page should open.
4. Choose the Google account that has the Gmail data you want.
5. If it is not listed, click `Use another account`.
6. Review the permissions.
7. Click `Allow`.
8. Repeat for `Google Calendar`, `Google Drive`, and `Google Sheets` if needed.

If your Gmail, Calendar, and Sheets live in different Google accounts, connect the correct account for each app if Composio allows separate connections. If a file is not visible, share it with the connected Google account.

## 9. Create Or Copy The Composio MCP URL

Composio's current docs recommend session-based MCP for most users. The advanced single-toolkit MCP path is also documented, but beginners should prefer a dashboard-generated or session-generated MCP URL when available.

Beginner dashboard path:

1. In Composio, open `MCP`, `Clients`, or `Connect clients`.
2. Create a new MCP client or session.
3. Choose the toolkits you need, such as Gmail, Calendar, Drive, or Sheets.
4. Copy the MCP server URL.
5. Copy any required header or API-key instruction.

If the dashboard asks for a user ID, use a stable private label, for example:

```text
{{COMPOSIO_USER_ID}} = personal-assistant
```

Do not use a public email address as a user ID in public examples.

## 10. Store The Composio API Key Safely

If Composio requires an API key header, store it outside the repo.

Temporary PowerShell session:

```powershell
$env:COMPOSIO_API_KEY = "your_private_key_here"
```

Persistent Windows environment variable:

```powershell
setx COMPOSIO_API_KEY "your_private_key_here"
```

macOS or Linux shell:

```bash
export COMPOSIO_API_KEY="your_private_key_here"
```

Never commit the real key to `opencode.json`, docs, prompts, screenshots, or examples.

## 11. Add Composio MCP To OpenCode

Create or edit `opencode.json` in your project root. OpenCode's official docs say MCP servers go under the `mcp` key.

Use this public-safe template:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "composio": {
      "type": "remote",
      "url": "{{COMPOSIO_MCP_URL}}",
      "enabled": true,
      "headers": {
        "x-api-key": "{env:COMPOSIO_API_KEY}"
      }
    }
  }
}
```

Replace `{{COMPOSIO_MCP_URL}}` privately with the MCP URL from Composio.

If your Composio MCP URL uses OAuth without an API-key header, follow the Composio and OpenCode docs for OAuth remote MCP instead of adding the `headers` block.

## 12. Test The MCP Connection

Start OpenCode in the folder containing `opencode.json`:

```bash
opencode
```

Check MCP status and connectivity:

```bash
opencode mcp debug
```

If authentication is required, run:

```bash
opencode mcp auth composio
```

Then test with a low-risk prompt:

```text
Use the composio tools to list available Google Workspace tools. Do not read private email, calendar events, or sheet rows yet.
```

After that, test one connector at a time:

```text
Use composio to check whether Gmail access is available. Do not summarize private email content yet.
```

```text
Use composio to check whether Calendar access is available. Do not list private event details yet.
```

```text
Use composio to check whether Sheets access is available. Do not read private rows yet.
```

## 13. Use Different Accounts Safely

If you need multiple Google accounts, keep a private account map outside the public repo.

Example private map:

```text
Gmail connector: personal Google account
Calendar connector: school Google account
Sheets connector: project Google account
Drive connector: project Google account
```

In public templates, write placeholders instead:

```text
{{GMAIL_ACCOUNT_LABEL}}
{{CALENDAR_ACCOUNT_LABEL}}
{{DRIVE_ACCOUNT_LABEL}}
{{SHEETS_ACCOUNT_LABEL}}
```

If OpenCode or Composio reads the wrong account, disconnect that connector and reconnect it. On the Google sign-in screen, choose `Use another account`.

## 14. Suggested MCP Tools

Start small. Add only what you need.

- Composio Google Workspace connector for Gmail, Calendar, Drive, and Sheets.
- GitHub MCP or Composio GitHub connector if you want issue and PR automation.
- Documentation search MCP such as Context7 if you want help reading technical docs.
- Avoid large toolkits until the basic daily workflow works.

## 15. Keep Secrets Out Of The Repo

Put API keys and tokens in local environment variables or a private config file.

Never commit:

- `.env`
- API keys
- OAuth tokens
- real Google Sheet IDs if the repo is public
- private vault paths
- private email addresses
- screenshots that show private connector accounts

This repo includes `.gitignore` entries for common secret files, but you still need to review changes before publishing.

## 16. First Real Test

After setup works, ask OpenCode:

```text
Using the connected tools available here, help me run a safe dry-run of the morning routine. Do not write files yet. Show what data sources are available, what is missing, and what the daily note would contain.
```

Only allow file writing after the dry-run output looks correct.
