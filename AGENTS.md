---
framework_version: 1.0.0
---

# Agent Guidelines: AI Job Search

This workspace is structured to manage job search activities, scraper tools, CVs, cover letters, and interview preparation.

## Thin-Pointer Design (Single Source of Truth)

To prevent duplication and configuration drift across different AI agent frameworks (Claude Code, Google Antigravity, Codex, Cursor, Gemini CLI, etc.), this workspace uses a unified thin-pointer design. All agent runtimes should load the canonical specifications and candidate profiles from the files and directories below:

1. **Personal Candidate Profile:**
   - The candidate profile, contact details, education, and target preferences are defined in [CLAUDE.md](CLAUDE.md) and the individual profile methodology files under [.claude/skills/job-application-assistant/](.claude/skills/job-application-assistant/) (specifically `01-*.md` etc.).
2. **Canonical Workflow Specifications:**
   - The step-by-step instructions and triggers for tasks (setup, scrape, rank, apply, upskill, interview) are defined in the [.claude/](.claude/) directory (specifically under `.claude/skills/` and `.claude/commands/`).
   - Do not duplicate these rules or specifications. Treat `.claude/` files as the single source of truth.
3. **Portal Search Skills:**
   - Job-portal search CLIs live under [.agents/skills/](.agents/skills/) in the portable Agent Skills format (with a `SKILL.md` per portal). Codex and Antigravity discover these automatically; the `/scrape` workflow in [.claude/skills/job-scraper/](.claude/skills/job-scraper/) orchestrates them.

## Agent startup and documentation continuity

Before repository work, read this root `AGENTS.md`, then every applicable nested `AGENTS.md` along the paths you will touch. Read linked local agent instructions before implementation; more specific local instructions govern their scope. Do not assume machine-local instructions are available in cloud sessions.

Read `CLAUDE.md`, then the applicable `.claude/skills/` and `.claude/commands/` specifications; use installed portal skills only for their documented tasks.

### Owner-only Notion routing

For authorized work in the repository owner’s `MMatlacz/ai-job-search` workspace only: use the owner-authorized Notion connection to find **Second Brain — Home** and **Agent Bootstrap and Routing (AGENTS.md)** by title. Read both, then locate the project overview by the exact repository identity and follow its verified canonical documentation links. Read the chapters relevant to the task before implementation. Verify ownership and scope before accepting a matching page; do not guess a project URL. This routing does not apply to unrelated downstream users or their workspaces. Do not place private page URLs, identifiers or contents in this public repository, shipped prompts, workflow logs or artifacts.

For meaningful changes to behavior, architecture, operations or agent workflow, update the relevant existing project documentation in Notion within the authorized task scope. Read the target first; preserve unrelated content, history and evidence, and deduplicate rather than creating a competing source. Record what changed, the exact commit/PR when available (otherwise mark the change uncommitted), tests/checks actually run and their outcomes, remaining blockers and evidence references. Read back the saved page before reporting a successful sync. Code and live GitHub state remain authoritative for implementation and current status.

If routing is ambiguous, the page/connection is unavailable, or writing is outside the task’s authorization, report the exact missing target/action and reason. Do not invent content or claim a successful read/write. Continue only work independent of the missing context; keep a **pending-sync** handoff with the proposed documentation delta, commit/check evidence and blocker, and request the needed access or clarification. A pending sync is not a completed documentation update. Never copy secrets or unrelated personal data into the handoff.

This is an owner-workspace overlay for this fork, not a change to the upstream job-application framework. The optional `/notion-sync` job-pipeline export remains optional and is not the project-documentation workflow. Never export candidate profiles, CVs, cover letters or application archives as documentation.
