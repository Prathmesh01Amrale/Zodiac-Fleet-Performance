# Fleet Performance Analytics — Stakeholder Summary

**To:** Head of Data Analytics  
**Subject:** Power BI prototype for fleet performance, maintenance exposure and reporting quality  
**Snapshot date:** 30 June 2026

## Purpose and approach

This prototype uses the supplied synthetic vessel, daily-operations, maintenance-order and inspection extracts to help a Fleet Performance Manager move from fleet-level monitoring to targeted investigation. The initial Fleet Overview brings together fuel consumed, CO₂ emissions, distance sailed, overdue work orders, downtime rate and reporting completeness. A monthly fuel trend provides historical context, while a vessel Attention Score offers a quick way to prioritise follow-up.

The source workbook was left unchanged. Power Query transformations were created in the PBIX to standardise identifiers and categories, convert types, and flag duplicates, orphan vessel IDs and implausible values. Rather than silently deleting suspicious records, the report keeps quality flags and uses metric-specific eligibility rules so a questionable fuel value does not automatically invalidate every other metric on the same row.

## Key decisions and caveats

The operational position is fixed at 30 June 2026 so the report remains reproducible. Maintenance is classed as overdue when it was not completed by that date and its valid due date is earlier than the snapshot date. Missing or invalid dates are not assumed to be overdue. Vessel IDs that do not match the vessel master are retained for investigation but excluded from vessel-attributed measures. Report rows explicitly labelled Missing are treated as untrusted for default operational totals even when values are populated. External vessels remain in the model and should be separated from Managed-vessel KPIs where required.

The Attention Score is an assumption-based triage aid, not a validated maritime safety rating. Likewise, the speed threshold, CO₂/fuel ratio tolerance and cost-outlier threshold are validation assumptions that should be reviewed with business stakeholders before the report is used operationally.

## Current status and next phase

The Fleet Overview page has been implemented with KPI cards, a monthly fuel trend, a vessel ranking and fleet/type/vessel/date slicers. The assessment brief also requests Vessel Detail, Maintenance Risk and Data Quality & Trust pages; these remain to be completed and tested if they are not present in the submitted PBIX. The next phase should complete those pages, verify date and slicer interactions, validate KPI denominators and maintenance date-role calculations, and conduct UAT with the intended business users. This would turn the current prototype into a more complete self-service reporting experience.
