---
name: Agent Readiness Evaluation
description: >
  Evaluate a repository's readiness for autonomous AI agent development, based
  on Factory AI's agent readiness framework adapted to the Antigravity agent.
  Produces a scored report across 9 pillars with a phased enhancement plan.
---

# Agent Readiness Evaluation

Evaluate how well a codebase supports autonomous AI-assisted development.
Based on [Factory AI Agent Readiness](https://docs.factory.ai/web/agent-readiness/overview),
adapted to Antigravity conventions and modern tooling standards.

## When to Use

- Onboarding a new repository for AI-assisted development.
- Periodic audits to find improvement areas.
- Planning modernization efforts for developer tooling.

## Workflow

### Step 1 — Detect the Ecosystem

Identify the primary language and framework by inspecting root-level files:

| Indicator Files | Ecosystem |
|---|---|
| `pyproject.toml`, `setup.py`, `requirements.txt` | Python |
| `Cargo.toml` | Rust |
| `package.json` + React in deps | React (Node.js) |
| `package.json` (no framework) | Vanilla JS / Node.js |
| `package.json` + TypeScript in deps | TypeScript |
| `go.mod` | Go |
| `Gemfile` | Ruby |
| `notebooks/`, `*.ipynb`, ML deps (torch, tensorflow, sklearn) | AI Development |
| `cloudbuild.yaml`, `app.yaml`, `.gcloudignore` | GCP Infrastructure |

Record the ecosystem; it determines which modernization recommendations apply
(see `resources/modernization_recommendations.md`).

### Step 2 — Audit Each Pillar

Evaluate the repository against the **9 pillars** listed below. For each
criterion, check whether evidence exists in the repo. Mark as:

- ✅ **Pass** — criterion fully met
- ⚠️ **Partial** — exists but incomplete/outdated
- ❌ **Fail** — not found

#### Pillar 1: Style & Validation

| # | Criterion | What to Look For |
|---|---|---|
| S1 | Linter configured | Config file for a linter (ruff, eslint, clippy, golangci-lint) |
| S2 | Code formatter configured | Formatter config or "format" in linter config (ruff format, prettier, rustfmt) |
| S3 | Type checker configured | Type checker config (pyright/mypy, TypeScript strict, Rust is typed by default) |
| S4 | Pre-commit hooks | `.pre-commit-config.yaml` or husky/lint-staged; hooks must match current tools |
| S5 | CI enforces lint/format | CI workflow step that runs linter and formatter in check mode |
| S6 | Import sorting | Import sort configured (ruff `I`, eslint-plugin-import, goimports) |

**Modernization signals**: If the repo uses isort/black/pylint separately →
recommend consolidation to ruff. If it uses tslint → recommend eslint. See
`resources/modernization_recommendations.md`.

#### Pillar 2: Build System

| # | Criterion | What to Look For |
|---|---|---|
| B1 | Build command documented | README or docs describe how to build/run |
| B2 | Dependencies pinned | Lockfile exists (uv.lock, package-lock.json, Cargo.lock, go.sum) |
| B3 | Single-command install | One command installs all deps (uv sync, npm ci, cargo build) |
| B4 | Reproducible CI builds | CI uses lockfile for dependency resolution |
| B5 | Dockerized build | Dockerfile or compose file for containerised builds |

**Modernization signals**: `requirements.txt` → `pyproject.toml` + uv.
`setup.py` only → `pyproject.toml`. `yarn` classic → `yarn berry` or `pnpm`.

#### Pillar 3: Testing

| # | Criterion | What to Look For |
|---|---|---|
| T1 | Unit tests exist | Test files in the repo (test_*.py, *.test.ts, *_test.go) |
| T2 | Test framework configured | Config file (pytest.ini, jest.config, Cargo test) |
| T3 | Tests runnable locally | Single documented command to run tests |
| T4 | CI runs tests | CI workflow step that executes tests |
| T5 | Coverage tracking | Coverage config or CI coverage step |
| T6 | Coverage threshold | Minimum coverage enforced (fail_under, coverageThreshold) |
| T7 | Integration tests exist | Tests that exercise external dependencies or multi-component flows |
| T8 | Test factories/fixtures | Data generation patterns (factory_boy, fishery, faker) |

**Modernization signals**: unittest → pytest. mocha → jest/vitest.

#### Pillar 4: Documentation

| # | Criterion | What to Look For |
|---|---|---|
| D1 | README with setup instructions | README.md with build, run, test commands |
| D2 | Architecture documentation | `docs/` or `docs/architecture/` with design docs |
| D3 | Agent context — content quality | See D3 sub-checks below |
| D4 | Environment variables documented | `.env.example`, settings docs, or env var table in README |
| D5 | API documentation | Swagger/OpenAPI, or API docs (drf-spectacular, tsoa, protobuf docs) |
| D6 | Contributing guide | CONTRIBUTING.md or contributing section in README |
| D7 | Changelog | CHANGELOG.md or release notes |
| D8 | Code conventions documented | Style guide, naming conventions, patterns documented |

**D3 — Agent Context Content Quality**

Instead of `AGENTS.md` (Factory AI convention), Antigravity uses `.agent/rules/`
for always-on agent context plus the README. D3 is **not** a file-existence
check — it evaluates whether the combined content across README,
`.agent/rules/`, docs, and config files gives an agent enough information to
work autonomously. Check each sub-criterion:

| # | Sub-criterion | What to Look For | Where |
|---|---|---|---|
| D3.1 | Tech stack documented | Language, framework, major libraries, and their versions are stated | README or `.agent/rules/` |
| D3.2 | Build/run commands | Exact commands to install deps, build, and run locally (copy-pasteable, not prose) | README |
| D3.3 | Test commands | Exact command to run tests + any prerequisites (DB, env vars, static files) | README or `.agent/rules/` |
| D3.4 | Lint/format commands | Exact commands to lint and format (e.g., `uv run ruff check --fix .`) | README, `.agent/rules/`, or docs |
| D3.5 | Project structure | Directory layout with purpose of each top-level directory | README or docs |
| D3.6 | Coding patterns | Key patterns the agent must follow (model conventions, service layer, naming) | `.agent/rules/` or docs |
| D3.7 | Architectural constraints | Things the agent should NOT do, deprecated modules, migration-in-progress areas | `.agent/rules/` |
| D3.8 | Doc maintenance rules | Instructions to keep docs in sync when modifying code | `.agent/rules/` |

**Scoring D3**:

- ✅ **Pass**: ≥ 6 of 8 sub-criteria present with accurate, current content
- ⚠️ **Partial**: 3-5 sub-criteria present, or content exists but is outdated
- ❌ **Fail**: ≤ 2 sub-criteria present, or no agent-oriented context at all

**Evaluating content accuracy**: For each sub-criterion, verify that the
documented commands/versions match the actual config files (e.g., does the
README say `pytest` but `pytest.ini` doesn't exist? Does it say Python 3.9 but
`pyproject.toml` says 3.13?).

#### Pillar 5: Dev Environment

| # | Criterion | What to Look For |
| --- | --- | --- |
| E1 | Environment template | `.env.example` or `envfile.template` with placeholder values |
| E2 | Devcontainer config | `.devcontainer/devcontainer.json` |
| E3 | Docker Compose for local services | `docker-compose.yml` with DB, cache, etc. |
| E4 | One-command local setup | Makefile target, script, or documented single command |
| E5 | Seed data mechanism | Fixtures, seeders, or migration-based data population |

#### Pillar 6: Debugging & Observability

| # | Criterion | What to Look For |
| --- | --- | --- |
| O1 | Structured logging configured | Logging library with JSON/structured output (structlog, winston, tracing) |
| O2 | Error tracking | Sentry, Bugsnag, or equivalent integration |
| O3 | Debug tools documented | Debug instructions (debugpy, delve, node --inspect) |
| O4 | Distributed tracing | OpenTelemetry, Jaeger, or cloud-native tracing |
| O5 | Health check endpoint | `/health` or `/readiness` endpoint |

#### Pillar 7: Security

| # | Criterion | What to Look For |
| --- | --- | --- |
| X1 | CODEOWNERS file | `.github/CODEOWNERS` or `CODEOWNERS` |
| X2 | Security linting rules | Security rules enabled in linter (ruff S, eslint-plugin-security, cargo-audit) |
| X3 | Dependency vulnerability scanning | Dependabot, Snyk, or `cargo audit` in CI |
| X4 | Secret scanning | GitHub secret scanning, gitleaks, or trufflehog |
| X5 | Branch protection | Require PR reviews, status checks (GitHub setting — note if cannot audit locally) |

#### Pillar 8: Task Discovery

| # | Criterion | What to Look For |
| --- | --- | --- |
| K1 | Issue templates | `.github/ISSUE_TEMPLATE/` directory with templates |
| K2 | PR template | `.github/pull_request_template.md` (must be GitHub-discoverable path) |
| K3 | Issue labeling system | `.github/labels.yml` or documented label taxonomy |
| K4 | Project board / tracking | Link to project board or tracking tool |

#### Pillar 9: Product & Experimentation

| # | Criterion | What to Look For |
| --- | --- | --- |
| P1 | Analytics instrumentation | Analytics SDK configured (Segment, Amplitude, PostHog) |
| P2 | Feature flags | Feature flag system (LaunchDarkly, Unleash, env-based flags) |
| P3 | Experiment infrastructure | A/B testing framework or experiment docs |

### Step 3 — Score and Determine Level

Count pass/partial/fail per pillar. Scoring rules:

- ✅ = 1 point
- ⚠️ = 0.5 points
- ❌ = 0 points

**Level thresholds** (based on total criteria across ALL pillars):

| Level | Requirement |
| --- | --- |
| L1 | Starting point (all repos) |
| L2 | ≥ 80% of L1 criteria pass (S1-S3, B1-B2, T1-T4, D1, D3, E3, X1) |
| L3 | L2 + ≥ 80% of L2 criteria (S4-S5, B3-B4, T5-T6, D2, D4-D5, E1-E2, O1-O2, X2-X3, K1-K2) |
| L4 | L3 + ≥ 80% of L3 criteria (S6, B5, T7-T8, D6-D8, E4-E5, O3-O5, X4-X5, K3-K4) |
| L5 | L4 + ≥ 80% of L4 criteria (P1-P3 + all remaining) |

### Step 4 — Generate the Enhancement Plan

Use the template in `resources/evaluation_template.md` to produce the final
report. The plan must follow these rules:

1. **Phase by level**: Group enhancements by the level they unlock.
2. **Modernize, don't pile on**: If a legacy tool exists, recommend migration to
   the modern equivalent (see `resources/modernization_recommendations.md`)
   rather than adding a parallel tool. Mark legacy as "replace" not "add alongside".
3. **Antigravity conventions**: Use `.agent/rules/` for agent context instead of
   `AGENTS.md`. Use `.agent/workflows/` for repeatable commands.
4. **Minimal invasiveness**: Prefer config/documentation changes over code
   changes. Code changes only when a modernization migration requires it
   (e.g., switching test framework).
5. **Explicit breaking changes**: If a modernization would break existing
   workflows (e.g., replacing isort hook with ruff), note it with a
   `> [!WARNING]` callout.
6. **Pros/Cons table**: Every plan must end with a pros/cons comparison.
7. **Verification plan**: Include automated and manual verification steps.

### Step 5 — Present to User

Use `notify_user` with `BlockedOnUser: true` to request review of the
implementation plan. Include questions about:

- Team ownership for CODEOWNERS
- Environment variable sources for `.env.example`
- Preferences on migration breaking changes
- Which phases to implement

## Output Artifacts

The skill produces one artifact:

| File | Content |
| --- | --- |
| `implementation_plan.md` | Evaluation report + phased enhancement plan (use template) |
