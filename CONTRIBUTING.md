# Contributing to Tamandua

Thanks for helping build Tamandua. This project values defensive usefulness, reproducible evidence, privacy, and clear review boundaries.

## Where Contributions Go

Use this repository for cross-project coordination:

- proposals and RFCs;
- detection ideas before they are ready for a component PR;
- benchmark interpretation;
- community process and documentation;
- issue templates and contributor onboarding.

Use component repositories for implementation work:

- `tamandua-server` for server, API, console, detections, alerting, and investigations;
- `tamandua-agent` for endpoint telemetry, transport, and local response;
- `tamandua-browser-extension` for browser security;
- `tamandua-ctl` for CLI workflows;
- `tamandua-core` for shared contracts;
- `tamandua-detection-validation` for validation harnesses and profiles;
- `tamandua-gui` for desktop GUI work.

## Contribution Principles

- Tie security claims to logs, code, artifacts, or reproducible steps.
- Distinguish telemetry observed from detection generated.
- Prefer safe lab scenarios over malware, exploit payloads, or customer logs.
- Include false-positive analysis for detection changes.
- Keep privacy and operational risk visible when adding telemetry.
- Expect extra review for response, credentials, updates, signing, drivers, and supply-chain surfaces.

## Before Opening an Issue

1. Search existing issues and discussions.
2. Choose the most specific template.
3. Sanitize logs, screenshots, command output, and hostnames.
4. Include platform, version or commit, environment, and reproduction steps.
5. Keep vulnerabilities and sensitive findings out of public issues.

## Pull Requests

For this repository, pull requests should usually be documentation, templates, proposals, or community process changes.

Checklist:

- The change has a clear owner or review path.
- Links point to public repositories or public docs.
- No secrets, customer data, internal hostnames, private lab credentials, or private incident details are included.
- Security-sensitive material belongs in the private disclosure flow, not public docs.
- Generated benchmark archives are not added here.

## Detection Contributions

Good detection proposals include:

- behavior or technique being detected;
- required telemetry fields;
- rule logic in plain language;
- malicious or suspicious cases;
- benign cases and false-positive risk;
- severity rationale;
- MITRE ATT&CK mapping where applicable;
- safe reproduction plan or benchmark artifact.

## Benchmark Contributions

Good benchmark reports include:

- profile or scenario name;
- OS, agent/server version, and relevant collector status;
- expected telemetry;
- observed telemetry;
- detections or alerts generated;
- missing fields, misses, partial coverage, or false positives;
- sanitized artifacts or exact reproduction notes.

## Response Safety

Response-related changes require careful review because they can affect endpoint availability, data integrity, or operator trust.

Include:

- blast radius;
- authorization and audit expectations;
- rollback path;
- failure mode;
- lab-safe reproduction;
- evidence that the UI/logs distinguish requested, queued, executed, failed, and rolled-back states.
