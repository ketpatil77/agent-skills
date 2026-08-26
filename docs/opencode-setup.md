# OpenCode Setup

This guide explains how to use Agent Skills with OpenCode without copying repository-maintainer instructions into unrelated projects.

## Overview

OpenCode can discover reusable skills from project-local or global skill directories. The reusable assets in this repository are the skill definitions under `skills/`; the repository's root `AGENTS.md` configures agents working on `addyosmani/agent-skills` itself and should not be copied into other projects.

## Installation

Install only the skills you want to use.

### Project-local skills

Copy each selected skill into your project using OpenCode's skill layout:

```text
.opencode/skills/<skill-name>/SKILL.md
```

For example:

```text
.opencode/skills/debugging-and-error-recovery/SKILL.md
.opencode/skills/code-review-and-quality/SKILL.md
```

### Global skills

To make a skill available across projects, place it under:

```text
~/.config/opencode/skills/<skill-name>/SKILL.md
```

Do not copy this repository's root `AGENTS.md` into your own project. If you want project-level guidance, create an `AGENTS.md` tailored to that project instead.

## Optional project `AGENTS.md`

A small project-specific instruction can encourage consistent skill use without importing repository-maintainer rules:

```markdown
# Agent instructions

Before starting non-trivial work, check the available OpenCode skills.
When a task matches a skill, load that skill and follow its workflow.
Keep changes scoped to this repository and preserve its existing conventions.
```

Adapt that text to your codebase, team conventions, and risk level.

## How It Works

OpenCode discovers installed skills from its supported skill directories. Once the relevant skills are installed, the agent can select them based on the task and invoke the `skill` tool when appropriate.

Typical mappings include:

- feature design → `spec-driven-development`
- implementation planning → `planning-and-task-breakdown`
- incremental coding → `incremental-implementation`
- bug fixing → `debugging-and-error-recovery`
- code review → `code-review-and-quality`

The lifecycle remains:

- DEFINE → `spec-driven-development`
- PLAN → `planning-and-task-breakdown`
- BUILD → `incremental-implementation` + `test-driven-development`
- VERIFY → `debugging-and-error-recovery`
- REVIEW → `code-review-and-quality`
- SHIP → `shipping-and-launch`

## Slash commands

OpenCode also supports project commands under `.opencode/commands/`. They are optional: skills can still be used directly through agent-driven selection. If this repository provides OpenCode command definitions, install only the command files you want alongside your project configuration rather than copying repository-scoped maintainer instructions.

## Recommended Workflow

1. Install the small set of skills relevant to your project.
2. Add project-specific `AGENTS.md` guidance only when your repository needs it.
3. Ask for work in natural language.
4. Let the agent select and run the matching installed skill workflow.

## Summary

For OpenCode, reuse the files under `skills/`, not this repository's root `AGENTS.md`. Keep reusable skill content and project-specific agent instructions separate so updates remain predictable and your own repository rules stay authoritative.
