# Superprompt

A self-referential rules framework for AI agents that solves the memory reset problem with file-based continuity.

## The Problem

AI agents lose all context when sessions end. Each new session starts from scratch — wasting time re-establishing context, re-reading files, and rediscovering project state.

## The Solution

Superprompt provides:
- **A standardized startup ritual** — Agents read rules → check knowledge → continue
- **A memory bank** (`knowledge/`) that persists context between sessions
- **A quality framework** — SPEC → VERIFY → CONTINUITY for consistent output

## Quick Start

1. An AI agent enters the project
2. Agent reads `.rules/START_HERE.md`
3. Agent reads `knowledge/` files for context
4. Agent continues from where work was left off

## Folder Structure

```
project/
├── .rules/              # Agent operating framework
│   └── START_HERE.md   # Entry point (read first)
├── knowledge/           # Memory bank (agent continuity)
│   ├── projectBrief.md      # Core requirements, goals
│   ├── productContext.md    # Why project exists
│   ├── activeContext.md    # Current focus, recent changes
│   ├── systemPatterns.md   # Architecture, design patterns
│   ├── techContext.md      # Technologies, setup
│   ├── progress.md         # What works, what's left
│   └── changelog.md        # Chronological change log
└── skills/              # Available techniques (planned)
```

## 3-Layer Approach

Agents follow a consistent quality framework:

### Layer 1: SPEC
Understand before acting. Read context, scan files, ask questions, define success criteria.

### Layer 2: VERIFY
Validate before finalizing. Cross-check against spec, iterate until criteria are met.

### Layer 3: CONTINUITY
Maintain documentation. Keep knowledge files current, document decisions.

## Self-Referential Nature

The rules describe themselves. This framework can be managed by agents using the framework. The `.rules/` folder starts with a dot, hidden from humans — it's purely for AI agents.

## Scale to Complexity

Not every task needs all layers:
- **Trivial** (single command): Skip to implementation
- **Medium** (feature, refactor): Full 3 layers
- **Mammoth** (architecture): Focus on architecture, entry points, key configs

## Design Philosophy

- Technology-neutral — works for any language or framework
- Verify don't assume — check config files, don't infer from filenames
- File-based persistence — knowledge files survive session resets
- Stale detection — if knowledge is >7 days old, reinitialize