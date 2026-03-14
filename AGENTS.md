---
trigger: always_on
---

# Getting Started Context

Read `README.md` first for the tech stack, prerequisites, and copy-pasteable
commands to install, build, run, test, and lint the project.

# Documentation Context

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

# Documentation Maintenance

If any task modifies an aspect covered by the documentation (`docs/`), update
the corresponding documentation as part of the same task. The task is not
complete until the documentation reflects the changes.

If a change affects the getting-started experience (dependencies, commands,
project structure), update `README.md` as part of the same task.

# Agent Readiness

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

See `README.md` for a summary of the current readiness level.
