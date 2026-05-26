# Benchmarks

Use this directory for lightweight benchmark interpretation and public-safe examples.

Large generated artifacts should live in the validation repository, release assets, or a dedicated evidence store, not in this community repository.

Good benchmark notes include:

- profile name;
- platform;
- exact version or commit;
- expected telemetry;
- observed telemetry;
- detections generated;
- misses, partial coverage, or false positives;
- sanitized artifacts or reproduction notes.

## Public Docs

- [Validation Snapshot](VALIDATION_SNAPSHOT.md)
- [Methodology](METHODOLOGY.md)
- [Windows Coverage Summary](WINDOWS_COVERAGE_SUMMARY.md)
- [False Positive Regression](FALSE_POSITIVE_REGRESSION.md)
- [CALDERA Enterprise Safe Status](CALDERA_ENTERPRISE_SAFE_STATUS.md)
- [Detection Rule Metadata](DETECTION_RULE_METADATA.md)

## Publication Rule

Publish summaries before raw artifacts. Raw JSON run outputs can contain lab identifiers, host details, command output, or excessive telemetry volume. Keep public evidence minimal, reproducible, and sanitized.
