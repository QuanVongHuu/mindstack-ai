# Why Obsidian?

This page explains what Obsidian is, why it matters in the mindstack-ai workflow, and how to install and use it at a basic level.

## What Is Obsidian?

Obsidian is a personal note-taking app built around Markdown files. Instead of locking your notes inside a proprietary database, Obsidian stores each note as a plain `.md` file inside a folder on your device. That folder is called a vault.

The core ideas are simple:

- A vault is the folder that contains your notes.
- A note is a Markdown file inside the vault.
- A daily note is one note per day, for example `06-06-2026.md`.
- An internal link connects notes with syntax like `[[Project Alpha]]`.
- A tag labels related notes or sections, for example `#task`, `#meeting`, or `#reflection`.

Obsidian works well for a personal AI assistant because the data is readable, portable, easy to back up, and easy for AI tools to edit safely.

## Why This Workflow Uses Obsidian

This repo needs a reliable place where the assistant can read, write, and update daily context. Obsidian is a good fit because it gives you a local, human-readable knowledge base that can also be automated.

## 1. Notes Are Plain Markdown Files

Claude Cowork, OpenCode, and MCP tools can work with Markdown more easily than with data locked inside a closed note app. A daily note is just text, so the assistant can read yesterday's note, create today's note, update tasks, and write an evening reflection without needing a complex format.

## 2. Daily Notes Become Your Personal Memory Layer

In this workflow, each day gets a note in `Daily/`. Over time, that folder becomes a structured personal history:

- What was on your calendar.
- Which emails needed attention.
- Which tasks were prioritized.
- What was completed or left open.
- What you reflected on at night.

The assistant can then support you with context instead of treating every run as an isolated chat.

## 3. You Own Your Data

An Obsidian vault lives in a folder you control. You can back it up, sync it, copy it, open it in another editor, or version it with Git. If you stop using Obsidian later, the Markdown files are still usable.

## 4. It Works With Both No-Code And Low-Code Tracks

In the no-code track, Claude Cowork can write daily notes to the destination you configure, such as a synced folder or a file connector that supports Markdown.

In the low-code track, OpenCode or MCP tools can work directly with a local vault: creating files, editing notes, finding older context, normalizing formatting, or updating project documentation.

## 5. It Keeps The System Simple

You do not need a database, server, or complex task-management app to start. A `Daily/` folder, a few Markdown files, and the right prompt are enough to run the morning routine and evening reflection.

## Suggested Vault Structure

Start with a simple vault layout:

```text
Obsidian Vault/
├── Daily/
│   ├── 06-06-2026.md
│   └── 07-06-2026.md
├── Projects/
├── Meetings/
├── Templates/
└── Inbox.md
```

The key folder for this workflow is `Daily/`. The other folders are optional but useful as your system grows.

## How To Install Obsidian

1. Go to the Obsidian download page: `https://obsidian.md/download`.
2. Choose the installer for your operating system: Windows, macOS, Linux, iOS, or Android.
3. Install it like a normal app.
4. Open Obsidian and choose `Create new vault`.
5. Name the vault, for example `Personal AI Assistant` or `Daily OS`.
6. Choose where to store the vault, for example `Documents/Obsidian/Personal AI Assistant`.
7. Create a `Daily/` folder inside the vault for daily notes.

If you want the same vault on multiple devices, you can sync it with Obsidian Sync, iCloud, Google Drive, Dropbox, OneDrive, or Git. If you are new to Obsidian, start with one local vault first, then add syncing later.

## Basic Usage

### 1. Create A Note

In Obsidian, click `New note`, name the note, and write content. Obsidian uses Markdown, so a note can be as simple as this:

```markdown
# Meeting Notes

## Tasks

- [ ] Reply to email
- [ ] Review project plan

## Notes

Main discussion points go here.
```

### 2. Create A Daily Note

Daily notes are the center of this workflow. Each day has one note that can contain:

- Today's calendar.
- Emails that need attention.
- Tasks from Google Sheets.
- Priority tasks.
- Evening reflection.
- Tomorrow's anchor task.

Example daily note:

```markdown
# 06-06-2026

## Calendar

- 09:00 Team meeting

## Inbox Summary

- Reply needed: project update email

## Priority Tasks

- [ ] Finish report draft
- [ ] Review assignment sheet

## Evening Reflection

- What went well?
- What should improve tomorrow?
```

### 3. Use Internal Links

You can connect notes with internal links:

```markdown
[[Project Alpha]]
[[06-06-2026]]
```

This keeps notes from becoming isolated. For example, today's daily note can link to a project note, meeting note, or task note.

### 4. Use Search And Graph View

Obsidian has fast search across the whole vault. As your archive grows, you can quickly find old decisions, tasks, reflections, and meeting notes.

Graph view shows links between notes. It is not required for this workflow, but it can help you see relationships between projects, people, meetings, and daily notes.

### 5. Add Plugins Only When Needed

Obsidian includes core plugins and community plugins. For this workflow, beginners only need the basics:

- Files.
- Search.
- Backlinks.
- Daily notes.
- Templates, if you want reusable note structures.

Avoid installing too many plugins at the start. Get the workflow running first, then add plugins when there is a clear need.

## Prompt Placeholders

The prompts in this repo use placeholders for your Obsidian setup:

```text
{{OBSIDIAN_VAULT_PATH}}
{{DAILY_NOTE_FOLDER}}
{{DATE_FORMAT}}
```

Example values:

```text
{{OBSIDIAN_VAULT_PATH}} = D:\Users\YourName\Documents\Obsidian\Personal AI Assistant
{{DAILY_NOTE_FOLDER}} = Daily/
{{DATE_FORMAT}} = DD-MM-YYYY
```

Do not publish real local paths, private emails, API keys, or Google Sheets links in a public repo.

## Beginner Checklist

Before running the morning routine prompt, confirm that you have:

- Installed Obsidian.
- Created a vault.
- Created a `Daily/` folder.
- Found the vault path on your machine.
- Chosen a daily note filename date format, for example `DD-MM-YYYY`.
- Created one note manually as a test.
- Replaced `{{OBSIDIAN_VAULT_PATH}}` and `{{DAILY_NOTE_FOLDER}}` in the prompt.

Then continue with [`01-getting-started.md`](01-getting-started.md).
