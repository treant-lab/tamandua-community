---
name: False Positive Report
about: Report a benign workflow that Tamandua flagged incorrectly
title: '[FALSE POSITIVE] '
labels: false-positive, detection, needs-repro
assignees: ''
---

## Alert Summary

- Alert or rule name:
- Severity shown:
- Platform:
- Tamandua version or commit:

## Benign Workflow

Describe the legitimate activity that triggered the alert.

## Why This Should Not Alert

Explain whether this is expected admin activity, software update behavior, developer tooling, security tooling, or another benign case.

## Evidence

Paste sanitized evidence only.

```json
{}
```

## Environment

- OS and version:
- Deployment: local dev / lab / Docker / production-like
- Relevant software involved:
- Frequency: one-time / repeated / every run

## Suggested Suppression or Rule Change

If you have a suggestion, describe the field, condition, allowlist scope, or severity adjustment.

## Safety and Privacy Check

- [ ] Logs are sanitized.
- [ ] No credentials, tokens, private keys, or customer data are included.
- [ ] This report includes enough context for maintainers to reproduce or reason about the match.
