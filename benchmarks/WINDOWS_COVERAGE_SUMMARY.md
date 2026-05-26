# Windows Coverage Summary

Status: curated public summary  
Snapshot date: 2026-05-26

Windows validation is currently the strongest public evidence lane.

## Passing or Strong Evidence

| Profile group | Summary |
| --- | --- |
| Windows P0 segmented batches | Latest scorecard shows segmented P0 batches passing `10/10`, `11/11`, and `7/7`. |
| Windows roadmap 300 batches | Several deterministic batches show passing evidence, but freshness and restore provenance are tracked separately. |
| Atomic upstream smoke | Latest curated evidence shows `8/8` passing. |
| CALDERA smoke | Latest curated evidence shows `5/5` passing. |
| Existing benign baseline | Seed benign evidence is tracked, with regression work continuing. |

## Known Boundaries

- A pass in one profile does not prove every Windows collector, response action, or enterprise workflow.
- Some profiles use deterministic safe commands instead of full upstream execution.
- Fresh VM provenance and repeatability are separate gates.
- High-volume raw artifacts are not included here.

## Contributor Opportunities

- Add benign workload profiles.
- Improve public redaction workflow for evidence packages.
- Add reproducible setup notes for external contributors.
- Expand expected field documentation for each technique.
