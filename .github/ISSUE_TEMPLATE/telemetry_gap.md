---
name: Telemetry Gap
about: Report missing, incomplete, unstable, or ambiguous endpoint telemetry
title: '[TELEMETRY GAP] '
labels: telemetry, needs-repro, community
assignees: ''
---

## Gap Summary

What telemetry is missing, incomplete, unstable, or difficult to use?

## Platform and Collector

- OS and version:
- Collector or event source:
- Tamandua version or commit:
- Deployment: local dev / lab / Docker / production-like

## Expected Fields

List the fields needed for reliable detection, investigation, or benchmarking.

- Process:
- Parent process:
- Command line:
- Path/hash:
- User/session:
- DNS/network:
- Registry/file:
- Collector health:

## Observed Fields

Paste sanitized event examples or describe what is currently emitted.

```json
{}
```

## Why It Matters

Which detection, benchmark, storyline, or analyst workflow is blocked or degraded?

## Constraints

- Expected volume:
- Privacy concern:
- CPU/memory concern:
- Backward compatibility concern:

## Safety and Privacy Check

- [ ] Examples are sanitized.
- [ ] No customer-sensitive data, secrets, tokens, or private keys are included.
- [ ] This issue describes telemetry needs, not a request to collect unnecessary sensitive data.
