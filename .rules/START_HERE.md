# AGENT START GUIDE

Read this file first. It contains your operating framework.

---

## PURPOSE

Your memory resets between sessions. These files are your continuity.

**When you start a new prompt:**
1. Read `.rules/START_HERE.md`
2. If `knowledge/` is missing or empty → Initialize CONTINUITY structure
3. Read `knowledge/` files to understand project state
4. Identify where work was left off (`activeContext.md`, `progress.md`)
5. Continue from where you stopped

**Project root** = parent directory of the `/.rules/` folder you're reading from.

**This project follows a 3-layer approach for consistent, high-quality output:**

1. **Spec** - Understand before acting
2. **Verify** - Validate before finalizing
3. **Continuity** - Maintain documentation (only if needed)

---

## FOLDER STRUCTURE

```
project/
├── .rules/           ← Read this folder first (hidden from humans)
│   └── START_HERE.md ← (you are here)
├── docs/             ← Project documentation (agents may populate with notes, API docs)
├── knowledge/        ← Memory bank (agent continuity)
└── skills/           ← Techniques, SDK references (agents may add "SDK lives here")
```

---

## LAYER 1: SPEC (Objective Identification)

**Before writing any code:**

1. **Read existing context**
   - Read all files in `knowledge/` (already done as part of startup ritual above)
   - Skim project files and READMEs
   - Understand what the project is

2. **Scan comprehensively (technology-neutral)**
   - Don't limit scanning to expected file types or directories
   - Check root directory, subdirectories, and config files
   - Document ALL files found, not just expected ones
   - **For mammoth projects:** Focus on architecture files, entry points, 
     and key configs first. Read module/namespace-level files, not every line.

3. **Cross-reference configs**
   - Verify config files match actual project structure
   - If config references a folder/file that doesn't exist, flag it
   - Check versions, dependencies, and structure from config files (package.json, 
     .csproj, Cargo.toml, pyproject.toml, etc.) — don't infer from filenames

4. **Ask questions until objectives are clear**
   - Use as a guide, not a checklist
   - Only ask relevant questions
   - Work out what you can - don't ask obvious things
   - Avoid question loops

5. **Use sequential thinking for complex tasks**
   - For multi-step, unclear, or high-impact decisions
   - Iterate, branch, verify hypotheses
   - Adjust thought count as needed

6. **Follow an Agile approach**
   - Iterative, flexible, continuous feedback
   - Re-evaluate as you learn

**Only proceed when you have a clear spec.**
At minimum, cover: **who** (stakeholder), **what** (success criteria), **scope** (in/out), **risks** (constraints or blockers).

---

## LAYER 2: VERIFY (Validation)

**Before finalizing output:**

1. **Define evaluation criteria**
   - What does "good" look like?
   - Quality standards for this task

2. **Cross-check against spec**
   - Does implementation match the spec?
   - Any gaps?

3. **Use external data to validate**
   - Check APIs, SDKs, documentation
   - Fact-check approaches

4. **Act as a critic**
   - You may be validating another agent's work
   - Be thorough, find issues
   - If something is wrong, say so

5. **Iterate until criteria are met**
   - Fix issues before moving on

6. **Offer reflection on non-trivial tasks**
   - After tasks with user feedback or multiple steps
   - Ask: "Would you like me to suggest improvements to the rules?"
   - If yes, analyze feedback, propose specific changes
   - Wait for approval before applying

**Do not finalize until quality standards are met.**

---

## LAYER 3: CONTINUITY (Documentation)

**Maintain documentation - setup if missing, update continuously.**

Create these files if `knowledge/` is missing or empty:
- `projectBrief.md` - Core requirements and goals
- `productContext.md` - Why project exists, problems solved
- `activeContext.md` - Current focus, recent changes (max 10 events), next steps
- `systemPatterns.md` - Architecture, design patterns, key decisions
- `techContext.md` - Technologies, setup, dependencies, constraints
- `progress.md` - What works, what's left, known issues
- `changelog.md` - Chronological log of changes

**Maintain continuously:**
- Keep knowledge files current
- Document decisions and changes
- Maintain sliding window of 10 recent events
- **Before ending a session:** Document current state so the next session can resume seamlessly

**If project appears empty (no files beyond .rules/):**
- Assess whether project should exist
- If unclear, discuss with user before creating structure

---

## SCALE TO TASK COMPLEXITY

Not every task needs all layers. Use proportionally:

- **Trivial** (single command, quick answer): Skip to implementation
- **Medium** (feature, refactor): Full 3 layers
- **Complex** (architecture, multi-component): Extra iteration in SPEC, deeper VERIFY

---

## FRESH PROJECT CHECKLIST

When `knowledge/` is missing/empty, create:

- [ ] Scan ALL project files and directories (technology-neutral)
- [ ] Verify config files match actual structure
- [ ] Document actual files found, not assumed structure
- [ ] `projectBrief.md` - Core requirements, goals, scope
- [ ] `productContext.md` - Why this project exists, problems solved
- [ ] `activeContext.md` - Initial state: "Project initialized, awaiting first task"
- [ ] `systemPatterns.md` - Architecture, key decisions, file inventory
- [ ] `techContext.md` - Technologies, setup, constraints
- [ ] `progress.md` - What works, what's left
- [ ] `changelog.md` - Initial entry with project creation date

**For mammoth projects:** Start with architecture overview. Document patterns and structure. Detailed file inventory is optional — focus on understanding, not cataloging everything.

---

## AGENT CONSTRAINTS

- **Build limitations:** If your environment cannot build, inform user that manual build may be required.

- **Memory reset:** Your memory resets between sessions. Knowledge files are your continuity - maintain them precisely.

- **Respect structure:** Follow project conventions and patterns.

- **Be methodical:** Follow the 3-layer approach consistently.

- **Inconsistencies:** If `knowledge/` files conflict or are outdated, flag to user and let them decide.

- **Stale context:** If `knowledge/` is older than 7 days OR files are inconsistent → reinitialize (delete and recreate from this framework)

- **Verify don't assume:** Always check config files for versions, dependencies, and structure. Don't infer from filenames, comments, or directory names.

- **Complete inventory:** When documenting a project, scan ALL files and directories — root-level, nested, configs, source. Include everything found.

- **Scale to project size:** 
  - **Small/greenfield:** Full scan, all files documented
  - **Mammoth (>50 files, >10 modules):** Focus on architecture, entry points, key configs. Document structure and patterns, not every file. Use globs, grep, and directory listing to understand scope first.

---

## QUICK REFERENCE

```
Task received
  → LAYER 1: SPEC (understand, questions, exit criteria)
  → LAYER 2: VERIFY (validate, cross-check, iterate)
  → LAYER 3: CONTINUITY (setup documentation only if needed)
  → Implement
```

---

**Start by reading `knowledge/` files, then proceed with your task.**