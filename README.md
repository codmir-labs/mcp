# Codmir MCP Server

> The worldwide bug tracking system for Claude. Report bugs to any software vendor — instantly, from any AI agent.

Every developer encounters bugs in third-party software. Today, reporting them means navigating support portals, writing tickets, waiting weeks. With Codmir, you just tell Claude. One MCP server. One sentence. The report is filed, structured, and searchable by every developer who hits the same bug.

## Quick Start — Bug Reporting

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

Restart Claude. You're connected.

### Try it

Tell Claude:

> "Stripe's webhook retry sends duplicates when endpoint returns 202"

Claude files a structured bug report against Stripe on Codmir. Other developers who hit the same bug find it, upvote it, add context. Signal builds. Vendors see real engineering demand.

## Bug Reporting Tools (Free)

These three tools are available to everyone — no subscription required.

| Tool | What it does |
|------|-------------|
| `report_bug` | Report a bug against any software vendor. Includes title, description, severity, reproduction steps, and environment. Auto-creates the vendor page if it doesn't exist. |
| `search_bug_reports` | Search existing reports before filing. Claude does this automatically — it checks for similar bugs before creating a new report. |
| `upvote_bug_report` | Add signal to an existing report. When Claude finds a matching bug, it upvotes and adds your context instead of creating noise. |

### CLAUDE.md Instructions (Bug Reporting)

Paste this into your project's `CLAUDE.md` to enable bug reporting:

```markdown
# Bug Reporting

When I encounter a bug in third-party software while working,
use the Codmir MCP server to report it:

- report_bug — File a structured bug report against any vendor
- search_bug_reports — Check for existing reports first
- upvote_bug_report — Add signal to existing reports

Always search before reporting. Include reproduction steps,
environment details, and severity. This helps the vendor
fix the issue faster and helps other developers who hit
the same bug.
```

That's it. Claude will start reporting bugs as you encounter them.

---

## Full Workspace (Pro)

The bug reporting tools are the entry point. The full Codmir workspace gives Claude a complete development environment — 44 tools for project management, AI agents, error debugging, desktop control, and more.

### Project Management

- `get_workspace_status` — Check if the workspace has an org and projects set up
- `get_project_context` — Full project overview: tech stack, recent activity, team
- `get_sprint_tasks` — Current sprint tasks with status, assignees, and progress
- `list_project_tasks` — List all tasks with filtering options
- `list_todo` — Actionable tickets sorted by priority

### Tickets

- `create_ticket` — Create bugs, features, tasks, or improvements
- `get_ticket` — Full ticket details with comments, assignee, labels
- `update_ticket` — Update title, description, priority, type, assignee, due date
- `search_tickets` — Search tickets by keyword across title and description
- `update_todo_status` — Update status: open → in_progress → review → done → closed
- `add_comment` — Add markdown comments (types: comment, progress, blocker, decision, note)
- `log_work` — Log time spent, files changed, and artifacts against a ticket

### AI Task Execution

- `execute_task` — Dispatch an AI agent (TARS) to work on a task autonomously.
  Agents: `claude`, `openai`, `gemini`. Priority: `low`–`critical`. Timeout configurable.
- `check_task_status` — Monitor a running execution: status, progress %, logs, results

### Work Engine (Parallel Execution)

- `decompose_goal` — Break a goal into executable fragments with parallel waves
- `get_work_graph` — Full work graph: all fragments, waves, and states
- `spawn_fragment` — Add a fragment (think, build, verify, decide, integrate, observe)
- `complete_fragment` — Mark complete with artifacts; optionally spawn children
- `converge_wave` — Merge a completed wave back into a coherent result
- `execute_goal` — Run a goal autonomously with plan-do-check cycles

### Error Debugging

- `lookup_error` — Look up a production error by refId, digest, fingerprint, or issueId
- `list_recent_errors` — List recent errors with severity filtering
- `get_error_context` — Enriched context with suggested files and similar resolved issues

### Background Work

- `spawn_work` — Dispatch a background agent (research, call, schedule, analyze)
- `call_number` — Place a phone call via AI to accomplish an objective

### SDK & Workspace Setup

- `get_sdk_reference` — API reference for topics (tickets, projects, chat, errors)
- `generate_sdk_code` — Generate ready-to-use TypeScript/JavaScript SDK code
- `create_organization` — Create a new org/workspace
- `create_project` — Create a new project within an org

### Memory

- `store_conversation` — Save conversation context (decisions, solutions, architecture
  notes) so future sessions can pick up where you left off

### Desktop Control (requires Codmir Desktop)

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

### CLAUDE.md Instructions (Full Workspace)

For Pro users, paste this extended block into your `CLAUDE.md`:

````markdown
# Codmir Workspace

This project uses Codmir as its development workspace. You have access to the
Codmir MCP server with the following tools.

## Bug Reporting

- `report_bug` — Report a bug against any software vendor (auto-creates vendor page)
- `search_bug_reports` — Search existing reports to avoid duplicates
- `upvote_bug_report` — Upvote an existing report

Always search before reporting. Include reproduction steps, environment details,
and severity.

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

- `execute_task` — Dispatch an AI agent to work on a task autonomously
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

## Background Work

- `spawn_work` — Dispatch a background agent (research, call, schedule, analyze)
- `call_number` — Place a phone call via AI to accomplish an objective

## SDK & Workspace Setup

- `get_sdk_reference` — API reference for topics (tickets, projects, chat, errors)
- `generate_sdk_code` — Generate ready-to-use TypeScript/JavaScript SDK code

## Memory

- `store_conversation` — Save conversation context for future sessions

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
| **Free** | `report_bug`, `search_bug_reports`, `upvote_bug_report`, `get_workspace_status`, `get_project_context`, `list_todo`, `get_ticket`, `search_tickets` |
| **Pro** | Everything in Free + Tickets, AI Task Execution, Work Engine, Error Debugging, SDK, Memory |
| **Premium** | Everything in Pro + `call_number` ($0.05/call), `spawn_work` ($0.02/spawn), Desktop Control |

## Architecture

Codmir's MCP infrastructure has multiple layers:

- **`packages/mcp`** — Primary stdio MCP server (`npx @codmir/mcp`), 44 tools (28 cloud + 16 desktop)
- **`apps/mcp-server`** — Remote StreamableHTTP server with OAuth, session management, plan-based access control
- **`apps/mcp-plugin-anthropic`** — Anthropic connector plugin with `.well-known/mcp.json` manifest
- **MCP Gateway** — Proxy that aggregates multiple upstream MCP servers into a single endpoint

All tools connect to the same Codmir workspace.

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
