# Good First Issues

Status: starter backlog
Last updated: 2026-05-19

This list gives new contributors realistic first tasks aligned with the [Open Source Roadmap](OPEN_SOURCE_ROADMAP.md) and [Contribution Tracks](CONTRIBUTION_TRACKS.md). These are starter issue ideas, not guarantees that a matching GitHub issue already exists.

When opening one, include the relevant template, expected evidence, and any safe reproduction steps.

## Detection Engineering

1. Add MITRE ATT&CK metadata to one existing rule or proposed rule.
   Evidence: rule name, technique mapping, severity rationale, and a short false-positive note.

2. Document benign suppressions for a noisy admin or developer workflow.
   Evidence: sanitized event sample, why it is benign, and the narrowest safe suppression scope.

3. Convert one detection idea from a discussion into a Detection Proposal issue.
   Evidence: required telemetry fields, expected logic, benign cases, and a safe reproduction plan.

4. Add expected telemetry requirements to a rule proposal.
   Evidence: process, parent, command line, user, file/hash, DNS/network, or registry fields needed.

## Endpoint Telemetry

1. Inventory missing process context for a safe local command.
   Evidence: expected fields, observed fields, OS version, and sanitized JSON.

2. Report a parent/child process mismatch or missing parent field.
   Evidence: reproduction command, observed event, expected parent process, and platform.

3. Check whether DNS or network events use stable field names.
   Evidence: event examples and proposed aliases if names are ambiguous.

4. Add collector health expectations to a telemetry gap report.
   Evidence: which counter would help, why it matters, and expected frequency.

## Benchmark Lab

1. Run one safe benchmark profile and submit a Benchmark Result issue.
   Evidence: profile name, platform, exact version or commit, telemetry observed, detections generated, misses, and false positives.

2. Draft a benign workload profile for common workstation activity.
   Evidence: commands or tools used, expected telemetry, and expected non-alert behavior.

3. Convert a custom fallback command into an upstream Atomic Red Team reference where possible.
   Evidence: upstream technique link, safety notes, and expected fields.

4. Improve a benchmark report with clearer "telemetry observed" versus "detection generated" sections.
   Evidence: before/after structure and one sanitized example.

## UX and Analyst Experience

1. Identify an alert view where evidence wraps poorly or hides important fields.
   Evidence: screenshot with sanitized data, viewport size, and expected behavior.

2. Report an empty state that implies data is live when it is historical or missing.
   Evidence: page, screenshot, data state, and corrected wording proposal.

3. Improve storyline readability notes for missing telemetry.
   Evidence: example timeline, missing event type, and analyst impact.

4. File a false-positive clarity issue for an alert that lacks enough context to triage.
   Evidence: alert name, missing fields, and what would make the decision easier.

## Infrastructure and Deployment

1. Verify a local Docker Compose setup step and report any stale command.
   Evidence: OS, Docker version, command run, result, and suggested doc fix.

2. Add a health-check expectation to deployment docs or an issue.
   Evidence: service, endpoint or command, healthy result, and failure signal.

3. Document a rollback step for a local lab setup change.
   Evidence: setup path, cleanup command, and data-loss warning if relevant.

4. Clarify an environment variable example that could be misread as a real secret.
   Evidence: file, current example, and safer placeholder.

## Response Safety

1. Review one response workflow for missing audit fields.
   Evidence: action type, expected audit fields, observed fields, and risk.

2. Report a response action that lacks clear rollback guidance.
   Evidence: action, lab-only reproduction, expected rollback path, and blast radius.

3. Document a safe validation profile for isolate, quarantine, kill process, or rollback.
   Evidence: non-production scope, expected result, audit expectations, and failure behavior.

4. Identify a response UI or log that does not distinguish requested, queued, executed, failed, and rolled-back states.
   Evidence: screenshot or sanitized log and the expected state model.

## Before Opening an Issue

- Search existing issues and discussions.
- Use the most specific issue template.
- Sanitize logs and screenshots.
- Include platform, version or commit, and reproduction steps.
- Keep security-sensitive vulnerabilities in the private disclosure path documented in `SECURITY.md`.
