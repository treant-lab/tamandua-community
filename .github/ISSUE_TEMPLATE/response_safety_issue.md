---
name: Response Safety Issue
about: Report a safety, auditability, rollback, or authorization concern in response workflows
title: '[RESPONSE SAFETY] '
labels: response, security-review, needs-repro
assignees: ''
---

## Safety Concern

Describe the response action, workflow, or policy behavior that may be unsafe.

## Response Surface

- Action type: isolate / quarantine / kill process / rollback / command / other
- Platform:
- Tamandua version or commit:
- Deployment: local dev / lab / production-like

## Expected Safe Behavior

What guardrail, audit event, confirmation, RBAC check, rollback path, or failure behavior did you expect?

## Observed Behavior

What happened instead?

## Reproduction Steps

Use a lab-safe reproduction only.

1. 
2. 
3. 

## Evidence

Paste sanitized logs, screenshots, or audit events.

```text

```

## Risk Assessment

- Blast radius:
- Data loss risk:
- Availability risk:
- Privilege or authorization concern:
- Suggested severity:

## Safety and Privacy Check

- [ ] No exploit payload, credential, private key, or customer-sensitive log is included.
- [ ] Reproduction steps are lab-safe.
- [ ] This is not a vulnerability disclosure requiring private reporting through SECURITY.md.
