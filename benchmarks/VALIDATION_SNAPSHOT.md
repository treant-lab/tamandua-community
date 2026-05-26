# Validation Snapshot

Status: public curated snapshot  
Snapshot date: 2026-05-26

This page summarizes the validation state without publishing raw run archives.

## Highlights

| Area | Public status | Evidence summary |
| --- | --- | --- |
| Windows P0 segmented deterministic pass | Pass | Latest segmented P0 batches show `10/10`, `11/11`, and `7/7` passing coverage in generated scorecards. |
| Atomic upstream smoke | Pass | `windows-atomic-upstream-smoke` latest public-safe summary reports `8/8` passing coverage. |
| CALDERA smoke | Pass, repeatability still tracked | `windows-caldera-smoke` latest summary reports `5/5`; repeatability gates still matter before broad claims. |
| False-positive regression noise | Seed pass | Latest false-positive regression profile reports `1/1` passing in the curated scorecard. |
| Detection rule metadata | Clean for high/critical review gate | Generated metadata report scanned `540` rules, including `357` high/critical rules, with `0` high/critical rules needing review. |
| CALDERA enterprise-safe expansion | In progress | Enterprise-safe runs are active and should be described as hardening work, not complete coverage. |
| Linux/macOS sensor smoke | Not complete | Public roadmap scorecard still marks cross-platform sensor smoke as failing or incomplete. |
| Response validation | Not complete | Response and investigation proof remains an open validation area. |

## Public Claim Boundary

It is fair to say:

- Tamandua has a repeatable validation harness.
- Tamandua tracks telemetry observed separately from detections generated.
- Tamandua has passing Windows P0 segmented validation evidence.
- Tamandua has passing smoke evidence for selected Atomic and CALDERA profiles.
- Tamandua tracks false-positive regression and detection metadata quality.

Do not overstate:

- complete CALDERA enterprise coverage;
- full cross-platform parity;
- production release hardening;
- full response workflow proof;
- complete absence of false positives.

## Next Public Evidence Targets

1. Publish a redacted public evidence package for selected passing profiles.
2. Add a repeatability note for CALDERA smoke.
3. Add cross-platform sensor smoke examples once Linux/macOS evidence is server-backed.
4. Publish response validation only after rollback and audit evidence are clear.
