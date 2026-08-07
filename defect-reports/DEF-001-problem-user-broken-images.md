# Defect Report

| Field | Detail |
|---|---|
| **Defect ID** | DEF-001 |
| **Title** | All product images render identically for `problem_user` |
| **Reported By** | Iroshan Baktharaja |
| **Date Reported** | 2026-08-08 |
| **Related Test Case(s)** | TC-04 |
| **Application / Module** | SauceDemo — Product Catalog (`/inventory.html`) |
| **Environment** | Chrome 126, macOS, https://www.saucedemo.com/ |
| **Severity** | Medium |
| **Priority** | P2 |
| **Status** | New (known/intentional SauceDemo demo bug — logged here as a documentation sample) |

## Summary

When logged in as `problem_user`, every product on the inventory page displays the same
image (a stock photo of a dog) instead of each product's actual image.

## Steps to Reproduce

1. Go to https://www.saucedemo.com/
2. Log in with username `problem_user` and password `secret_sauce`
3. Observe the product image for each of the 6 items on `/inventory.html`

## Expected Result

Each product displays its own distinct image (backpack, bike light, bolt t-shirt, etc.),
matching what `standard_user` sees.

## Actual Result

All 6 products display the identical placeholder image (a dog), regardless of the actual
product.

## Evidence

- `/inventory.html` screenshot while logged in as `problem_user` shows 6 identical images
- Compare against `/inventory.html` screenshot while logged in as `standard_user`, which
  shows 6 distinct images
- (In a real report: attach both screenshots side by side here)

## Impact

Users would be unable to visually distinguish products before purchasing, directly
undermining the core function of a shopping catalog. If this occurred on a production
storefront it would likely affect conversion and trust.

## Additional Notes

This is one of SauceDemo's intentionally-seeded bugs for testing practice, tied
specifically to the `problem_user` account — `standard_user` does not reproduce it. Included
here as a realistic, reproducible example of how to document a visual/data-binding defect,
including the "expected vs actual" and cross-account comparison that makes root cause
easy to scope (frontend image-binding logic vs. account-level data issue).
