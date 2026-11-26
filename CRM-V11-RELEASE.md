# Overview Dashboard CRM v11 source save

The shared CRM v11 library now handles the validated invoice-date case population, exact case detail and the exact CustomerID route for the default CRM connection. Existing case count, invoice bounds, detail enrichment, customer fallback and cache publication logic are preserved.

The read-only MT API Tests run for 2026-10-01 through 2026-10-15 matched all 1,310 case records on the audited fields, 2,934 product lines, case detail, customer metadata, and detail enrichment counts. The paired readers took 19.47 seconds on legacy and 14.79 seconds on v11. v11 used two case requests versus fifteen on legacy.

The catalog test surfaced a response difference. The existing unfiltered product request returned no rows while the filtered v11 request returned 2,360. This release preserves the existing catalog request and its existing dashboard fallback behavior.

The synchronized source carries forward all 96 files from the newer editor baseline. The existing live web URL continues serving version 52 by Summer's decision. No dashboard cache or workbook refresh ran, and no BigQuery query was submitted.

[Passing read-only comparison source](https://github.com/summer871/mt-api-tests-crm-api/commit/ebcde3e621252aa613d7edf72343a1ad1fd892eb)

## Cache follow-up

The current Apps Script HEAD and GitHub source include the v6.683 memory fix. The live cache refresh completed in 6m 14s, validated all 2,730 November CRM cases, and published a browser cache with 135,403 rows. The public web app still serves version 52. [Memory fix](https://github.com/summer871/overview-dashboard-crm-api/commit/e5247353d1eb97767d91590cac84f3a0d1e354db) · [Current CRM rollout audit](https://github.com/summer871/magictouch-crm-client/blob/55408fa30ad1f6c6c3c4609408aaa2db8adac858/docs/consumer-rollout-audit.md)
