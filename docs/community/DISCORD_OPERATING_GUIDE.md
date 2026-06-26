# Tamandua Discord Operating Guide

Permanent invite: https://discord.gg/52Duv5GVDF

Discord is for fast coordination, support triage, benchmark discussion, demos, and contributor onboarding. GitHub Issues, Pull Requests, Discussions, and docs remain the durable source of truth.

## Positioning

Tamandua is a self-hosted EDR/XDR focused on endpoint evidence, detection validation, response workflows, and privacy-safe proof metadata for Web3 and security teams.

Short version:

> Private detection, public proof.

What the community should make clear:

- Current product focus is endpoint telemetry, detections, alerts, investigations, response, detection validation, and optional Solana proof metadata.
- Advanced areas such as broad CSPM, full DPI/NDR, mobile agents, public marketplace, and on-chain governance are roadmap items until validated.
- Security claims should be tied to reproducible artifacts, not screenshots alone.

## Channel Intent

### Start Here

- `#announcements`: official releases, validation snapshots, roadmap updates, and public demos.
- `#welcome`: entry point with project links, current status, and role guidance.
- `#rules`: community rules and safe-sharing boundaries.
- `#getting-started`: install help, local lab setup, agent enrollment, and first validation run.

### Product

- `#support`: general usage support and environment troubleshooting.
- `#benchmarks`: Atomic Red Team, CALDERA, validation artifacts, coverage gaps, and reproducibility.
- `#detections-and-rules`: Sigma/YARA ideas, false-positive analysis, ATT&CK mapping, and detection quality.
- `#threat-intel`: IOC enrichment, feeds, blocklists, Abuse.ch, local intel, and enrichment quality.
- `#live-response`: shell, isolation, quarantine, rollback, command queue, recording, and response safety.

### Web3 Security

- `#solana-security`: signer workstations, validator/RPC host protection, smart-contract execution nodes, and proof metadata.
- `#web3-ops`: custody, exchange, protocol, treasury, and developer-machine security operations.

### Contributors

- `#contributors`: first PRs, repo setup, implementation coordination, and engineering questions.
- `#roadmap`: product direction, planning, proposals, and milestone tradeoffs.
- `#showcase`: screenshots, demos, lab runs, dashboards, integrations, and public wins.

### Private Ops

- `#mod-log`: moderator notes.
- `#triage`: maintainer-only support and issue triage.
- `#partners`: private pilot, partner, and integration coordination.

## Roles

- `Member`: general community access.
- `Endpoint Operator`: agent, deployment, and operational usage.
- `Detection Engineer`: Sigma/YARA, false-positive analysis, ATT&CK mapping.
- `Benchmark Lab`: Atomic Red Team, CALDERA, validation artifacts.
- `Threat Intel`: IOC enrichment, feeds, and blocklist quality.
- `Live Response`: shell, isolation, quarantine, rollback, and audit trails.
- `Web3 Security`: Solana, signer workstations, validators, RPC nodes, and custody ops.
- `Core Contributor`: active implementation contributors.
- `Partner`: private pilot and integration coordination.
- `Moderator`: moderation and community triage.
- `Maintainer`: project maintainers.

## Pinned Texts

### `#welcome`

Welcome to Tamandua EDR.

Tamandua is a self-hosted EDR/XDR for endpoint evidence, detection validation, response workflows, and privacy-safe proof metadata for Web3/security teams.

Start here:

- README: project overview and local setup.
- Detection Validation docs: benchmark workflow and evidence quality.
- Roadmap Hub and current validation snapshot: honest status boundary.
- Security policy: vulnerability disclosure and safe reporting.
- `#getting-started`: install help and first agent enrollment.
- `#benchmarks`: reproducible validation artifacts.
- `#detections-and-rules`: detection quality and false-positive analysis.

Do not post secrets, private keys, customer telemetry, live malware samples, or exploit payloads.

### `#rules`

Community rules:

- No credentials, private keys, customer data, or live malware samples.
- Share sanitized logs and safe reproduction steps.
- Vulnerabilities go through `SECURITY.md`, not public chat.
- Benchmark claims need artifacts: commands, profile, agent/server version, telemetry observed, alerts generated, and known gaps.
- Confirmed bugs should become GitHub Issues.
- Design decisions and roadmap commitments should move to GitHub Discussions or docs.

### `#benchmarks`

Benchmark format:

- Environment: OS, agent version, driver/eBPF status, server version.
- Scenario: Atomic/CALDERA/manual profile and technique IDs.
- Expected telemetry: process, command line, parent, file, registry, DNS/network, user, hash.
- Observed telemetry: what arrived and what was missing.
- Detection result: alert ID, severity, MITRE, evidence, storyline quality.
- False positives: unexpected high/critical alerts and benign workload notes.
- Artifacts: report JSON, screenshots only as supporting evidence, logs when sanitized.

Passing a benchmark means more than seeing an event. It should produce investigable evidence and a clear alert or explain why it intentionally did not alert.

### `#detections-and-rules`

Detection proposal format:

- Technique or behavior.
- Required telemetry fields.
- Rule logic in plain language.
- Expected benign cases and suppressions.
- Expected malicious cases.
- Severity rationale.
- Test plan with safe reproduction.
- False-positive risk.

Avoid string-only detections when richer evidence is available. Prefer behavior, parent/child context, path trust, signature/hash, user context, network context, and time-window correlation.

### `#roadmap`

Roadmap principle:

Tamandua should earn claims through validation. We prioritize reliable telemetry, evidence quality, response safety, and reproducible benchmarks before expanding claims.

Near-term priorities:

1. Endpoint telemetry quality: process, command line, parent, user, file, registry, DNS/network, hash, driver/eBPF health.
2. Detection quality: fewer string-only shortcuts, better correlation, clear severity, and lower false positives.
3. Storyline quality: attack chains that analysts can read, not only isolated rule hits.
4. Response validation: kill, quarantine, isolate, live response, audit trail, rollback, and safety gates.
5. Benchmark maturity: deterministic safe profiles plus upstream-backed Atomic Red Team and CALDERA runs.
6. Web3 operator coverage: signer workstations, developer machines, RPC/validator hosts, custody workflows, and proof metadata.
7. Community contribution loop: rules, IOCs, hardening packs, playbooks, benchmark profiles, review, and safe attribution.

Roadmap-only until validated:

- broad CSPM;
- full NDR/DPI;
- mobile endpoint agents;
- public marketplace;
- on-chain reputation/governance;
- automatic blocking from untrusted intel feeds.

## Roadmap Governance

Use `#roadmap` for lightweight discussion. Move durable proposals to GitHub Discussions or docs when they include:

- a clear user or operator problem;
- current behavior;
- desired behavior;
- telemetry required;
- security and false-positive risks;
- implementation scope;
- validation plan.

## Moderation Workflow

1. Keep `#support` and `#getting-started` friendly but evidence-oriented.
2. Move confirmed defects into GitHub Issues.
3. Move roadmap/design proposals into GitHub Discussions.
4. Move sensitive security issues into the disclosure path.
5. Use `#triage` for maintainer notes when a support thread needs private coordination.
