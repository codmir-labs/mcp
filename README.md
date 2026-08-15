# Codmir MCP Server

> The physical layer for Claude. Give your AI agent a full development workspace.

Codmir exposes a [Model Context Protocol](https://modelcontextprotocol.io) server that lets Claude work on your projects end-to-end — tickets, sprints, AI agents, error debugging, phone calls, and desktop control. Claude on steroids.

## Quick Start

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "codmir": {
      "url": "https://codmir.com/mcp"
    }
  }
}
```

Restart Claude. Done.

## CLAUDE.md Instructions

Paste this block into your project's `CLAUDE.md` to give Claude full context on what it can do:

````markdown
# Codmir Workspace

This project uses Codmir as its development workspace. You have access to the
Codmir MCP server with the following tools.

## Project Management

- `get_workspace_status` — Check if the workspace has an org and projects set up
- `get_project_context` — Full project overview: tech stack, recent activity, team
- `get_sprint_tasks` — Current sprint tasks with status, assignees, and progress
- `list_project_tasks` — List all tasks with filtering options
- `list_todo` — Actionable tickets sorted by priority

## Tickets

- `create_ticket` — Create bugs, features, tasks, or improvements
- `get_ticket` — Full ticket details with comments, assignee, labels
- `update_ticket` — Update title, description, priority, type, assignee, due date
- `search_tickets` — Search tickets by keyword across title and description
- `update_todo_status` — Update status: open → in_progress → review → done → closed
- `add_comment` — Add markdown comments (types: comment, progress, blocker, decision, note)
- `log_work` — Log time spent, files changed, and artifacts against a ticket

## AI Task Execution

- `execute_task` — Dispatch an AI agent (TARS) to work on a task autonomously.
  Agents: `claude`, `openai`, `gemini`. Priority: `low`–`critical`. Timeout configurable.
- `check_task_status` — Monitor a running execution: status, progress %, logs, results

## Work Engine (Parallel Execution)

- `decompose_goal` — Break a goal into executable fragments with parallel waves
- `get_work_graph` — Full work graph: all fragments, waves, and states
- `spawn_fragment` — Add a fragment (think, build, verify, decide, integrate, observe)
- `complete_fragment` — Mark complete with artifacts; optionally spawn children
- `converge_wave` — Merge a completed wave back into a coherent result
- `execute_goal` — Run a goal autonomously with plan-do-check cycles

## Error Debugging

- `lookup_error` — Look up a production error by refId, digest, fingerprint, or issueId
- `list_recent_errors` — List recent errors with severity filtering
- `get_error_context` — Enriched context with suggested files and similar resolved issues

## Bug Bounty

- `report_bug` — Report a bug against any software vendor (auto-creates vendor page)
- `search_bug_reports` — Search existing reports to avoid duplicates
- `upvote_bug_report` — Upvote an existing report

## Background Work

- `spawn_work` — Dispatch a background agent (research, call, schedule, analyze)
- `call_number` — Place a phone call via AI to accomplish an objective

## SDK & Workspace Setup

- `get_sdk_reference` — API reference for topics (tickets, projects, chat, errors)
- `generate_sdk_code` — Generate ready-to-use TypeScript/JavaScript SDK code
- `create_organization` — Create a new org/workspace
- `create_project` — Create a new project within an org

## Memory

- `store_conversation` — Save conversation context (decisions, solutions, architecture
  notes) so future sessions can pick up where you left off

## Desktop Control (requires Codmir Desktop)

When the Codmir desktop agent is running, you also get:

- `codmir_screenshot` — Capture the entire screen
- `codmir_click` / `codmir_double_click` / `codmir_right_click` — Click at coordinates
- `codmir_type` — Type text at cursor position
- `codmir_key` — Press keyboard shortcuts
- `codmir_scroll` — Scroll at coordinates
- `codmir_mouse_move` — Move the cursor
- `codmir_shell` — Run shell commands on the machine
- `codmir_screen_info` — Screen dimensions and frontmost app
- `codmir_fetch_page` — Fetch a web page (returns HTML, links, title)
- `codmir_scan_routes` — Scan multiple web routes for status codes
- `codmir_list_directory` — List files at a path
- `codmir_connect` / `codmir_disconnect` — Start/end an agent session with visual border glow

## Workflow

1. `get_project_context` → understand the current state
2. `get_sprint_tasks` → see what's in the current sprint
3. `search_tickets` → find related work before creating duplicates
4. `create_ticket` or `execute_task` → create work or dispatch an agent
5. `check_task_status` → monitor running agents
6. `store_conversation` → save decisions for future sessions
````

## Tools by Plan

| Plan | Tools |
|------|-------|
| **Free** | `get_workspace_status`, `get_project_context`, `list_todo`, `get_ticket`, `search_tickets`, `report_bug`, `search_bug_reports`, `upvote_bug_report` |
| **Pro** | Everything in Free + `create_project`, `create_ticket`, `update_ticket`, `update_todo_status`, `add_comment`, `execute_task`, `check_task_status`, `store_conversation`, Work Engine tools, Error tools, SDK tools |
| **Premium** | Everything in Pro + `call_number` ($0.05/call), `spawn_work` ($0.02/spawn) |

## Architecture

Codmir's MCP infrastructure has multiple layers:

- **`packages/mcp`** — Primary stdio MCP server (`npx @codmir/mcp`), 44 tools (28 cloud + 16 desktop)
- **`apps/mcp-server`** — Remote StreamableHTTP server with OAuth, session management, plan-based access control
- **`apps/mcp-plugin-anthropic`** — Anthropic connector plugin with `.well-known/mcp.json` manifest
- **MCP Gateway** — Proxy that aggregates multiple upstream MCP servers into a single endpoint

All tools connect to the same Codmir workspace. Use the MCP server from Claude for planning and dispatching. Pair it with the CLI or desktop app for hands-on development.

## Install CLI (Optional)

For the full workstation experience:

```bash
# macOS / Linux
curl -fsSL https://codmir.com/install.sh | bash

# Windows
irm https://codmir.com/install.ps1 | iex
```

The MCP server and CLI connect to the **same workspace** — use both, or just one.

## Links

- [codmir.com](https://codmir.com) — Platform
- [Documentation](https://codmir.com/docs) — Full docs
- [MCP Protocol](https://modelcontextprotocol.io) — MCP specification

## License

MIT
