# Defect Log — Summary

Quick-reference index of all defects found during the [sample test plan](./test-plans/sample-test-plan-saucedemo-login-checkout.md).
Each row links to a full defect report with steps to reproduce, evidence, and impact.

| ID | Title | Severity | Priority | Status | Full Report |
|---|---|---|---|---|---|
| DEF-001 | All product images render identically for `problem_user` | Medium | P2 | New | [View](./defect-reports/DEF-001-problem-user-broken-images.md) |
| DEF-002 | "Last Name" field at checkout does not accept input for `problem_user` | High | P1 | New | [View](./defect-reports/DEF-002-problem-user-lastname-field-uneditable.md) |
| DEF-003 | Product sort dropdown does not reorder items for `problem_user` | Low | P3 | New | [View](./defect-reports/DEF-003-problem-user-sort-not-working.md) |

## Severity vs. Priority — quick definitions used in this log

| | Definition | Example from this log |
|---|---|---|
| **Severity** | How badly the defect breaks functionality, regardless of how many users hit it | DEF-002 is High severity — it fully blocks checkout completion |
| **Priority** | How urgently it should be fixed, considering scope/workarounds/business impact | DEF-002 is also P1 — no workaround exists for the affected account |

Severity and priority don't always match — a defect can be High severity but lower
priority if it's rare or has a workaround, or Low severity but high priority if it's
trivial to fix and highly visible. Each defect report justifies both independently
rather than assuming one implies the other.
