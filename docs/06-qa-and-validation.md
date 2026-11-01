# 06 — QA & Validation

> Status: **LIVING QA MATRIX & TEST SPECIFICATION**  
> Rule: **Claims Follow Evidence.** A QA row is **Pass** only with empirical evidence (date, test log, tester, environment). Until then it stays **Pending**. Releases must explicitly list which rows remain Pending.

---

## 1. Verification Levels

1. **Automated Unit & Invariant Tests:** Executed by the verification gate on every change before commit.
2. **Automated Budget & Soak Tests:** Empirical measurements against NFR budgets (latency, idle CPU, memory footprint).
3. **Autonomous UI & A11y Crawl (`ui-qa-tester`):** Non-intrusive headless UI verification, accessibility audits (contrast, labels), and dead-button detection via `qa-session.toml`.
4. **Real-Environment QA:** End-to-end testing run on physical hardware, real OS environments, or live user accounts.
5. **System Edge Cases:** OS permissions, sleep/resume, abrupt termination, network loss, and upgrade migrations.

---

## 2. Autonomous UI & Accessibility QA (`ui-qa-tester`)

For applications with graphical user interfaces (Native Windows GUI or Web frontends), automated non-intrusive UI testing is configured via [`qa-session.template.toml`](../qa-session.template.toml):

```bash
# Copy template and launch automated UI crawl
cp qa-session.template.toml qa-session.toml
ui-qa-cli crawl --config qa-session.toml
```

- Reports and annotated step screenshots are exported to `qa-reports/`.
- Dead buttons (`UX-DEAD-BTN`), low contrast (`A11Y-LOW-CONTRAST`), and unhandled exceptions are flagged automatically.
- Community members and testers report findings using [`.github/ISSUE_TEMPLATE/qa_verification.yml`](../.github/ISSUE_TEMPLATE/qa_verification.yml).

---

## 3. Non-Functional Budget Results (NFRs)

| ID | Metric | Budget | Measured Output | Date / Commit | Measurement Method |
|---|---|---|---|---|---|
| NFR-P1 | Idle RAM Footprint | {{< 25 MB}} | Pending | | Task Manager / memory profiler |
| NFR-P2 | Idle CPU Usage | {{< 0.1%, event-driven}} | Pending | | Sysinternals Process Explorer |
| NFR-P3 | Execution Latency | {{< 0.5 ms}} | Pending | | High-resolution benchmark test |

---

## 4. Real-Environment Test Matrix

| Test ID | Area / Feature | Verification Procedure | Expected Outcome | Result | Date / Environment / Tester |
|---|---|---|---|---|---|
| QA-01 | First-run setup | Run installer or launch portable binary | UI opens without errors; config generated | Pending | |
| QA-02 | Core interaction | Execute primary feature workflow | State updates and persists cleanly | Pending | |
| QA-03 | UI navigation | Traverse all tabs, modals, and settings | Zero dead buttons; responsive layout | Pending | |
| QA-04 | Graceful exit | Exit application / terminate process | Background hooks and locks released | Pending | |

---

## 5. System Edge Cases & Invariant Regressions

| Test ID | Invariant Protected | Edge Procedure | Expected Behavior | Result |
|---|---|---|---|---|
| QA-SYS-01 | Single-instance lock | Launch second instance while first is running | Focuses existing window; avoids collision | Pending |
| QA-SYS-02 | Sleep / Resume | Put system to sleep while running | Resumes smoothly without restart | Pending |
| QA-SYS-03 | Corrupt config recovery | Launch with malformed config file | Recovers default config gracefully | Pending |

---

## 6. Incident & Discrepancy Protocol
Any discrepancy between documentation and actual behavior:
1. Stop immediately. Do not guess or silently hack around the issue.
2. Formulate a diagnostic probe and report empirical findings.
3. Open an issue labeled `bug` and add a regression test to prevent recurrence.
