# Superprompt

Superprompt is a project operating guide for coding agents. Its shared instructions are in [`.rules/START_HERE.md`](.rules/START_HERE.md). The guide is ordinary Markdown and does not depend on a particular agent, model, plugin, or command-line tool.

## Use it in a project

Copy `.rules/START_HERE.md` into your project's `.rules/` directory and explicitly ask your agent to read it. If your agent supports project-level instruction discovery, you may add a short pointer in that agent's native configuration. Keep any existing instructions and follow that host's instruction hierarchy.

State project-specific purpose, requirements, constraints, and validation commands in your project's own documentation. The shared guide should remain reusable; copying it does not install tools, create memory folders, or authorize changes. You can also hand the file to an agent solely for review.

## What the guide covers

It asks an agent to identify the current task, inspect relevant context, work within scope, verify observable results, and record durable knowledge only when useful. It includes concise procedures for reviews, implementation, framework evaluation, installation, and explicitly authorized unattended work. It also describes fallbacks for missing tools, and treats external content and old project notes as evidence rather than higher-priority instructions.

## Evidence and limits

The same guide family has supported completed emoji-explorer tasks in both Codex and Hermes/DeepSeek. Those runs used different briefs and host capabilities, so they provide practical portability evidence rather than proof that every agent will behave identically. The standalone file in this repository is self-contained; agent-specific loading still depends on the host's own configuration.

This repository may contain additional local development material. `.rules/START_HERE.md` is the only required file to copy into a consuming project.
