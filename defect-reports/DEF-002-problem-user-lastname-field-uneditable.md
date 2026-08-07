# Defect Report

| Field | Detail |
|---|---|
| **Defect ID** | DEF-002 |
| **Title** | "Last Name" field at checkout does not accept keyboard input for `problem_user` |
| **Reported By** | Iroshan Baktharaja |
| **Date Reported** | 2026-08-08 |
| **Related Test Case(s)** | TC-06 |
| **Application / Module** | SauceDemo — Checkout Step One (`/checkout-step-one.html`) |
| **Environment** | Chrome 126, macOS, https://www.saucedemo.com/ |
| **Severity** | High |
| **Priority** | P1 |
| **Status** | New (known/intentional SauceDemo demo bug — logged here as a documentation sample) |

## Summary

When logged in as `problem_user`, the "Last Name" input field on the checkout information
step cannot be typed into. Clicking the field and typing produces no visible text, which
blocks completion of checkout entirely for this account.

## Steps to Reproduce

1. Go to https://www.saucedemo.com/ and log in as `problem_user` / `secret_sauce`
2. Add any product to the cart
3. Click the cart icon, then click "Checkout"
4. On the checkout information page, click into the "Last Name" field
5. Type a value, e.g. "Baktharaja"

## Expected Result

The typed text appears in the "Last Name" field, matching the behavior of the "First
Name" and "Zip/Postal Code" fields on the same form.

## Actual Result

The field remains empty regardless of typed input. Clicking "Continue" then triggers the
form's required-field validation error ("Error: Last Name is required"), blocking checkout
completion.

## Evidence

- Screen recording of the checkout-step-one form showing keystrokes not registering in
  the Last Name field specifically, while First Name and Zip Code accept input normally
- Browser console shows no JavaScript errors at the time of the failed input — this
  points to a field-specific event handler issue rather than a page-level script crash
- (In a real report: attach the screen recording and a console log export here)

## Impact

This is a **checkout-blocking** defect for the affected account — the user cannot
complete a purchase at all, since the field is required and cannot be filled. In a real
production context this would be a Critical/P1 revenue-blocking bug; kept at High/P1
here since it's scoped to a single test account on a demo site rather than all users.

## Additional Notes

This is one of SauceDemo's intentionally-seeded bugs, isolated to `problem_user` — the
same flow completes successfully under `standard_user`. Useful example of a defect where
severity (High — blocks a core flow) and priority (P1 — no workaround exists for the
affected account) both need to be justified independently rather than assumed to match.
