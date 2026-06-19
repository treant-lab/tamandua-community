# Tamandua Open Source Roadmap

Status: active / public operating model
Last updated: 2026-06-19

This roadmap explains how Tamandua is being operated as an open-source security project without pretending every internal or experimental feature is production-ready.

The principle is simple:

> Keep the public code inspectable and contribution-friendly. Gate privileged response, update, driver, and supply-chain surfaces with extra review.

## Current Public Repositories

- `treant-lab/tamandua-community` - public governance, contribution, and community docs hub.
- `treant-lab/tamandua-agent` - endpoint agent mirror.
- `treant-lab/tamandua-server` - server, console, API, response, and attestation mirror.
- `treant-lab/tamandua-core` - reusable core library mirror.
- `treant-lab/tamandua-ctl` - CLI mirror.
- `treant-lab/tamandua-gui` - desktop GUI mirror.
- `treant-lab/tamandua-browser-extension` - browser extension mirror.
- `treant-lab/tamandua-detection-validation` - validation harness, schemas, and scorecard mirror.
- `treant-lab/tamandua-community` - governance, contribution, and community docs mirror.
- `tamandua-ml` is intentionally held until experimental model artifacts and public claim boundaries are ready.

## Goals

1. Make the community edition self-hostable, inspectable, and useful for real endpoint validation.
2. Give contributors clear paths to improve detections, telemetry quality, benchmarks, docs, deployment, and integrations.
3. Keep security-sensitive release surfaces controlled: signed builds, update trust, live response, agent credentials, and kernel/driver changes.
4. Separate current product claims from aspirational roadmap items.
5. Build a contribution loop that rewards defensive value, reproducible evidence, and low false-positive impact.

## Open-Core Boundary

### Community Core

The community core should include:

- self-hosted server baseline;
- endpoint agent baseline;
- GUI/dashboard baseline;
- enrollment and mTLS identity model;
- persisted Event History;
- real Agent Status based on heartbeat/socket state;
- alerts, investigations, and storyline views;
- base response actions with safety gates;
- base Sigma/YARA rules;
- detection validation runner and benchmark profiles;
- local IOC/threat-intel enrichment;
- optional Solana proof metadata;
- docs, deployment recipes, and reproducible validation artifacts.

### Commercial / Managed Surface

The commercial or managed layer may include:

- hosted control plane;
- managed retention, backups, monitoring, and upgrades;
- premium support and onboarding;
- premium threat feeds and curated rule packs;
- enterprise RBAC/SSO/compliance exports;
- managed benchmark/validation projects;
- private marketplace/review workflows;
- paid pilot integrations;
- SLA-backed response workflows.

### Hold Until Security Review

Do not publish casually:

- update signing infrastructure;
- private signing keys or deployment secrets;
- cloud production automation;
- billing/licensing internals;
- privileged live-response policy internals without RBAC/audit review;
- kernel/driver modules that lack fuzzing, signing, and rollback guidance;
- marketplace moderation antifraud logic that could be gamed;
- proprietary feeds or partner data.

## Release Phases

### Phase 0: Honest Public Surface

Goal: keep the public repos navigable and avoid overclaiming.

Deliverables:

- current product boundary documented;
- community hub and component mirrors published;
- known production gaps visible;
- Discord and GitHub contribution paths clear;
- public invite published;
- issue/discussion templates aligned with benchmark and detection quality;
- docs identify roadmap-only features.

Exit criteria:

- a new contributor can understand what is real, what is experimental, and where to help in under 15 minutes.

### Phase 1: Community Validation Core

Goal: make community testing reproducible.

Deliverables:

- deterministic detection validation profiles;
- Windows safe ATT&CK coverage baseline;
- Linux safe ATT&CK coverage baseline;
- benchmark report format with telemetry, alert, false-positive, and storyline scoring;
- clear "telemetry observed" versus "detection generated" distinction;
- documented benign workload baseline;
- public benchmark examples.

Exit criteria:

- a contributor can run a benchmark and submit a useful issue or PR without private lab access.

### Phase 2: Contribution Intake

Goal: accept useful defensive artifacts safely.

Accepted contribution types:

- Sigma/YARA rules;
- IOC bundles;
- detection packs;
- benchmark scenarios;
- hardening/config packs;
- response playbooks;
- docs and deployment fixes;
- telemetry normalization improvements;
- UI/UX evidence-quality improvements;
- connector/integration adapters.

Required contribution evidence:

- expected telemetry fields;
- benign cases and suppressions;
- malicious/suspicious cases;
- severity rationale;
- safe reproduction plan;
- benchmark result or unit/integration test;
- false-positive risk.

Exit criteria:

- submitted detections and benchmark profiles can be reviewed consistently.

### Phase 3: Agent and Response Hardening

Goal: make endpoint changes safer before broader adoption.

Deliverables:

- signed builds;
- documented build and verification path;
- crash recovery and backpressure behavior;
- response action audit trail;
- live response recording/encryption policy;
- kill/quarantine/isolate/rollback validation profiles;
- driver/eBPF health reporting;
- safe defaults for experimental collectors.

Exit criteria:

- response workflows are tested in lab environments and can fail closed with audit evidence.

### Phase 4: Ecosystem and Bounty Pilot

Goal: reward validated defensive value without incentivizing noisy detections.

Deliverables:

- contribution review states;
- duplicate detection;
- PII/sensitive telemetry checks;
- reviewer approval workflow;
- public-safe attribution;
- benchmark coverage scoring;
- false-positive tracking;
- optional bounty settlement workflow.

Exit criteria:

- a defensive artifact can be reviewed, validated, attributed, and optionally rewarded without exposing tenant telemetry.

## Contributor Tracks

### Detection Engineering

Best first issues:

- improve one rule with better telemetry requirements;
- add suppressions for a known benign case;
- add MITRE mapping and severity rationale;
- add a safe benchmark scenario.

Review bar:

- no string-only shortcut if better context is available;
- must include false-positive analysis;
- must distinguish telemetry from detection;
- must include test or benchmark evidence.

### Endpoint Telemetry

Best first issues:

- normalize process fields;
- improve parent/child context;
- add missing command line/path/user/hash fields;
- improve DNS/network field mapping;
- add collector health counters.

Review bar:

- bounded CPU/memory impact;
- privacy-aware field selection;
- stable schema aliases;
- regression tests where practical.

### Benchmark Lab

Best first issues:

- add safe Atomic-style profile;
- convert fallback command to upstream Atomic Red Team;
- add CALDERA profile documentation;
- add benign workload profile;
- improve report scoring.

Review bar:

- deterministic and safe;
- clear expected telemetry;
- no destructive action by default;
- artifacts are reproducible.

### UX / Analyst Experience

Best first issues:

- improve alert evidence wrapping;
- improve empty states;
- clarify live versus historical data;
- improve storyline timeline readability;
- remove mock/fake UI claims.

Review bar:

- shows data provenance;
- no fake refresh/timers pretending live data;
- handles missing telemetry explicitly;
- works on narrow and wide screens.

### Infrastructure and Deployment

Best first issues:

- tighten Docker Compose docs;
- add health checks;
- improve config examples;
- document upgrade/rollback;
- simplify local lab setup.

Review bar:

- no secrets committed;
- clear defaults;
- reproducible commands;
- rollback path documented.

## Labels

Recommended labels:

- `good first issue`
- `help wanted`
- `docs`
- `telemetry`
- `detection`
- `benchmark`
- `false-positive`
- `storyline`
- `response`
- `agent`
- `driver`
- `server`
- `frontend`
- `security-review`
- `needs-repro`
- `roadmap`
- `community`

## Issue Templates

Recommended public issue types:

- Bug report;
- Detection/rule proposal;
- False-positive report;
- Benchmark result;
- Telemetry gap;
- Response safety issue;
- Documentation improvement;
- Feature proposal.

## Discussion Categories

Recommended GitHub Discussions categories:

- Announcements;
- Q&A;
- Ideas;
- Benchmarks;
- Detections and Rules;
- Web3 Security;
- Contributors;
- Show and Tell.

## Public Roadmap Themes

### Now

- honest docs and claim boundary;
- Discord/community setup;
- deterministic benchmark harness;
- telemetry quality improvements;
- alert evidence and storyline quality;
- false-positive reduction;
- safe response validation.

### Next

- upstream-backed Atomic Red Team runs;
- CALDERA campaign validation;
- benign workload baselines;
- signed release pipeline;
- contribution review workflow;
- first community rule/benchmark packs;
- public examples of privacy-safe proofs.

### Later

- marketplace and bounty pilot;
- curated premium packs;
- broader infrastructure sensors;
- stronger driver/eBPF coverage;
- enterprise support paths;
- on-chain reputation/governance only after antifraud and legal review.

## Public Messaging

Use:

- "advanced alpha";
- "open-core staged release";
- "self-hosted community edition";
- "private endpoint telemetry, inspectable evidence, optional public proof";
- "benchmarks and detections are tied to reproducible artifacts."

Avoid:

- "fully open source today";
- "production-ready replacement for CrowdStrike";
- "trustless EDR";
- "fully autonomous AI SOC";
- "complete NDR/DPI";
- "automatic blocking from all threat feeds."

## Discord to GitHub Flow

1. Discuss quickly in Discord.
2. If actionable, create an issue or discussion.
3. Link artifacts: logs, report JSON, sanitized screenshots, profile, versions.
4. Review with the right label.
5. Merge only after validation appropriate to risk.
6. Post a short summary back to Discord.

## Maintenance Cadence

- Weekly: review support and benchmark threads for issues.
- Weekly: tag good first issues.
- Biweekly: publish validation snapshot.
- Monthly: update known gaps and roadmap state.
- Before each release: run secret scan, dependency audit, benchmark smoke, and docs check.
