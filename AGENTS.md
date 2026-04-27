---
trigger: always_on
---

# Agent Guidelines

## Getting Started

Read `README.md` first for the tech stack, prerequisites, and copy-pasteable
commands to install, build, run, test, and lint the project.

## Documentation

### Context

Read `docs/README.md` first for an index of available documentation, then read
the relevant sections for context about the application architecture, design
decisions, coding patterns, and development recommendations before making
changes that affect the application structure.

Read coding patterns and contributing guide **before planning and
implementing** any task — these contain architectural constraints and
conventions that apply to both humans and agents.

When the scope of a task is not clearly defined, files are not explicitly given,
or the shared scope may be incomplete, complement your understanding by reading
relevant sections of `docs/` before proceeding.

### Maintenance

If any task modifies an aspect covered by the documentation (`docs/`), update
the corresponding documentation as part of the same task. The task is not
complete until the documentation reflects the changes.

If a change affects the getting-started experience (dependencies, commands,
project structure), update `README.md` as part of the same task.

## Agent Readiness

This project follows the
[agent-readiness framework](docs/agent-readiness/) to track its readiness for
autonomous AI-assisted development. Re-evaluate the project using the
agent-readiness skill and save the updated report to `docs/agent-readiness/`
when any of the following change:

- CI/CD pipelines or workflows
- Linter, formatter, or type-checker configuration
- Test infrastructure or coverage tooling
- Documentation structure (`docs/`, `README.md`, `AGENTS.md`)
- Build system, Docker, or devcontainer setup
- Project dependencies that affect tooling (e.g., adding pre-commit)

See `README.md` or last saved report `docs/agent-readiness/` for a summary of the current readiness level.

## Reducing Common LLM Mistakes

[Behavioral guidelines](https://github.com/forrestchang/andrej-karpathy-skills) to reduce common LLM coding mistakes. These bias toward
caution over speed — for trivial tasks, use judgment.

### Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:

- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them — don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

### Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes,
simplify.

### Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:

- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it — don't delete it.

When your changes create orphans:

- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

### Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:

- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:

```text
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it
work") require constant clarification.
