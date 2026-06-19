# Superprompt

A self-referential rules framework for AI agents that solves the memory reset problem with file-based continuity.

## The Problem

AI agents lose all context when sessions end. Each new session starts from scratch — wasting time re-establishing context, re-reading files, and rediscovering project state.

## The Solution

Superprompt provides:
- **A standardized startup ritual** — Agents read rules → check knowledge → continue
- **A memory bank** (`knowledge/`) that persists context between sessions
- **A quality framework** — SPEC → VERIFY → CONTINUITY for consistent output
- **LOOP MODE** — For ongoing projects: design automations, use worktrees, codify skills, connect to tools, split maker/checker

## Quick Start

1. An AI agent enters the project
2. Agent reads `.rules/START_HERE.md` (typically via an agent config signpost like `.claude/CLAUDE.md`, `.cursor/rules/START_HERE.mdc`, or `.codex/AGENTS.md`)
3. Agent creates `docs/`, `skills/`, and agent config folders (e.g. `.claude/`, `.codex/`, `.github/workflows/`) if missing — config files must point back to `.rules/START_HERE.md` as the primary entry point, plus any agent-specific instructions for self-improvement/loop mode
4. Agent initializes `knowledge/` only if missing/empty
5. Agent reads `knowledge/` files for context
6. Agent continues from where work was left off

Only `.rules/START_HERE.md` and this `README.md` are typically committed. Placeholder files (`.gitkeep`) in `docs/` and `skills/` may also be tracked. Everything else is generated per workspace for agent continuity.

## Folder Structure

```
project/
├── .rules/              # Agent operating framework (committed)
│   ├── START_HERE.md   # Entry point (read first)
│   └── *.md            # Operating framework files
├── README.md            # This file (committed)
├── docs/                # Project documentation (created automatically if missing)
├── knowledge/           # Memory bank (agent continuity, generated per workspace)
│   ├── projectBrief.md      # Core requirements, goals
│   ├── productContext.md    # Why project exists
│   ├── activeContext.md    # Current focus, recent changes
│   ├── systemPatterns.md   # Architecture, design patterns
│   ├── techContext.md      # Technologies, setup
│   ├── progress.md         # What works, what's left
│   └── changelog.md        # Chronological change log
├── skills/              # Agent-platform skills (created automatically if missing)
├── .claude/CLAUDE.md    # Claude Code entry point (signpost to START_HERE.md)
├── .cursor/rules/       # Cursor entry point (signpost to START_HERE.md)
└── [agent-config]/      # Other agent configs (`.codex/`, `.github/workflows/`, etc.)
                         Brackets mean a placeholder name, not a literal path.
```

## 3-Layer Approach

Agents follow a consistent quality framework:

### Layer 1: SPEC
Understand before acting. Read context, scan files, ask questions, define success criteria.

### Layer 2: VERIFY
Validate before finalizing. Cross-check against spec, iterate until criteria are met.

### Layer 3: CONTINUITY
Maintain documentation. Keep knowledge files current, document decisions.

## LOOP MODE (for ongoing projects)

When work never stops — daily triage, CI monitoring, continuous refactoring — design a loop instead of running tasks manually.

Five primitives (tool-agnostic):
1. **Automations** — scheduled prompts, `/goal`, `/loop`, hooks
2. **Worktrees** — parallel isolated checkouts (`git worktree`)
3. **Skills** — codified project knowledge (SKILL.md files)
4. **Connectors** — MCP servers, issue trackers, Slack, CI
5. **Sub-agents** — maker/checker split for unattended verification

## Scale to Complexity

Not every task needs all layers:
- **Trivial** (single command): Skip to implementation
- **Medium** (feature, refactor): Full 3 layers
- **Complex** (architecture): Extra iteration in SPEC, deeper VERIFY
- **Ongoing** (maintenance, unattended ops): Consider LOOP MODE

## Design Philosophy

- Technology-neutral — works for any language or framework
- Verify don't assume — check config files, don't infer from filenames
- File-based persistence — knowledge files survive session resets
- Stale detection — check knowledge file ages before reading; reinitialize if >7 days old or inconsistent
- Present trade-offs neutrally — let the user decide (EVENHANDEDNESS)
