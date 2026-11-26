# Overview Dashboard CRM v11 source save

The shared CRM v11 library now handles the validated invoice-date case population, exact case detail and the exact CustomerID route for the default CRM connection. Existing case count, invoice bounds, detail enrichment, customer fallback and cache publication logic are preserved.

The read-only MT API Tests run for 2026-10-01 through 2026-10-15 matched all 1,310 case records on the audited fields, 2,934 product lines, case detail, customer metadata, and detail enrichment counts. The paired readers took 19.47 seconds on legacy and 14.79 seconds on v11. v11 used two case requests versus fifteen on legacy.

The catalog test surfaced a response difference. The existing unfiltered product request returned no rows while the filtered v11 request returned 2,360. This release preserves the existing catalog request and its existing dashboard fallback behavior.

The synchronized source carries forward all 96 files from the newer editor baseline. The existing live web URL continues serving version 52 by Summer's decision. No dashboard cache or workbook refresh ran, and no BigQuery query was submitted.

[Passing read-only comparison source](https://github.com/summer871/mt-api-tests-crm-api/commit/ebcde3e621252aa613d7edf72343a1ad1fd892eb)
