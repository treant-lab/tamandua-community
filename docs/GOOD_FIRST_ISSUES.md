# Good First Issues

This list gives new contributors realistic starter tasks. These are issue ideas, not guarantees that a matching issue already exists.

## Detection Engineering

1. Add MITRE ATT&CK metadata to one existing or proposed rule.
2. Document benign suppressions for a noisy admin or developer workflow.
3. Convert one detection idea from a discussion into a Detection Proposal issue.
4. Add expected telemetry requirements to a rule proposal.

Useful evidence:

- rule name;
- technique mapping;
- severity rationale;
- false-positive note;
- sanitized event example where possible.

## Endpoint Telemetry

1. Inventory missing process context for a safe local command.
2. Report a parent/child process mismatch.
3. Check whether DNS or network events use stable field names.
4. Add collector health expectations to a telemetry gap report.

Useful evidence:

- platform and version;
- reproduction command;
- observed event;
- expected fields;
- sanitized JSON.

## Benchmark Lab

1. Run one safe benchmark profile and submit a Benchmark Result issue.
2. Draft a benign workload profile for common workstation activity.
3. Convert a custom fallback command into an upstream Atomic Red Team reference where possible.
4. Improve report wording that confuses telemetry observed with detection generated.

Useful evidence:

- profile name;
- exact commit or version;
- OS and environment notes;
- telemetry observed;
- detections generated;
- misses and false positives.

## UX and Analyst Experience

1. Identify an alert view where evidence wraps poorly or hides important fields.
2. Report an empty state that implies data is live when it is missing or historical.
3. Improve storyline readability notes for missing telemetry.
4. File a false-positive clarity issue for an alert that lacks context.

Useful evidence:

- screenshot with sanitized data;
- viewport size;
- page or route;
- expected behavior.

## Infrastructure and Deployment

1. Verify a local Docker Compose setup step and report stale commands.
2. Add a health-check expectation to deployment docs.
3. Document rollback for a local lab setup change.
4. Clarify an environment variable example that could be misread as a real secret.

Useful evidence:

- OS;
- Docker or tool version;
- command run;
- result;
- suggested doc fix.

## Response Safety

1. Review one response workflow for missing audit fields.
2. Report a response action that lacks rollback guidance.
3. Document a safe validation profile for isolate, quarantine, kill process, or rollback.
4. Identify UI or logs that do not distinguish requested, queued, executed, failed, and rolled back states.

Useful evidence:

- action type;
- lab-only reproduction;
- expected audit fields;
- rollback path;
- blast radius.
