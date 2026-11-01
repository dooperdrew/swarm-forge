# Changelog & Development Log

Chronological record of milestones, decisions and discoveries. Newest first.

## 2026-11-01 — Autonomous AI Model Optimization, Parallel Worker Swarms & Complete Pipeline Hardening
- **Autonomous Model Optimizer (`.agents/skills/model-optimizer`):** Introduced a continuous learning engine with `scripts/collect-model-stats.ps1`, `scripts/apply-model-optimisation.ps1`, and background daemon `scripts/start-model-optimiser.ps1`. Automatically benchmarks subagent latency, token consumption, and success rates ($\ge 95\%$) in `.agents/config/model-stats.json`, dynamically promoting low-token models (`flash_lite`) in `.agents/config/model-default.toml` and reporting history in `docs/model-optimization-report.md`.
- **Parallel Subagent Orchestration (`scripts/run-parallel-agents.ps1`):** Created a turnkey multi-worker launcher that spawns isolated Git worktrees (`.worktrees/<task-id>`), enforces disjoint file ownership, dispatches lightweight subagent workers, and verifies quality via the fast gate.
- **Verification Gate Dry-Run Mode (`scripts/verify-gate.ps1`):** Added `-DryRun` switch for pre-flight stage inspection without executing side-effects.
- **CI Matrix & Automated Telemetry Pipeline (`.github/workflows/ci.yml`):** Rebuilt GitHub Actions CI with parallel matrix tasks (`lint`, `test`, `build`), automated script audits, and post-test model optimization metrics ingestion.
- **Release Automation Hardening (`.github/workflows/release.yml`):** Enhanced release workflow with checksum publishing (`.sha256`), standalone setup executables (`*-Setup.exe`), and GitHub Releases integration.
- **Skill Privacy & Path Sanitization (`scripts/manage-skill.ps1`):** Sanitized user profile paths in console outputs (`~`), preventing accidental disclosure of local directory trees.
- **Cross-Platform Git Hygiene (`.gitattributes` & `.gitignore`):** Enforced LF/CRLF normalization, explicit UTF-8 encoding, and exclusion of transient task outputs (`.system_generated/`).
- **Complete Documentation Parity:** Updated `README.md`, `docs/README.md`, `docs/05-roadmap.md`, `docs/skill-scope.md`, and `docs/model-fallback-log.md` with complete architecture maps, badges, and cross-references.

## 2026-11-01 — Multi-Agent Parallelism, Skill Scoping & Autonomous QA Architecture
- **Isolated Worktree Lifecycle (`scripts/manage-worktree.ps1`):** Enabled conflict-free parallel worker development using isolated git worktrees (`.worktrees/task-<id>`), automated gate verification, and Sole Committer rebase/merge.
- **Tiered Verification Gate (`scripts/verify-gate.ps1`):** Added dual-mode quality gate runner (`-Mode Fast` for incremental worker iteration; `-Mode Full` for lead committer release verification) with automatic stack detection (Rust, Node, Python, Go, Template) and millisecond timer auditing.
- **Dynamic Skill Scoping (`scripts/manage-skill.ps1` & `.agents/skills/skill-manager`):** Added hierarchical skill scoping between Workspace (0 global token cost) and Global Machine scopes to strictly respect the 20,000 token customization budget.
- **Autonomous QA Crawl Integration (`ui-qa-tester`):** Integrated non-intrusive headless and GUI crawler runner (`scripts/run-qa.ps1`), crawl session configuration (`qa-session.template.toml`), and workspace skill (`.agents/skills/project-qa`).
- **Cloud Worker & GitHub Copilot Protocol:** Standardized Cloud Worker integration via `.github/ISSUE_TEMPLATE/agent_task.yml`, `.github/copilot-instructions.md`, and the Draft PR pattern in `docs/multi-agent-methodology.md`.
- **Roadmap Disjoint File Contracts:** Added explicit `Tier`, `Depends on`, `Owned files`, and `Acceptance` metadata for parallel tasks (`⇉`) in `docs/05-roadmap.md`.

## 2026-10-31 — Project Template Bootstrap & Packaging Automation
