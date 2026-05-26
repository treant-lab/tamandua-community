# Contribution Tracks

Tamandua accepts community work when it improves defensive value, reproducibility, and analyst trust without expanding unsafe surfaces casually.

## Detection Engineering

Typical work:

- Sigma or YARA rules.
- Detection pack metadata.
- MITRE ATT&CK mapping.
- Severity rationale.
- Suppressions for known benign behavior.
- False-positive analysis.
- Safe benchmark scenarios.

Review expectations:

- Include expected telemetry fields.
- Explain suspicious behavior and benign cases.
- Avoid single-string rules when better context exists.
- Include a benchmark result, test, or sanitized event sample where practical.

## Endpoint Telemetry

Typical work:

- Process identity normalization.
- Parent and child process context.
- Command line, path, user, hash, and signer fields.
- DNS and network mapping.
- Registry and file context.
- Collector health counters.
- Stable schema aliases.

Review expectations:

- Explain why each field is needed.
- Keep privacy impact bounded.
- Consider CPU, memory, and event volume.
- Preserve stable schema semantics.

## Benchmark Lab

Typical work:

- Safe Atomic-style profiles.
- CALDERA campaign documentation.
- Benign workload baselines.
- Report scoring improvements.
- Sanitized public examples.

Review expectations:

- Keep scenarios deterministic and non-destructive.
- Document expected telemetry and expected detections separately.
- Include versions, commands, and environment notes.
- Avoid requiring private infrastructure.

## UX and Analyst Experience

Typical work:

- Alert evidence layout.
- Storyline timeline readability.
- Missing telemetry states.
- False-positive explanation.
- Triage affordances.

Review expectations:

- Show data provenance.
- Avoid fake live indicators.
- Handle missing or partial telemetry explicitly.
- Keep narrow and wide screen behavior usable.

## Infrastructure and Deployment

Typical work:

- Docker Compose docs.
- Health checks.
- Configuration examples.
- Local lab setup.
- Upgrade and rollback notes.
- Troubleshooting.

Review expectations:

- Do not commit secrets.
- Use reproducible commands.
- Document safe defaults.
- Include rollback or cleanup guidance when changing deployment behavior.

## Response Safety

Typical work:

- Audit event clarity.
- Authorization checks.
- Rollback documentation.
- Lab validation profiles.
- Safer failure states.

Review expectations:

- Use lab-safe reproduction only.
- Identify blast radius and failure mode.
- Include auditability expectations.
- Expect security review before merge.
