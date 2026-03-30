# Lark Minutes Tasks

An AI agent skill that reads Lark/Feishu meeting transcripts, extracts action items, and actually gets them done. Not just a to-do list generator. The agent executes the tasks for you.

## What it does

You give it a meeting transcript (Lark Minutes URL or meeting notes doc). It:

1. Reads the full transcript
2. Scans for Wake Word commands (phrases you said during the meeting to directly instruct the agent)
3. Extracts every action item, both explicit ("I'll send you that doc") and implied
4. For each item, figures out the best way to execute it (schedule a meeting, draft a message, search for info, create a doc, etc.)
5. Shows you a numbered list. You pick which ones the agent should handle.
6. Executes them. Done.

## Wake Word

Set a trigger phrase (like "hey agent" or anything you want). Say it during a meeting, and the agent will pick up your command from the transcript after the meeting. You don't need to remember what you said. The agent remembers for you.

## Install

Drop `minutes.md` into your agent's commands directory:

**Claude Code:**
```bash
cp minutes.md ~/.claude/commands/minutes.md
```

**Other agents:**
Place the file wherever your agent reads skill/command definitions from.

## Prerequisites

- [Lark CLI](https://github.com/larksuite/cli) installed and configured (`lark-cli config init`)
- User authentication completed (`lark-cli auth login --domain all`)

## Usage

```
/minutes https://your-lark-instance.com/minutes/your-minute-token
```

Or pass a meeting notes document URL:

```
/minutes https://your-lark-instance.com/docx/your-doc-token
```

The agent will walk you through the rest.

## Supported action types

| Type | What the agent does |
|------|-------------------|
| Send message | Drafts the message, copies to clipboard for you to paste |
| Schedule meeting | Checks calendars, finds free slots, creates the event |
| Write document | Creates a Lark doc with the content |
| Research | Searches web or Lark docs, summarizes findings |
| Try a product | Finds the link/install instructions, sends to you |
| Create task | Creates a Lark task with assignee and due date |
| Read/review doc | Fetches the doc, reads it, gives you a summary |

## License

MIT
