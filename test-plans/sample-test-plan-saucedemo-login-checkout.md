# Test Plan: Login & Checkout Flow

## 1. Overview

| Field | Detail |
|---|---|
| **Feature/Module** | Login, Product Catalog, Checkout |
| **Application** | SauceDemo (https://www.saucedemo.com/) |
| **Author** | Iroshan Baktharaja |
| **Date** | 2026-08-08 |
| **Version/Build** | Public demo build (no version tag exposed) |

## 2. Objective

Verify that all six SauceDemo test accounts can authenticate correctly where expected,
that the product catalog displays and sorts correctly, and that the checkout flow
accepts valid input and rejects invalid input. This plan is designed to surface the
account-specific behavioral bugs SauceDemo intentionally ships for testing practice.

## 3. Scope

**In scope:**
- Login with all 6 documented test accounts (standard_user, locked_out_user,
  problem_user, performance_glitch_user, error_user, visual_user)
- Product listing display and sort functionality
- Add-to-cart and cart badge behavior
- Checkout form validation and completion

**Out of scope:**
- Payment gateway integration (SauceDemo has none — checkout is simulated)
- Cross-browser visual regression (covered separately in the Playwright suite)
- Performance/load testing beyond noting `performance_glitch_user`'s known delay

## 4. Test Environment

| Item | Detail |
|---|---|
| **URL / Build** | https://www.saucedemo.com/ |
| **Browsers/Devices** | Chrome 126 (primary), Firefox 128 (secondary) |
| **Test data / accounts** | standard_user, locked_out_user, problem_user, performance_glitch_user, error_user, visual_user — password `secret_sauce` for all |
| **Tools used** | Manual testing + Selenium/Playwright/Cypress automation, browser DevTools for network/console inspection |

## 5. Assumptions & Dependencies

- SauceDemo's test data and account behaviors are stable (site is maintained
  specifically as a testing sandbox and its known bugs are intentional/documented)
- No test data setup/teardown required — the site has no persistent user-created state

## 6. Test Scenarios & Cases

| Test Case ID | Title | Priority | Preconditions | Steps | Expected Result |
|---|---|---|---|---|---|
| TC-01 | Standard user logs in successfully | High | None | 1. Go to site 2. Enter `standard_user`/`secret_sauce` 3. Click Login | Redirected to `/inventory.html`, product list visible |
| TC-02 | Locked-out user is blocked | High | None | 1. Enter `locked_out_user`/`secret_sauce` 2. Click Login | Error message shown, stays on login page |
| TC-03 | Invalid password is rejected | High | None | 1. Enter `standard_user`/wrong password 2. Click Login | Error message: "Username and password do not match" |
| TC-04 | Product images render correctly per product | Medium | Logged in as `problem_user` | 1. Log in 2. Observe product images | Each product shows its own distinct image |
| TC-05 | Sorting by name (Z to A) reorders the list | Medium | Logged in as `problem_user` | 1. Log in 2. Select "Name (Z to A)" from sort dropdown | List re-orders with Z-first item on top |
| TC-06 | Last Name field accepts input at checkout | High | Logged in as `problem_user`, 1 item in cart | 1. Go to checkout step one 2. Click Last Name field 3. Type a value | Typed value appears in the field |
| TC-07 | Cart badge updates when item is added | High | Logged in as `standard_user` | 1. Log in 2. Click "Add to cart" on any item | Cart badge shows "1" |
| TC-08 | Checkout completes with valid shipping info | High | Logged in as `standard_user`, 1 item in cart | 1. Go to checkout 2. Fill all 3 fields with valid data 3. Continue 4. Finish | "Thank you for your order" confirmation shown |
| TC-09 | Checkout blocks submission with empty required field | Medium | Logged in as `standard_user`, 1 item in cart | 1. Go to checkout 2. Leave Postal Code blank 3. Click Continue | Error message shown, does not proceed to overview |

## 7. Entry / Exit Criteria

**Entry criteria:**
- Site is reachable and returns the login page
- Test accounts are documented and unchanged from SauceDemo's published list

**Exit criteria:**
- All test cases executed at least once
- All defects found are logged with severity and reproduction steps (see `/defect-reports`)
- No High-severity defect is left without a filed report

## 8. Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| SauceDemo changes its intentional bugs/test accounts without notice | Low | Medium | Re-verify this plan's scenarios before reusing it in a portfolio review |
| Manual testing misses timing-dependent bugs (e.g. `performance_glitch_user`) | Medium | Low | Cross-check manual findings against automated suite results |

## 9. Sign-off

| Role | Name | Date |
|---|---|---|
| QA | Iroshan Baktharaja | 2026-08-08 |
| Dev Lead | — (portfolio project, no dev team) | — |
