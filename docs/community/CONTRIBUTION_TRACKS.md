# Tamandua Contribution Tracks

Status: public contributor guide
Last updated: 2026-05-19

Tamandua accepts community work when it improves defensive value, reproducibility, and analyst trust without expanding unsafe response or release surfaces casually. Start with the [Open Source Roadmap](OPEN_SOURCE_ROADMAP.md) for the staged release boundary.

## Contribution Principles

- Tie detection claims to reproducible telemetry or benchmark evidence.
- Distinguish "telemetry observed" from "detection generated."
- Prefer safe lab scenarios over live malware, exploit payloads, or customer logs.
- Include false-positive analysis for detection changes.
- Keep privacy and operational risk visible when adding telemetry.
- Expect extra review for response, driver, credential, update, signing, and marketplace surfaces.

## Detection Engineering

Good work in this track improves rules, suppressions, ATT&CK mapping, severity, and evidence quality.

Typical contributions:

- Sigma or YARA rules.
- IOC bundles with source and expiry context.
- Detection pack metadata.
- Suppressions for known benign cases.
- Severity and MITRE ATT&CK rationale.
- Safe benchmark scenarios that prove the rule behavior.

Review expectations:

- Include expected telemetry fields.
- Explain malicious or suspicious behavior.
- List benign cases and false-positive risk.
- Avoid single-string rules when better context is available.
- Include a benchmark result, unit test, or sanitized event sample where practical.

Use the Detection Proposal or False Positive Report issue templates when ready.

## Endpoint Telemetry

Good work in this track makes endpoint events complete, stable, and usable for detections, benchmarks, and investigations.

Typical contributions:

- Process identity normalization.
- Parent/child process context.
- Command line, path, user, and hash fields.
- DNS and network field mapping.
- Registry and file context.
- Collector health counters.
- Schema aliases and backwards-compatible field names.

Review expectations:

- Explain why each field is needed.
- Keep privacy impact bounded.
- Consider CPU, memory, and event volume.
- Preserve stable schema semantics.
- Include regression coverage where practical.

Use the Telemetry Gap issue template for missing or ambiguous data.

## Benchmark Lab

Good work in this track makes validation repeatable for contributors without private lab access.

Typical contributions:

- Safe Atomic-style profiles.
- Upstream Atomic Red Team conversions.
- CALDERA campaign documentation.
- Benign workload baselines.
- Report scoring improvements.
- Public examples with sanitized artifacts.

Review expectations:

- Keep scenarios deterministic and non-destructive by default.
- Document expected telemetry and expected detections separately.
- Include exact versions, commands, and environment notes.
- Avoid requiring private infrastructure.
- Sanitize artifacts before posting publicly.

Use the Benchmark Result issue template for completed runs and the Benchmarks discussion template for interpretation.

## UX and Analyst Experience

Good work in this track improves how analysts understand evidence, timelines, gaps, and provenance.

Typical contributions:

- Alert evidence layout and wrapping.
- Empty states that do not overclaim.
- Live versus historical data clarity.
- Storyline timeline readability.
- Missing telemetry states.
- False-positive explanation and triage affordances.

Review expectations:

- Show data provenance.
- Avoid fake live indicators or mock claims.
- Handle missing or partial telemetry explicitly.
- Keep narrow and wide screen behavior usable.

Open a feature request or discussion before broad UX changes.

## Infrastructure and Deployment

Good work in this track makes self-hosted use easier and safer.

Typical contributions:

- Docker Compose documentation.
- Health checks.
- Configuration examples.
- Local lab setup.
- Upgrade and rollback notes.
- Dependency or environment troubleshooting.

Review expectations:

- Do not commit secrets.
- Use reproducible commands.
- Document safe defaults.
- Include rollback or cleanup guidance when changing deployment behavior.

## Response Safety

Response workflows require higher scrutiny because mistakes can affect availability, data integrity, or endpoint control.

Typical contributions:

- Audit event clarity.
- Confirmation and authorization checks.
- Rollback documentation.
- Lab validation profiles.
- Safer failure states.

Review expectations:

- Use lab-safe reproduction only.
- Identify blast radius and failure mode.
- Include auditability expectations.
- Expect security review before merge.

Use the Response Safety Issue template for unsafe behavior, missing auditability, or rollback concerns.

## Where to Start

See [Good First Issues](GOOD_FIRST_ISSUES.md) for scoped starter tasks by track. Use GitHub Discussions for ideas that are not ready for an actionable issue, and GitHub Issues for reproducible work with enough evidence to review.
