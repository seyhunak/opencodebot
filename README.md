# opencodebot

Team-lead agent that analyzes a task, picks the right coworkers, and runs them in sequence with user approval at each handoff.

## What it does

`opencodebot` is a lead agent that orchestrates a team of specialized coworker subagents to complete complex tasks. Instead of running every stage by default, it analyzes your request first, then dynamically selects and sequences only the coworkers needed for that specific task. After each stage it shows you the output and waits for your explicit approval before continuing.

This means faster execution, cleaner outputs, and you stay in control at every step.

## How it works

1. **Task analysis** — `opencodebot` reads your request and decides which coworkers are required.
2. **Execution plan** — it creates a sequence of stages with clear inputs/outputs.
3. **Sequential execution** — each coworker runs, writes its output, and hands off.
4. **User gate** — you review each stage's output and approve before the next one runs.
5. **Final delivery** — all artifacts are collected and presented for your use.

## Available coworkers

| Coworker | Purpose | Output |
|----------|---------|--------|
| `researcher` | Web research, structured briefs | `research.md` |
| `data-specialist` | Structured data extraction, CSV/JSON tables | `data.md` |
| `analyst` | Strategic insights, SWOT, market/competitor context | `analysis.md` |
| `designer` | Visual/UX recommendations, design specs | `design-spec.md` |
| `writer` | Polished long-form content, articles, proposals | `draft.md` |
| `fact-checker` | Verifies claims and sources against research | `fact-check.md` |
| `legal` | Compliance, privacy, IP risk review | `legal-review.md` |
| `reviewer` | Quality check for clarity, accuracy, tone | `review.md` |
| `presenter` | Slide-ready presentation outlines | `presentation.md` |
| `summarizer` | Executive summaries and abstracts | `summary.md` |
| `sales-prep` | Battle cards, objection handling, discovery questions | `sales-kit.md` |
| `project-manager` | Project plans, timelines, milestones | `project-plan.md` |
| `drafter` | Contact emails, outreach drafts | `email-draft.md` |
| `scheduler` | Calendar checks, meeting slot proposals | `meeting-options.md` |

## Typical pipelines

### Cold outreach
`researcher → analyst → drafter → scheduler`

### Competitive analysis
`researcher → data-specialist → analyst → writer → reviewer → presenter`

### Due diligence
`researcher → data-specialist → analyst → legal → fact-checker → reviewer → summarizer`

### Sales prep
`researcher → analyst → sales-prep → drafter`

### Content creation
`researcher → analyst → writer → fact-checker → reviewer → summarizer`

## Setup

1. Copy `opencode.json` into your project root.
2. Configure Composio MCP tools as needed.
3. Run `opencodebot` with your task — it will plan and orchestrate the coworker pipeline.

## Permissions

| Agent | Edit | Bash | Composio | Web |
|-------|------|------|----------|-----|
| `opencodebot` (team lead) | ✅ | ❌ | ask | ❌ |
| Subagents | ✅ | ❌ | ask | varies |
| `coworker` (standalone) | ❌ | ❌ | ask | ✅ |

## Guardrails

- Every Composio action is approved before execution.
- No secrets are sent into browser task text.
- Login/2FA flows stop and ask the user to take over.

## License

MIT
