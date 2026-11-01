# 05 — Roadmap

> The single source of truth for tasks. Each task fits in **one conversation** (or one worker).
> Tick boxes with `(YYYY-MM-DD, <commit>)`. Don't start a milestone before the previous **Exit** is met.
> ⇉ = can run in parallel with the other ⇉ tasks in the same milestone (**strictly disjoint files**).

---

### Parallel Execution & Disjoint File Contract
Tasks marked with `⇉` can be delegated concurrently to local subagents (`project-worker`) or cloud workers (GitHub Copilot Agent).
To prevent git merge collisions and cognitive overlap, every parallel task must specify:
1. **Tier:** `T1-Lean` (pure logic, tests, schemas), `T2-Mod` (UI, IPC, platform), or `T3-Crit` (concurrency, hot paths, hardware).
2. **Depends On:** Explicit prerequisites or `None`.
3. **Owned Files:** Exact file paths or directory globs the worker is authorized to create/edit.
4. **Acceptance:** Command to run in `scripts/verify-gate.ps1 -Mode Fast`.

---

## M0 — Spikes 🔬 (decision gate)
- [ ] M0.1 Project skeleton + verification gate working locally (and in CI if applicable).
- [ ] M0.2 ⇉ [T1-Lean] Probe/prototype for {{unknown #1}}.
  - Depends on: M0.1
  - Owned files: `probes/spike1/**`
  - Acceptance: Invariant probe runs headless and outputs empirical metrics
- [ ] M0.3 ⇉ [T1-Lean] Probe/prototype for {{unknown #2}}.
  - Depends on: M0.1
  - Owned files: `probes/spike2/**`
  - Acceptance: Invariant probe runs headless and outputs empirical metrics
- [ ] M0.4 User runs the probes in the real environment; results go into `docs/{{spike}}-findings.md`.
- [ ] M0.5 Resolve the 🔬 items in requirements/architecture and record any design change as an ADR.
**Exit:** every 🔬 item resolved or has an accepted fallback.

## M1 — Skeleton
- [ ] M1.1 ⇉ [T1-Lean] {{Data models & schemas}}
  - Depends on: M0.5
  - Owned files: `src/models/**`, `tests/test_models.*`
  - Acceptance: `scripts/verify-gate.ps1 -Mode Fast`
- [ ] M1.2 ⇉ [T2-Mod] {{Platform IPC / base service skeleton}}
  - Depends on: M0.5
  - Owned files: `src/service/**`, `tests/test_service.*`
  - Acceptance: `scripts/verify-gate.ps1 -Mode Fast`
**Exit:** {{measurable}}

## M2 — Core logic
- [ ] M2.1 ⇉ [T1-Lean] {{Core computation engine}}
  - Depends on: M1.1
  - Owned files: `src/core/engine/**`, `tests/test_engine.*`
  - Acceptance: Core unit test suite passes with 100% invariant coverage
- [ ] M2.2 ⇉ [T2-Mod] {{State management / storage adapter}}
  - Depends on: M1.1
  - Owned files: `src/storage/**`, `tests/test_storage.*`
  - Acceptance: Storage adapter unit tests pass
**Exit:** {{}}

## M3 — Integrations / platform

## M4 — UI

## M5 — Hardening & verification
- [ ] M5.1 Measure every NFR budget and record the results in `docs/06-qa-and-validation.md`.
- [ ] M5.2 Soak / edge-case tests.
- [ ] M5.3 Audit any code produced by fallback models (see `docs/model-fallback-log.md`).
- [ ] M5.4 Real-environment QA run by the user (manual matrix).

## M6 — Packaging & release
- [ ] M6.1 Release script + artifact.
- [ ] M6.2 User guide + known limitations.
- [ ] M6.3 First release following `docs/release-methodology.md`.

## M7 — Retrospective
- [ ] M7.1 Run the `project-retrospective` skill and feed the lessons back into the kit.
