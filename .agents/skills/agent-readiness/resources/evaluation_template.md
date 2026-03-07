# Agent Readiness Evaluation — `{{REPO_NAME}}`

Based on [Factory AI Agent Readiness](https://docs.factory.ai/web/agent-readiness/overview),
adapted for Antigravity conventions.

## Ecosystem

| Property | Value |
| --- | --- |
| Language | {{LANGUAGE}} |
| Framework | {{FRAMEWORK}} |
| Package manager | {{PACKAGE_MANAGER}} |
| Detected tools | {{DETECTED_TOOLS}} |

## Current Readiness Summary

<!-- Fill one row per pillar. Use emoji: 🟢 (L3+), 🟡 (L2), 🔴 (L1) -->

| Pillar | Estimated Level | Score | Key Gap |
| --- | --- | --- | --- |
| Style & Validation | **L?** | ? | |
| Build System | **L?** | ? | |
| Testing | **L?** | ? | |
| Documentation | **L?** | ? | |
| Dev Environment | **L?** | ? | |
| Debugging & Observability | **L?** | ? | |
| Security | **L?** | ? | |
| Task Discovery | **L?** | ? | |
| Product & Experimentation | **L?** | ? | |

**Overall estimated level: L?**

---

## Detailed Pillar Evaluation

<!-- For each pillar, use this table format:

| Criterion | Status | Evidence |
|---|---|---|
| Criterion name | ✅/⚠️/❌ | File link or explanation |

-->

### 1. Style & Validation

| Criterion | Status | Evidence |
| --- | --- | --- |
| Linter configured | | |
| Code formatter | | |
| Type checker | | |
| Pre-commit hooks | | |
| CI enforces lint/format | | |
| Import sorting | | |

### 2. Build System

| Criterion | Status | Evidence |
| --- | --- | --- |
| Build command documented | | |
| Dependencies pinned | | |
| Single-command install | | |
| Reproducible CI builds | | |
| Dockerized build | | |

### 3. Testing

| Criterion | Status | Evidence |
| --- | --- | --- |
| Unit tests exist | | |
| Test framework configured | | |
| Tests runnable locally | | |
| CI runs tests | | |
| Coverage tracking | | |
| Coverage threshold | | |
| Integration tests | | |
| Test factories/fixtures | | |

### 4. Documentation

| Criterion | Status | Evidence |
| --- | --- | --- |
| README with setup | | |
| Architecture docs | | |
| Env vars documented | | |
| API documentation | | |
| Contributing guide | | |
| Changelog | | |
| Code conventions | | |

**D3 — Agent Context Content Quality**

| Sub-criterion | Status | Evidence | Source |
| --- | --- | --- | --- |
| D3.1 Tech stack documented | | | |
| D3.2 Build/run commands | | | |
| D3.3 Test commands | | | |
| D3.4 Lint/format commands | | | |
| D3.5 Project structure | | | |
| D3.6 Coding patterns | | | |
| D3.7 Architectural constraints | | | |
| D3.8 Doc maintenance rules | | | |

**D3 Score**: ___ / 8 → ✅ (≥6) / ⚠️ (3-5) / ❌ (≤2)

**Accuracy notes**: <!-- Document any mismatches between docs and actual config -->

### 5. Dev Environment

| Criterion | Status | Evidence |
| --- | --- | --- |
| Environment template | | |
| Devcontainer | | |
| Docker Compose local | | |
| One-command setup | | |
| Seed data mechanism | | |

### 6. Debugging & Observability

| Criterion | Status | Evidence |
| --- | --- | --- |
| Structured logging | | |
| Error tracking | | |
| Debug tools documented | | |
| Distributed tracing | | |
| Health check endpoint | | |

### 7. Security

| Criterion | Status | Evidence |
| --- | --- | --- |
| CODEOWNERS | | |
| Security linting | | |
| Dependency scanning | | |
| Secret scanning | | |
| Branch protection | | |

### 8. Task Discovery

| Criterion | Status | Evidence |
| --- | --- | --- |
| Issue templates | | |
| PR template | | |
| Issue labeling | | |
| Project board | | |

### 9. Product & Experimentation

| Criterion | Status | Evidence |
|---|---|---|
| Analytics instrumentation | | |
| Feature flags | | |
| Experiment infrastructure | | |

---

## Modernization Recommendations

<!-- List any legacy→modern tool migrations here. Use this format:

> [!WARNING]
> **Breaking change**: Replacing `{{OLD_TOOL}}` with `{{NEW_TOOL}}` in
> pre-commit hooks. Developers must update their local pre-commit installation.

| Current | Recommended | Rationale | Breaking? |
|---|---|---|---|
| old tool | new tool | reason | Yes/No |

-->

---

## Proposed Enhancement Plan

<!-- Group changes by the level they unlock -->

> [!IMPORTANT]
> This plan addresses **configuration and documentation changes only** unless a
> modernization migration explicitly requires code changes.

### Phase 1 — Unlock Level {{NEXT_LEVEL}} (Quick Wins)

<!-- List each file change:

#### [NEW] [filename](file:///absolute/path)
Description of what to create.

#### [MODIFY] [filename](file:///absolute/path)
Description of what to change.

#### [DELETE] [filename](file:///absolute/path)
Description of what to remove (only for replaced legacy files).

-->

### Phase 2 — Strengthen Level {{NEXT_LEVEL}}

<!-- More changes for solidifying the level -->

### Phase 3 — Path to Level {{NEXT_LEVEL + 1}}

<!-- Changes that push toward the next level -->

---

## Pros / Cons

| Pros | Cons |
| --- | --- |
| | |

## Verification Plan

### Automated Tests

```zsh
# Commands to verify the changes work
```

### Manual Verification

<!-- Steps that require human review, e.g. GitHub UI checks -->
