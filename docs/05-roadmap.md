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

**Automated Orchestration:**
Launch parallel tasks simultaneously across isolated sibling worktrees using:
```powershell
powershell -ExecutionPolicy Bypass -File .\scripts\run-parallel-agents.ps1 -TaskBase "m1"
```

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
- [ ] M1.3 ⇉ [T1-Lean] {{Lint rules & static audit helpers}}
  - Depends on: M0.5
  - Owned files: `scripts/lint/**`, `tests/test_lint.*`
  - Acceptance: `scripts/verify-gate.ps1 -Mode Fast`
**Exit:** All skeleton services initialize and unit tests pass cleanly.

## M2 — Core logic
- [ ] M2.1 ⇉ [T1-Lean] {{Core computation engine}}
  - Depends on: M1.1
  - Owned files: `src/core/engine/**`, `tests/test_engine.*`
  - Acceptance: Core unit test suite passes with 100% invariant coverage
- [ ] M2.2 ⇉ [T2-Mod] {{State management / storage adapter}}
  - Depends on: M1.1
  - Owned files: `src/storage/**`, `tests/test_storage.*`
  - Acceptance: Storage adapter unit tests pass
**Exit:** Core business logic invariants pass without mock dependencies.

## M3 — Integrations / Platform
- [ ] M3.1 ⇉ [T2-Mod] {{Platform OS / Win32 / Core Audio / Device API wrapper}}
  - Depends on: M2.1
  - Owned files: `src/platform/**`, `tests/test_platform.*`
  - Acceptance: Platform probe runs headless in fast gate
- [ ] M3.2 ⇉ [T1-Lean] {{Event bus & IPC protocol serializer}}
  - Depends on: M2.1
  - Owned files: `src/ipc/**`, `tests/test_ipc.*`
  - Acceptance: Protocol serialization roundtrip tests pass
**Exit:** Platform subsystem passes headless integration probes.

## M4 — UI & Ergonomics
- [ ] M4.1 ⇉ [T2-Mod] {{Main UI shell, screens, and view model}}
  - Depends on: M3.2
  - Owned files: `src/ui/**`, `src/components/**`
  - Acceptance: Component layout render tests pass without regression
- [ ] M4.2 ⇉ [T1-Lean] {{Localization & i18n dictionaries}}
  - Depends on: M4.1
  - Owned files: `locales/**`, `src/i18n/**`
  - Acceptance: Missing key lint check passes
**Exit:** UI screens crawl cleanly with zero dead buttons in `run-qa.ps1`.

## M5 — Hardening & verification
- [ ] M5.1 Measure every NFR budget and record the results in `docs/06-qa-and-validation.md`.
- [ ] M5.2 Soak / edge-case tests.
- [ ] M5.3 Audit any code produced by fallback models (see `docs/model-fallback-log.md`).
- [ ] M5.4 Run model optimization review (see `docs/model-optimization-report.md`).
- [ ] M5.5 Real-environment QA run by the user (manual matrix).
**Exit:** All NFR budgets verified; no un-audited fallback models.

## M6 — Packaging & release
- [ ] M6.1 Release script + portable zip + standalone setup executable (`scripts/package-release.ps1`).
- [ ] M6.2 WinGet & Scoop package manifests (`scripts/generate-manifests.ps1`).
- [ ] M6.3 User guide + documentation parity verified (`docs/user-guide.md`).
- [ ] M6.4 Tag release and verify GitHub Actions release workflow (`.github/workflows/release.yml`).
**Exit:** Pre-built release archive and manifests generated and verified.

## M7 — Retrospective
- [ ] M7.1 Run the `project-retrospective` skill and extract lessons learned into `docs/lessons-learned.md`.
- [ ] M7.2 Promote generic rules and tools tagged `[KIT]` into upstream project-kickstart templates.
