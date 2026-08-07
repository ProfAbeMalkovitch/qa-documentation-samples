# Defect Report

| Field | Detail |
|---|---|
| **Defect ID** | DEF-003 |
| **Title** | Product sort dropdown does not reorder items for `problem_user` |
| **Reported By** | Iroshan Baktharaja |
| **Date Reported** | 2026-08-08 |
| **Related Test Case(s)** | TC-05 |
| **Application / Module** | SauceDemo — Product Catalog sort control (`/inventory.html`) |
| **Environment** | Chrome 126, macOS, https://www.saucedemo.com/ |
| **Severity** | Low |
| **Priority** | P3 |
| **Status** | New (known/intentional SauceDemo demo bug — logged here as a documentation sample) |

## Summary

When logged in as `problem_user`, selecting "Name (Z to A)" or "Price (high to low)"
from the product sort dropdown does not change the on-screen order of products — the
list stays in its default order regardless of the selected sort option.

## Steps to Reproduce

1. Go to https://www.saucedemo.com/ and log in as `problem_user` / `secret_sauce`
2. On `/inventory.html`, note the default product order (top to bottom)
3. Open the sort dropdown (top-right of the product list)
4. Select "Name (Z to A)"
5. Observe the product order

## Expected Result

The product list re-orders alphabetically Z→A, with "Test.allTheThings() T-Shirt (Red)"
appearing first and "Sauce Labs Backpack" last.

## Actual Result

The product order is unchanged from the default view — the dropdown visually shows
"Name (Z to A)" as selected, but the underlying list order does not update.

## Evidence

- Screenshot of product order before selecting a sort option
- Screenshot of product order after selecting "Name (Z to A)" — orders are identical
- (In a real report: attach both screenshots here, ideally as a side-by-side diff)

## Impact

Low direct impact — users can still browse and purchase all products, and the bug is
cosmetic/functional rather than blocking. Still worth fixing since a non-functional
sort control undermines user trust in the UI, especially on a larger catalog where
sorting is more load-bearing for usability.

## Additional Notes

This is one of SauceDemo's intentionally-seeded bugs, isolated to `problem_user` —
`standard_user` sorts correctly under the same steps. Included as an example of a
lower-severity defect that's still worth documenting precisely, since "the dropdown
looks like it worked but didn't" is exactly the kind of bug that's easy to miss without
a specific before/after comparison step in the reproduction.
