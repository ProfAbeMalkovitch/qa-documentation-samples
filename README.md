# QA Documentation Samples — Test Plans & Defect Reports

A portfolio repo showing how I write test plans and log defects — the documentation
side of QA that doesn't show up in an automation framework repo, but is just as core to
the job. Most junior QA candidates only show code; this shows the thinking behind it.

## Why this exists

Automated test suites prove you can write code. This repo proves you can:
- Scope a test plan (in/out of scope, entry/exit criteria, risk assessment)
- Design test cases with clear preconditions, steps, and expected results
- Turn a found bug into a defect report someone else could reproduce without asking
  you a single follow-up question
- Distinguish severity (how badly it breaks things) from priority (how urgently to fix
  it) — and justify each independently, rather than assuming they always match

## What's inside

```
qa-documentation-samples/
├── test-plans/
│   ├── TEMPLATE-test-plan.md
│   └── sample-test-plan-saucedemo-login-checkout.md
├── defect-reports/
│   ├── TEMPLATE-defect-report.md
│   ├── DEF-001-problem-user-broken-images.md
│   ├── DEF-002-problem-user-lastname-field-uneditable.md
│   └── DEF-003-problem-user-sort-not-working.md
├── defect-log-summary.md
└── .github/ISSUE_TEMPLATE/bug_report.md
```

## The sample defects are real, reproducible bugs

All three sample defects were found on [SauceDemo](https://www.saucedemo.com/) — a
public site maintained specifically for testing practice, which intentionally seeds
bugs tied to its `problem_user` test account. They're genuinely reproducible today by
anyone (see steps in each report), not fabricated examples. This ties directly into my
[Selenium](https://github.com/ProfAbeMalkovitch/selenium-testng-framework),
[Playwright](https://github.com/ProfAbeMalkovitch/playwright-framework), and
[Cypress](https://github.com/ProfAbeMalkovitch/cypress-framework) automation repos,
which test the same site.

| Defect | Severity | Priority | What it shows |
|---|---|---|---|
| [DEF-001](./defect-reports/DEF-001-problem-user-broken-images.md) | Medium | P2 | Cross-account comparison to isolate a data-binding bug |
| [DEF-002](./defect-reports/DEF-002-problem-user-lastname-field-uneditable.md) | High | P1 | A checkout-blocking bug with no workaround — severity and priority both High |
| [DEF-003](./defect-reports/DEF-003-problem-user-sort-not-working.md) | Low | P3 | A "looks like it worked but didn't" bug that needs a precise before/after step |

See [`defect-log-summary.md`](./defect-log-summary.md) for the full index with a
severity-vs-priority explanation.

## Using the templates yourself

1. Copy `test-plans/TEMPLATE-test-plan.md` → rename per feature → fill in each section
2. Copy `defect-reports/TEMPLATE-defect-report.md` → rename `DEF-0XX-short-title.md` per bug
3. Link each defect back to the test case that found it (see the "Related Test Case(s)"
   field) so a reviewer can trace bug → test case → test plan in one click

The GitHub Issue template in `.github/ISSUE_TEMPLATE/bug_report.md` mirrors the same
format, in case a team files defects as GitHub Issues rather than standalone markdown.

## Next steps / ideas for extending this

- Add a defect report for a bug found via the automation suites themselves (tie a
  Selenium/Playwright/Cypress test failure directly to a filed defect)
- Add a lightweight RTM (Requirements Traceability Matrix) linking requirements → test
  cases → defects
- Convert `defect-log-summary.md` into a small sortable table using a static site
  generator, if this repo grows past a handful of defects
