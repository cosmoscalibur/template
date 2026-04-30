# Agent-Ready Repository Template

A GitHub template repository that bootstraps projects for autonomous
AI-assisted development. It provides an `AGENTS.md` entry file, an
agent-readiness evaluation skill, and behavioral guidelines — so every new
project starts with a consistent, agent-friendly foundation.

## What's Included

| Component | Path | Purpose |
| --- | --- | --- |
| Agent entry file | `AGENTS.md` | Universal context file loaded by AI agents on every task |
| Agent-readiness skill | `.agents/skills/agent-readiness/` | Evaluates a repo's readiness for autonomous AI development |

## Design Decisions

### Agent Readiness Framework

The agent-readiness skill is based on
[Factory AI's Agent Readiness](https://docs.factory.ai/web/agent-readiness/overview),
adapted to modern tooling standards (e.g., ruff over black+isort, uv over pip,
`just` over make). It evaluates repositories across 9 pillars — from basic
linting to full product experimentation — and produces a scored report with a
phased enhancement plan.

### Behavioral Guidelines

`AGENTS.md` includes behavioral instructions derived from
[Andrej Karpathy's recommendations](https://github.com/forrestchang/andrej-karpathy-skills)
for reducing common LLM coding mistakes. These bias toward caution over speed:
think before coding, prefer simplicity, make surgical changes, and define
verifiable success criteria. For trivial tasks, agents should use judgment.

## Project Structure

```text
.
├── AGENTS.md                          # Agent context (hot memory)
├── README.md                          # This file
└── .agents/
    └── skills/
        └── agent-readiness/           # Readiness evaluation skill
            ├── SKILL.md               # Skill instructions
            └── resources/             # Evaluation templates & references
```

## Usage

### As a Template

Use this repository as a
[GitHub template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)
to create new projects. After creating, customize `AGENTS.md` to reference your
project's specific `docs/` and `README.md`.

### Running the Agent-Readiness Evaluation

Ask your AI agent:

```text
Evaluate this repository for agent readiness. Repository type: both,
documentation language: English, project type: cli-tool.
```

The skill will audit the repo across 9 pillars and produce a phased enhancement
plan saved to `docs/agent-readiness/`.
