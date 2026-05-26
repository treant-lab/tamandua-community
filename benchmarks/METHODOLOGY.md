# Benchmark Methodology

Tamandua benchmark summaries distinguish evidence quality from marketing claims.

## Core Terms

| Term | Meaning |
| --- | --- |
| Telemetry observed | The agent or server received events relevant to the scenario. |
| Detection generated | A rule or analysis path produced a detection or alert. |
| Investigable evidence | The alert includes enough context for an analyst to understand what happened. |
| Partial | Some expected evidence was present, but fields, alerts, source quality, or storyline context were incomplete. |
| Missed | Required telemetry, detection, or alert evidence was absent. |
| Execution failed | The scenario runner failed before evidence quality could be assessed. |

## What a Passing Result Means

A passing profile means the selected quality gate passed for that profile and run. It does not automatically imply:

- complete product coverage;
- production hardening;
- absence of false positives;
- all upstream Atomic Red Team or CALDERA scenarios are proven;
- support for every OS, kernel, browser, or deployment mode.

## Evidence Expected

Good public benchmark summaries include:

- profile name;
- scenario source;
- platform;
- version or commit;
- expected telemetry;
- observed telemetry;
- detections generated;
- alert evidence quality;
- false-positive notes;
- known gaps.

## What We Do Not Publish by Default

Raw run JSON and logs are not published in this repository by default because they can contain:

- hostnames;
- internal lab identifiers;
- command output;
- environment details;
- excessive endpoint telemetry;
- large files unsuitable for a community coordination repository.

When raw artifacts are useful, they should be redacted and published through the validation repository, release assets, or a dedicated evidence store.
