---
name: Detection Proposal
about: Propose or improve a Sigma/YARA rule, IOC bundle, or detection pack
title: '[DETECTION] '
labels: detection, needs-repro, community
assignees: ''
---

## Summary

What behavior should Tamandua detect?

## Detection Type

- [ ] Sigma rule
- [ ] YARA rule
- [ ] IOC bundle
- [ ] Detection pack
- [ ] Existing rule improvement

## Threat Context

- Technique or behavior:
- MITRE ATT&CK mapping, if known:
- Severity rationale:
- Target platform: Windows / Linux / both

## Required Telemetry

List the fields needed to make this detection reliable.

- Process:
- Parent process:
- Command line:
- File/path/hash:
- Registry:
- DNS/network:
- User/session:
- Other:

## Expected Detection Logic

Describe the condition that should alert. Avoid rules that rely only on a single string when richer context is available.

## Benign Cases and Suppressions

List known legitimate tools, admin workflows, developer workflows, or noisy environments that could match this logic.

## Reproduction Evidence

- Safe reproduction steps:
- Benchmark profile or test, if available:
- Sanitized event sample:

```json
{}
```

## Safety and Privacy Check

- [ ] No live malware sample is attached.
- [ ] No secrets, private keys, tokens, customer logs, or sensitive hostnames/IPs are included.
- [ ] The proposal distinguishes observed telemetry from generated detection output.
