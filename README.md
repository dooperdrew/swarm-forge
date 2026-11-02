<p align="center">
  <img src=".github/assets/hero-banner.svg" alt="SwarmForge — Spec-First Autonomous Multi-Agent Engineering Forge" width="100%">
</p>

# ⚡ SwarmForge

<p align="center">
  <strong>The spec-first engineering forge for autonomous AI coding swarms and human engineers.</strong>
</p>

<p align="center">
  <a href="https://github.com/dooperdrew/swarm-forge/generate">
    <img src="https://img.shields.io/badge/Use%20this%20template-2ea44f?style=for-the-badge&logo=github&logoColor=white" alt="Use this template">
  </a>
</p>

<p align="center">
  <a href="docs/README.md"><img src="https://img.shields.io/badge/Architecture-Spec--First-blue.svg?style=flat-square" alt="Spec-First"></a>
  <a href="AGENTS.md"><img src="https://img.shields.io/badge/AI-Agent--Ready-success.svg?style=flat-square" alt="Agent-Ready"></a>
  <a href="docs/multi-agent-methodology.md"><img src="https://img.shields.io/badge/Workflow-Antigravity%20%2B%20Copilot-orange.svg?style=flat-square" alt="Multi-Agent"></a>
  <a href="docs/model-optimization-report.md"><img src="https://img.shields.io/badge/Model-Self--Tuning-brightgreen.svg?style=flat-square" alt="Model-Optimized"></a>
  <a href="scripts/run-parallel-agents.ps1"><img src="https://img.shields.io/badge/Worktrees-Isolated%20Parallel-teal.svg?style=flat-square" alt="Parallel-Worktrees"></a>
  <a href="scripts/verify-gate.ps1"><img src="https://img.shields.io/badge/Verification-Sub--Second%20Gate-purple.svg?style=flat-square" alt="Verification Gate"></a>
  <a href=".github/workflows/ci.yml"><img src="https://img.shields.io/badge/GitHub-Actions%20CI%2FCD-2088FF.svg?style=flat-square" alt="CI/CD"></a>
  <a href="CODE_OF_CONDUCT.md"><img src="https://img.shields.io/badge/Community%20Health-100%25-brightgreen.svg?style=flat-square" alt="Community Health"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square" alt="License: MIT"></a>
</p>

---

## 🌟 The SwarmForge Narrative & Philosophy

Modern software development with autonomous AI coding agents (Antigravity, GitHub Copilot, Claude Code, Cursor) is blazing fast. However, without strict architectural discipline and boundary enforcement, unguided agents rapidly induce systemic entropy:

* **🧠 Context Drift:** Agents lose track of architecture decisions, data schemas, and non-goals established in earlier conversations.
* **🔬 Hallucinated Assumptions:** Agents fabricate unverified hardware behaviors, remote APIs, and network protocols as fact.
* **💥 Git Collision Chaos:** Unbounded agents edit overlapping files, overwrite each other's work, and break `main`.
* **💸 Token Burn:** Dispatching heavyweight frontier reasoning models to trivial unit tests, documentation, or boilerplate exhausts budgets.
* **🌫️ Ephemeral Learning:** Critical debugging lessons and edge-case fixes evaporate the moment a conversation ends.

### The Swarm & The Forge
**SwarmForge eliminates this entropy through two complementary forces:**

1. **🐝 The Swarm:** A coordinated division of labor. A Lead Architect agent (**Sole Committer**) decomposes milestones into bounded tasks with strict disjoint file ownership. Autonomous worker swarms (`project-worker`, Copilot Cloud workers) execute concurrently in **isolated git worktrees** using cost-optimized models (`flash_lite`).
2. **🔥 The Forge:** An unyielding quality barrier. Every change is tempered through living markdown specifications (`docs/`), sub-second tiered verification gates (`verify-gate.ps1`), non-intrusive UI QA (`ui-qa-tester`), and continuous persistent learning (`docs/lessons-learned.md`).

---

## 🤖 Supported AI Agents & Ecosystem Matrix

This framework is built for polyglot software development (Rust, TypeScript/React/Node, Python, Go) and coordinates seamlessly across all major AI coding environments:

| Agent / Environment | Primary Role in Framework | Integration Mechanism | Concurrency Isolation |
|---|---|---|---|
| **Google Antigravity** | Lead Orchestrator & **Sole Committer** | Reads [`AGENTS.md`](AGENTS.md), drives milestones, runs verification gates | Interactive Lead Session |
| **GitHub Copilot Agent** | Asynchronous Cloud Worker | Consumes [`.github/ISSUE_TEMPLATE/agent_task.yml`](.github/ISSUE_TEMPLATE/agent_task.yml), adheres to [`.github/copilot-instructions.md`](.github/copilot-instructions.md) | Draft PRs (`task/<issue>-<desc>`) |
| **Claude Code** | Terminal & CLI Worker | Follows bounded tasks in [`docs/05-roadmap.md`](docs/05-roadmap.md), executes pre-commit gates | Isolated git worktrees (`.worktrees/`) |
| **Cursor / Windsurf** | In-Editor Composer & Agent | Enforces module boundaries in [`docs/03-architecture.md`](docs/03-architecture.md) | Branch / Worktree |
| **Autonomous Subagents** | Lightweight Worker Swarms (`project-worker`) | Dispatched via `scripts/run-parallel-agents.ps1`, routed dynamically to `flash_lite` | Disjoint file ownership & worktrees |

---

## 🏛️ Core Architectural Pillars

### 1. The Complete Spec Stack (`docs/`)
All knowledge lives in version-controlled markdown specifications before any application code is written.

```mermaid
flowchart TD
    subgraph Spec["Specification Layer"]
        V["docs/01-vision.md<br/><b>Vision & Non-Goals</b>"]
        R["docs/02-requirements.md<br/><b>MoSCoW & Budgets</b>"]
        A["docs/03-architecture.md<br/><b>Components & Boundaries</b>"]
        U["docs/04-ux.md<br/><b>Interaction & Screens</b>"]
    end
    subgraph Execution["Execution & Verification"]
        M["docs/05-roadmap.md<br/><b>Milestones (M0-M7)</b>"]
        Q["docs/06-qa-and-validation.md<br/><b>Empirical QA & NFRs</b>"]
        SPK["docs/m0-spike-findings.md<br/><b>Diagnostic Spike Ground Truth</b>"]
        G["AGENTS.md<br/><b>Verification Gate & Operating Rules</b>"]
        METH["docs/multi-agent-methodology.md<br/><b>Parallel & Cloud Orchestration</b>"]
    end
    subgraph Evolution["Product & Community"]
        UX7["docs/07-ux-and-improvements.md<br/><b>UX & Onboarding Backlog</b>"]
        COM8["docs/08-community-and-growth-strategy.md<br/><b>Distribution & Community</b>"]
        UG["docs/user-guide.md<br/><b>User Documentation & FAQ</b>"]
    end
    subgraph Learning["Living Memory"]
        LL["docs/lessons-learned.md<br/><b>Continuous Feedback Loop</b>"]
        ADR["docs/decisions/<br/><b>Architecture Decision Records</b>"]
        RETRO["docs/retrospective.md<br/><b>Milestone Retrospectives</b>"]
    end

    V --> R --> A --> U --> M
    M --> G
    G --> Q
    Q --> SPK
    SPK --> UX7 --> COM8 --> METH --> UG
    Q -.-> LL
    LL -.-> RETRO
    A -.-> ADR
```

Detailed guides for each document are available in the [Documentation Guide](docs/README.md).
- See the **Skill Scope Guide** for managing local vs global skills: [docs/skill-scope.md](docs/skill-scope.md)

---

### 2. Dual-Agent Parallel Architecture: Antigravity + GitHub Copilot
This template pioneers a hybrid **Hub-and-Spoke** division of labor combining local interactive reasoning with asynchronous cloud agent execution:

```mermaid
flowchart TD
    USER["User / Product Owner"] -->|"High-Level Directives & Milestones"| LEAD["Lead Orchestrator (Antigravity)<br/>• Sole Committer to main<br/>• Decomposes milestones into bounded issues<br/>• Runs verification gate & merges PRs"]
    
    subgraph LOCAL["Local Worker Subagents (project-worker)"]
        W1["Subagent: Tier 1 (Flash / Flash-Lite)<br/>Pure Logic, Schemas, Unit Tests"]
        W2["Subagent: Tier 2 (Flash / Pro)<br/>UI Layouts, IPC, Platform Wrappers"]
    end

    subgraph CLOUD["Cloud Worker Agent (GitHub Copilot Agent)"]
        COPILOT["GitHub Copilot Agent (Cloud / IDE)<br/>• Consumes agent_task.yml Issues<br/>• Scoped to disjoint file boundaries<br/>• Generates draft code & tests<br/>• Submits Draft Pull Requests"]
    end
    
    LEAD -->|"Spawns in isolated branch"| W1
    LEAD -->|"Spawns in isolated branch"| W2
    LEAD -->|"Creates Issue via agent_task.yml"| COPILOT
    
    W1 -->|"Completion Report"| LEAD
    W2 -->|"Completion Report"| LEAD
    COPILOT -->|"Draft PR (task/<issue-id>-<desc>)"| LEAD
    
    LEAD -->|"Pulls branch locally & runs Verification Gate"| GATE{"Verification Gate<br/>Lint + Tests + Budgets"}
    GATE -->|"Pass"| MERGE["git commit & git push origin main<br/>Close issue & update docs"]
    MERGE --> GITHUB[("GitHub main & Releases")]
```

- **Antigravity (Local Lead Agent):** Acts as the Lead Architect and **Sole Committer**. It analyzes dependencies, defines self-contained issues using [`.github/ISSUE_TEMPLATE/agent_task.yml`](.github/ISSUE_TEMPLATE/agent_task.yml), verifies incoming pull requests locally, and updates documentation.
- **GitHub Copilot Agent (Cloud Worker):** Acts as the **Fast Draft Implementer**. It consumes GitHub Issues in the cloud or IDE, adheres to [`.github/copilot-instructions.md`](.github/copilot-instructions.md), writes unit tests, and submits **Draft Pull Requests**. It is strictly forbidden from committing directly to `main`.
- Read the full [Multi-Agent Methodology Guide](docs/multi-agent-methodology.md) for sequence diagrams and protocol details.

---

### 3. Complexity Tiers & Model Routing
Tasks are categorized by complexity to optimize both execution speed and cognitive capability:

| Tier | Scope | Recommended Model |
|---|---|---|
| **T1 Lean** | Pure deterministic logic, data schemas, unit tests, i18n, build scripts, docs | Fast / Lightweight models (e.g., Flash, Haiku) |
| **T2 Moderate** | UI layouts, standard IPC, platform integrations, standard REST/gRPC endpoints | Balanced models (e.g., Sonnet, Pro) |
| **T3 Critical** | Concurrency, safety-critical routines, crypto, custom hardware/kernel hooks, performance hot paths | High-reasoning models (e.g., Pro, Opus) |

*Any model downgrade due to quota or rate-limiting is logged in [`docs/model-fallback-log.md`](docs/model-fallback-log.md) for mandatory audit before release.*

---

### 4. Claims Follow Evidence & Autonomous QA
- **No Guesswork:** Never present unverified assumptions (hardware behaviors, external APIs, network latency) as fact.
- **Spikes (🔬):** Unverified technical points are isolated as Milestone 0 spikes and documented with real outputs in [`docs/m0-spike-findings.md`](docs/m0-spike-findings.md).
- **Autonomous UI & A11y QA (`ui-qa-tester`):** Test UI screens and accessibility non-intrusively via `qa-session.template.toml` and `scripts/run-qa.ps1`.
- **Isolated Parallel Worktrees (`scripts/manage-worktree.ps1`):** Instantly spawn, test, and merge isolated sibling worktrees (`.worktrees/task-<id>`) so multiple agents or developers run parallel tasks with zero git collisions.
- **Tiered Verification Gate (`scripts/verify-gate.ps1`):** Fast incremental pre-commit checks (`-Mode Fast`) for rapid worker subagent iteration, and comprehensive build/lint/test release checks (`-Mode Full`) for the Lead Sole Committer.
- **Dynamic Skill Scoping (`manage-skill.ps1`):** Keep agent skills local to the workspace (`.agents/skills/`) to consume **0 global customization tokens**, or promote proven skills globally (`~/.gemini/config/skills/`) on demand.
- **Decoupled QA:** Automated invariant tests run on every commit; manual or hardware testing stays marked **`Pending`** in [`docs/06-qa-and-validation.md`](docs/06-qa-and-validation.md) until empirically confirmed. Community testers report results via [`.github/ISSUE_TEMPLATE/qa_verification.yml`](.github/ISSUE_TEMPLATE/qa_verification.yml).

---

### 5. Continuous Learning & Retrospectives
- **Living Lessons Learned:** When an agent receives a correction or encounters friction, it documents the root cause and creates an actionable rule in [`docs/lessons-learned.md`](docs/lessons-learned.md).
- **Repository Operating Rules:** Universal rules are promoted to [`AGENTS.md`](AGENTS.md) and [`.github/copilot-instructions.md`](.github/copilot-instructions.md).
- **Milestone Retrospectives:** Finished milestones undergo structured retrospectives in [`docs/retrospective.md`](docs/retrospective.md) analyzing failure modes, velocity, and multi-agent token economics.

---

## 📦 Automated Release & Multi-Channel Distribution

The repository includes pre-configured automation scripts in `scripts/`:
- **Portable Packaging (`scripts/package-release.ps1`):** Builds release binaries, stages documentation and assets, creates `.zip` archives, and computes SHA-256 checksums.
- **Package Manager Manifests (`scripts/generate-manifests.ps1`):** Automatically produces Windows Package Manager (**WinGet**) and **Scoop** manifests.
- **Zero-Elevation Installers (`scripts/setup-wizard.ps1`, `scripts/install.ps1`, `scripts/uninstall.ps1`, `setup.cmd`):** Clean graphical and console installers into `%LOCALAPPDATA%\Programs\<ProjectName>`.
- **Inno Setup Script (`scripts/installer.iss`):** Ready-to-compile native Windows installer script.
- **GitHub Actions CI/CD (`.github/workflows/`):** Automated PR/push verification in `ci.yml` and tag-triggered GitHub Releases in `release.yml`.

---

## 📂 Repository Tour

```text
├── .agents/                        # 🆕 Workspace-scoped agent skills & rules (zero global token cost)
│   ├── config/
│   │   ├── model-default.toml      # Active repository default model routing policy
│   │   └── model-stats.json        # Quantitative runtime metrics & token economics database
│   ├── skills/
│   │   ├── model-optimizer/SKILL.md # Autonomous monitoring & dynamic model routing optimizer
│   │   ├── project-qa/SKILL.md     # Workspace skill for running autonomous UI & accessibility QA
│   │   └── skill-manager/SKILL.md  # Workspace skill for scoping, promoting & demoting agent skills
│   └── rules/
│       └── README.md               # Guide to creating project-isolated agent rules
├── .github/
│   ├── assets/
│   │   └── hero-banner.svg         # Crisp vector architecture and social hero banner
│   ├── ISSUE_TEMPLATE/
│   │   ├── agent_task.yml          # Form template for delegating tasks to Copilot / subagents
│   │   ├── agent_task.md           # Markdown template fallback for agent task issues
│   │   ├── bug_report.yml          # Structured bug report with QA test IDs
│   │   ├── feature_request.yml     # Feature requests tied to MoSCoW priorities
│   │   └── qa_verification.yml     # Empirical manual / hardware QA verification report
│   ├── workflows/
│   │   ├── ci.yml                  # Automated PR & push verification gate with matrix tasks
│   │   └── release.yml             # Tag-triggered GitHub Releases and asset publishing
│   ├── copilot-instructions.md     # Binding instructions for GitHub Copilot (Agent & IDE)
│   └── pull_request_template.md    # PR template enforcing verification gate checks & Draft PR rules
├── docs/
│   ├── decisions/
│   │   └── 0000-template.md        # Architecture Decision Record (ADR) skeleton
│   ├── 01-vision.md                # Vision, problem statement, principles, non-goals
│   ├── 02-requirements.md          # MoSCoW functional requirements & NFR budgets
│   ├── 03-architecture.md          # Component diagrams, tech stack, disjoint modules
│   ├── 04-ux.md                    # Interaction flows, screens, and accessibility
│   ├── 05-roadmap.md               # Sized milestone task board with parallel markers (⇉)
│   ├── 06-qa-and-validation.md     # Empirical validation matrix & budget measurements
│   ├── 07-ux-and-improvements.md   # UX backlog, setup wizard, responsive refactor
│   ├── 08-community-and-growth-strategy.md # WinGet, Scoop, and community expansion strategy
│   ├── m0-spike-findings.md        # Ground truth from Milestone 0 diagnostic spikes
│   ├── multi-agent-methodology.md  # Detailed Antigravity + Copilot collaboration guide
│   ├── user-guide.md               # End-user documentation and troubleshooting FAQ
│   ├── lessons-learned.md          # Living log of friction points and rules adopted
│   ├── model-fallback-log.md       # Audit trail for downgraded agent runs
│   ├── model-optimization-report.md # Living audit log for automated model routing tuning
│   ├── skill-scope.md              # Local vs Global skill scoping & token economics guide
│   ├── release-methodology.md      # SemVer, version source of truth, and release checklist
│   ├── retrospective.md            # Milestone retrospective and token economics template
│   └── README.md                   # Comprehensive guide to the documentation system
├── scripts/
│   ├── apply-model-optimisation.ps1 # Evaluates model performance and tunes default routing
│   ├── collect-model-stats.ps1     # Scans execution logs and computes model statistics
│   ├── generate-manifests.ps1      # WinGet & Scoop manifest generator
│   ├── install.ps1                 # Zero-elevation user-level installer
│   ├── installer.iss               # Inno Setup native Windows installer template
│   ├── manage-skill.ps1            # Scaffolds, lists, promotes, and demotes skills (Local vs Global)
│   ├── manage-worktree.ps1         # Automates isolated Git worktrees for parallel agent tasks
│   ├── package-release.ps1         # Automated release bundler & SHA-256 calculator
│   ├── run-parallel-agents.ps1     # Multi-agent parallel task orchestrator across worktrees
│   ├── run-qa.ps1                  # Autonomous UI crawl launcher using ui-qa-tester
│   ├── setup-wizard.ps1            # Graphical & console guided Windows setup wizard
│   ├── start-model-optimiser.ps1   # Continuous background daemon for model optimization
│   ├── uninstall.ps1               # Clean application and shortcut uninstaller
│   └── verify-gate.ps1             # Tiered verification gate runner (Fast incremental vs Full)
├── setup.cmd                       # Double-clickable Windows setup launcher
├── qa-session.template.toml        # Automated UI & accessibility crawl configuration for ui-qa-tester
├── .gitignore                      # Multi-stack git ignore rules (Rust, Node, Python)
├── AGENTS.md                       # Binding operational rules and verification gate
├── CHANGELOG.md                    # Chronological milestone changelog
├── CODE_OF_CONDUCT.md              # Contributor Covenant v2.1 code of conduct
├── CONTRIBUTING.md                 # Contribution, branching, and multi-agent pair programming guide
├── LICENSE                         # MIT License
├── SECURITY.md                     # Security policy, memory/platform guarantees, vulnerability reporting
├── SUPPORT.md                      # Community support channels, quick docs links, FAQ
└── README.md                       # Repository overview and onboarding
```

---

## 🚦 Getting Started

### Method A: Using as a GitHub Template (Recommended)
1. Click **"Use this template"** > **"Create a new repository"** on GitHub.
2. Clone your new repository locally:
   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   cd <your-repo-name>
   ```
3. Open the repository in your favorite AI-enabled environment (Antigravity, Cursor, VS Code, etc.).
4. Run the Project Kickstart discovery flow:
   - In Antigravity: Run the `/project-kickstart` skill or prompt:
     > *"Initialize project definition using the templates in this repository."*
   - In other assistants: Prompt the agent to interview you following the sections in `docs/01-vision.md` through `05-roadmap.md`.
5. Review and approve the generated specifications.
6. Begin implementing Milestone 0 (Spikes) and Milestone 1 (Skeleton)!

### Method B: Manual Configuration
1. Fill in [`AGENTS.md`](AGENTS.md) with your project mission, critical complexity areas, verification gate commands, and hard rules.
2. Replace the `{{...}}` placeholders in `docs/01-vision.md` through `docs/05-roadmap.md`.
3. Set up your verification gate command in [`AGENTS.md`](AGENTS.md#6-task-lifecycle) (e.g., `cargo test`, `npm test`, `pytest`).
4. Commit your initial project specification.

---

## 🔄 The Milestone Lifecycle

Every project built with this template progresses through 8 structured milestones:

```text
M0: Spikes (🔬)           De-risk unknowns with disposable diagnostic probes; record in m0-spike-findings.md.
M1: Skeleton              Establish module structure, CI pipeline, and verification gate.
M2: Core Logic            Implement deterministic domain logic (100% unit-tested).
M3: Integrations          Connect OS APIs, persistence, networking, and external services.
M4: User Interface        Build UI views, entry points, and state management.
M5: Hardening & QA        Measure NFR budgets, conduct edge-case, soak, and crowdsourced QA testing.
M6: Packaging & Release   Build binaries/artifacts with scripts/, publish GitHub Releases & package manifests.
M7: Retrospective         Review lessons learned in retrospective.md and promote generic rules to toolkits.
```

---

## 🛡️ Operating Rules for AI Agents

All AI assistants working on this repository must read and adhere to [`AGENTS.md`](AGENTS.md):
1. **Always read documents in mandatory order:** Vision -> Requirements -> Architecture -> UX -> Roadmap -> QA -> Spikes -> UX Backlog -> Community -> Methodology -> Decisions -> Lessons Learned.
2. **Work on one roadmap task at a time:** Check off items in [`docs/05-roadmap.md`](docs/05-roadmap.md) with date and commit hash only after passing the verification gate.
3. **Run the Verification Gate:** Every change must satisfy the verification gate commands before being considered complete.
4. **Environment Resiliency:** Never assume standard toolchains are in `$PATH`; explicitly configure environment variables.
5. **Cross-Platform Hygiene:** Use UTF-8 encoding without BOM, avoid unconstrained recursive file searches over dependency caches (`node_modules`, `target`, `.venv`), and do not commit build artifacts.

---

## 📄 License

This template is licensed under the [MIT License](LICENSE). Feel free to use, adapt, and distribute it for personal and commercial projects.
