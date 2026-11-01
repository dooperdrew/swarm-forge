# Model Fallback Log

Every time an autonomous subagent or worker task runs on a lower-tier or alternate model than its assigned tier required (due to quota limits, rate limiting, or API unavailability), it is recorded here.

This ensures complete transparency and prevents cognitive or safety regressions from slipping into production unnoticed.

---

## Active Fallback Routing Hierarchy

When the primary requested model tier is unreachable, Antigravity gracefully falls back along this deterministic route:

$$\text{inherit} \longrightarrow \text{pro} \longrightarrow \text{flash} \longrightarrow \text{flash\_lite}$$

All fallback events are continuously ingested by `scripts/collect-model-stats.ps1` and analyzed by `scripts/apply-model-optimisation.ps1` to tune default repository routing policies in `.agents/config/model-default.toml`.

---

## Fallback Audit Table

| Date | Task ID | Target Model | Fallback Used | Reason | Audit Status | Auditor Notes |
|---|---|---|---|---|---|---|
| — | — | — | — | — | N/A | Baseline initialized. No fallbacks recorded. |

---

## Mandatory Audit Workflow

1. **Automatic Detection:** Any fallback event is noted in the task completion report and appended to this table.
2. **Roadmap Tracking:** A corresponding review item is automatically flagged for the **Milestone 5 (Hardening)** audit pass (`docs/05-roadmap.md` Task M5.3).
3. **High-Reasoning Verification:** A higher-tier model (`pro` or human pair programmer) reviews the generated code for edge cases, performance budgets, and security invariants.
4. **Resolution:** Once verified, update the **Audit Status** to `AUDITED & PASSED` or `REFACTORED` with git commit reference.
