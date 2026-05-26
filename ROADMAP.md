# Public Roadmap

Tamandua is opening in stages so the public project is useful without overstating what is production-ready.

## Goals

1. Make the community edition self-hostable, inspectable, and useful for endpoint validation.
2. Give contributors clear paths for detections, telemetry quality, benchmarks, docs, deployment, integrations, and analyst UX.
3. Keep sensitive release surfaces controlled: signed builds, update trust, live response, agent credentials, drivers, and supply-chain automation.
4. Separate current capability from roadmap work.
5. Build a contribution loop that rewards defensive value and low false-positive impact.

## Phase 0: Honest Public Surface

Focus:

- repository map;
- public contribution process;
- security disclosure;
- community channels;
- clear known boundaries;
- templates for useful issues and proposals.

Exit criteria:

- a new contributor can understand what Tamandua is, where to file work, and what not to post publicly in under 15 minutes.

## Phase 1: Community Validation Core

Focus:

- deterministic validation profiles;
- safe ATT&CK-style coverage;
- benchmark report format;
- telemetry observed versus detection generated;
- benign workload baselines;
- sanitized public examples.

Exit criteria:

- a contributor can run a safe benchmark and submit a useful issue or PR without private lab access.

## Phase 2: Contribution Intake

Accepted contribution types:

- Sigma and YARA rules;
- IOC bundles with source and expiry context;
- benchmark scenarios;
- hardening and configuration packs;
- response safety docs;
- deployment fixes;
- telemetry normalization improvements;
- evidence-quality UI improvements;
- connector and integration adapters.

Required review evidence:

- expected telemetry fields;
- benign cases;
- suspicious or malicious cases;
- severity rationale;
- safe reproduction plan;
- benchmark result or test where practical;
- false-positive risk.

## Phase 3: Agent and Response Hardening

Focus:

- signed and verifiable builds;
- crash recovery and backpressure behavior;
- response action audit trail;
- live response safety model;
- kill, quarantine, isolate, and rollback validation profiles;
- driver and eBPF health reporting;
- safe defaults for experimental collectors.

## Phase 4: Ecosystem and Bounty Pilot

Focus:

- contributor attribution;
- duplicate detection review;
- PII and sensitive telemetry checks;
- benchmark coverage scoring;
- false-positive tracking;
- optional reward workflows for validated defensive artifacts.

This phase should not incentivize noisy detections or unsafe reproduction.
