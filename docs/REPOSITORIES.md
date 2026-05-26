# Repository Map

Tamandua uses a monorepo internally for integration work and public component repositories for focused collaboration and release surfaces.

## Public Component Repositories

| Repository | Owns |
| --- | --- |
| `tamandua-community` | Community process, roadmap proposals, RFCs, discussion templates, contribution onboarding. |
| `tamandua-server` | Server, API, web console, alerting, investigations, rules, and orchestration. |
| `tamandua-agent` | Endpoint collectors, transport, local response, platform telemetry, and agent runtime. |
| `tamandua-browser-extension` | Browser guard, web policy enforcement, extension packaging, and extension tests. |
| `tamandua-ctl` | CLI workflows for operators and automation. |
| `tamandua-core` | Shared contracts, data types, and cross-component utilities. |
| `tamandua-detection-validation` | Benchmark harnesses, safe profiles, fixtures, report generation, and validation docs. |
| `tamandua-gui` | Desktop GUI where it is developed and released separately. |

## Routing Rules

- File implementation bugs in the owning component repo.
- File cross-component design work here first.
- File security vulnerabilities through private disclosure.
- File benchmark interpretation here or in `tamandua-detection-validation`, depending on whether the action is discussion or implementation.
- File docs bugs where the docs live.

## Sync Model

The monorepo remains the integration source of truth. Component repositories should receive scoped updates through sync branches or pull requests. Changes made directly in a component repository should be brought back to the integration source before they are treated as canonical.
