# Changelog & Development Log

Chronological record of milestones, decisions and discoveries. Newest first.

## 2026-11-01 — Multi-Agent Parallelism, Skill Scoping & Autonomous QA Architecture
- **Isolated Worktree Lifecycle (`scripts/manage-worktree.ps1`):** Enabled conflict-free parallel worker development using isolated git worktrees (`.worktrees/task-<id>`), automated gate verification, and Sole Committer rebase/merge.
- **Tiered Verification Gate (`scripts/verify-gate.ps1`):** Added dual-mode quality gate runner (`-Mode Fast` for incremental worker iteration; `-Mode Full` for lead committer release verification) with automatic stack detection (Rust, Node, Python, Go, Template) and millisecond timer auditing.
- **Dynamic Skill Scoping (`scripts/manage-skill.ps1` & `.agents/skills/skill-manager`):** Added hierarchical skill scoping between Workspace (0 global token cost) and Global Machine scopes to strictly respect the 20,000 token customization budget.
- **Autonomous QA Crawl Integration (`ui-qa-tester`):** Integrated non-intrusive headless and GUI crawler runner (`scripts/run-qa.ps1`), crawl session configuration (`qa-session.template.toml`), and workspace skill (`.agents/skills/project-qa`).
- **Cloud Worker & GitHub Copilot Protocol:** Standardized Cloud Worker integration via `.github/ISSUE_TEMPLATE/agent_task.yml`, `.github/copilot-instructions.md`, and the Draft PR pattern in `docs/multi-agent-methodology.md`.
- **Roadmap Disjoint File Contracts:** Added explicit `Tier`, `Depends on`, `Owned files`, and `Acceptance` metadata for parallel tasks (`⇉`) in `docs/05-roadmap.md`.

## 2026-10-31 — Project Template Bootstrap & Packaging Automation
