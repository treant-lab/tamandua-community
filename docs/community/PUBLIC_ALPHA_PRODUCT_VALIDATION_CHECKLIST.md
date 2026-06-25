# Tamandua Public Alpha Product Validation Checklist

Status: pre-release validation gate
Owner: product validation
Scope: docs-only checklist for deciding whether Tamandua can be called a Public Alpha product
Last updated: 2026-06-25

This checklist defines the minimum validation evidence required before calling
Tamandua a Public Alpha product. A feature is not product-ready because code
exists, a route renders once, or an older benchmark was green. It is
product-ready only when the current lab/server evidence proves the user-visible
workflow, operational safety, and audit trail.

## Non-Negotiable Safety Rules

- Do not reboot the local Windows workstation used by the operator.
- Do not run aggressive, destructive, persistence, reboot, driver-stress,
  malware-like, or long-running load tests on the local Windows workstation.
- Aggressive or broad endpoint validation runs only on the isolated
  `win-template` lab VM or another explicitly approved disposable lab host.
- Server validation must target the lab/server at `192.168.12.146` unless a
  newer release owner documents a different release target in the evidence.
- Local commands for this checklist must be read-only or docs-only unless an
  operator explicitly switches to an isolated lab runbook.
- If a test can affect endpoint stability, security controls, firewall rules,
  DNS routing, agent config, response actions, scheduled scans, or system
  services, it must run in the lab and must produce a rollback note.
- Do not promote a validation pass if the evidence omits commit SHA, target
  host, environment, timestamp, request IDs, or affected alert/event IDs.

## Release Decision Rule

Public Alpha is allowed only when all P0 gates below are `pass` or have an
explicit `accepted-alpha-gap` entry with owner, rationale, user-facing impact,
and follow-up issue. A gap cannot be accepted when it affects authentication,
tenant isolation, agent config integrity, destructive response actions, or UI
routes that block first-use navigation.

## Evidence Packet Required For Every Gate

Each gate must link or attach a validation packet containing:

- `commit_sha`: exact Git commit validated.
- `validated_at`: timestamp with timezone.
- `validator`: person or agent identity.
- `target`: server URL/IP, endpoint hostname, agent ID, and tenant/org ID.
- `environment`: local, `win-template`, Linux lab, macOS lab, or server `146`.
- `commands_or_probe`: safe command, script, browser path, or API probe used.
- `request_ids`: HTTP request IDs, Phoenix request IDs, MCP request IDs, job
  IDs, or WebSocket correlation IDs where applicable.
- `alert_ids`: alert IDs produced or inspected.
- `event_ids`: event IDs, timeline event IDs, scan job IDs, detection result
  IDs, or audit event IDs.
- `screenshots_or_logs`: UI screenshots, structured JSON output, or server log
  excerpts sufficient to reproduce the claim.
- `result`: `pass`, `fail`, `blocked`, or `accepted-alpha-gap`.
- `claim_boundary`: exact wording that can be used publicly.

## P0 Gates

| Gate | Must Validate | Required Evidence |
|------|---------------|-------------------|
| Operational safety | Local Windows was not rebooted; aggressive tests did not run locally; aggressive runs, if any, were confined to `win-template`; rollback path exists. | Evidence packet names local host and `win-template`, includes command history/probe summary, and states no local reboot/aggressive execution occurred. |
| Lab/server 146 readiness | `192.168.12.146` serves the intended backend/frontend, current commit is deployed or explicitly mapped, auth works, health checks are green enough for alpha validation, and stale assets are not being tested by mistake. | Health/API/UI evidence with commit SHA, server URL, request IDs, asset/build identifier, and deployment note. |
| Primary navigation | Primary UI navigation pages load without HTTP 500, blocking JS errors, broken first paint, or auth loops. | Route list tested on server `146`, status code per route, request IDs for failures, screenshots for top-level pages. |
| Agent enrollment and health | At least one Windows lab agent and one non-Windows agent, where in scope for the alpha claim, enroll and report fresh heartbeat/health without false "ready" promotion. | Agent IDs, heartbeat timestamps, health payloads, event IDs, and explicit platform claim boundary. |
| DNS feed/history/blocklist/DoH bypass | DNS feed, DNS history, blocklist CRUD/import, detection display, and DoH/alternate-DNS bypass coverage are validated as visible product flows. | DNS query/event IDs, feed item IDs, blocklist entry IDs, request IDs, screenshots, and clear note on what DoH bypass is detected, blocked, or only warned. |
| MCP tools/schema | MCP tool listing, schema validation, request handling, auth/RBAC scope, reason capture, dry-run behavior, and audit output are proven for read-only and action-like tools. | MCP request IDs, schema validation output, audit event IDs, denied-call evidence, allowed-call evidence, and tenant/agent scope evidence. |
| Hyperautomation/workflows | Hyperautomation action catalog, workflow listing, workflow execution or dry-run, approval gates, and audit trail work without route crashes. | Workflow IDs, action IDs, approval/audit event IDs, request IDs, UI screenshots, and failure-mode evidence. |
| Alerts/timeline/storyline | Alerts are created or inspected with evidence, timeline entries, storyline graph/detail, MITRE/context fields, source-health clarity, and stable alert detail navigation. | Alert IDs, event IDs, storyline/timeline IDs, request IDs, screenshots, and missing-data states where telemetry is incomplete. |
| Scheduled scans | Scheduled scan creation, execution, result display, and history work for ML, ONNX, YARA, hash, and archive scanning where claimed. | Scan job IDs, schedule IDs, model/rule/hash/archive identifiers, result IDs, alert IDs if generated, and execution host. |
| Agent config protection | Agent config files, policy/config bundles, token material, and local AI/MCP/agentic config surfaces are protected or monitored according to the alpha claim. | Baseline config hash, attempted change event IDs, audit IDs, policy bundle ID, and explicit sensitive-content redaction note. |
| `AGENT_PROTECTION` alerts | Tamper/config-protection detections produce `AGENT_PROTECTION` or equivalent alert taxonomy with usable evidence and no silent failure. | Alert IDs, event IDs, config path or redacted hash, severity, source, request IDs, and response/audit trail. |
| Response and rollback safety | Any response action exposed in alpha is gated by RBAC, reason, scope, approval or explicit policy, audit, and rollback notes. | Response action IDs, request IDs, approval IDs, audit event IDs, target agent IDs, and rollback evidence. |
| Tenant/auth boundary | User, org, tenant, token, and API/MCP scopes prevent cross-tenant reads/actions and fail closed. | Positive and denied request IDs, user/org IDs, audit IDs, and redacted token/auth context. |
| Evidence exportability | Product evidence can be exported or copied into a validation packet without leaking secrets or raw sensitive content. | Export artifact path/hash, redaction note, request IDs, and reviewer sign-off. |

## Primary Navigation Minimum Route Set

The release validator must test the current primary nav, not an outdated route
list. At minimum, cover these areas if present in the deployed UI:

- Dashboard or overview.
- Agents and agent detail.
- Alerts and alert detail.
- Events, timeline, or investigation views.
- Storyline view.
- DNS, network, or threat-intel surfaces.
- Detection rules, scheduled scans, or validation surfaces.
- Hyperautomation, playbooks, workflows, or response actions.
- MCP servers/tools or AI/agentic security surfaces.
- Settings, users, tenants, and audit logs.

Each route must record HTTP status, client console errors, server request ID,
and whether the page is usable after refresh.

## DNS And Bypass Coverage

Validate the DNS story as a product workflow, not isolated API calls:

- Feed ingestion or feed refresh shows source, timestamp, and counts.
- DNS history can be filtered by domain, agent, time window, and verdict.
- Blocklist add/import/remove works and records actor, reason, and audit ID.
- A blocklisted domain produces expected event, alert, or policy result.
- DoH, DoT, alternate resolver, VPN/proxy, and direct-IP bypass limitations are
  explicit in the UI or documentation.
- Public wording distinguishes "detects or surfaces bypass indicators" from
  "prevents all encrypted DNS bypasses" unless enforcement evidence proves it.

## MCP And Agentic Action Coverage

Before any MCP or agentic workflow is called product-ready:

- Tool schemas validate with required fields, parameter types, and safe
  defaults.
- Missing auth, missing reason, invalid scope, cross-tenant target, and
  unauthorized action attempts are denied and audited.
- Read-only tools and action-like tools have distinct permissions.
- Destructive tools default to dry-run or approval unless a narrow autonomous
  policy explicitly allows execution.
- Every accepted call records caller identity, tenant/org, target agent/scope,
  reason, request ID, and audit event ID.

## Scheduled Scan Coverage

Scheduled scan validation must prove both scheduling and execution:

- ML scan: model/version is recorded, inference result is persisted, and false
  positive/unknown states are visible.
- ONNX scan: runtime/model metadata is recorded and errors are user-visible.
- YARA scan: rule ID/version and matched strings or redacted match metadata are
  persisted.
- Hash scan: hash algorithm, feed/source, and match/no-match result are shown.
- Archive scan: archive type, recursion/depth limits, encrypted archive
  handling, and extraction errors are visible.
- Results link back to alerts, events, evidence, or scan history.

## Agent Config Protection Coverage

The alpha claim must cover agent config protection honestly:

- Protected config locations are enumerated per platform in the evidence.
- Baseline hashes or signed bundle IDs are recorded.
- Unauthorized modification, deletion, downgrade, or token/config replacement
  produces an event and a visible alert.
- `AGENT_PROTECTION` alerts include severity, reason, affected path or redacted
  identifier, agent ID, and recommended next action.
- Sensitive file contents, secrets, tokens, prompts, and private MCP config
  values are redacted; hashes and metadata are preferred.

## Go/No-Go Template

Use this template in the final validation packet:

```text
Decision: go | no-go | go-with-accepted-alpha-gaps
Commit SHA:
Validated target:
Validated at:
Validator:
Local Windows safety statement:
Aggressive tests location:
Server 146 health:
Primary nav result:
Critical P0 failures:
Accepted alpha gaps:
Representative alert IDs:
Representative event IDs:
Representative request IDs:
Representative scan/job IDs:
Claim boundary approved:
```

## Automatic No-Go Conditions

- Local Windows workstation was rebooted or used for aggressive validation.
- Any primary navigation route needed for first-use alpha evaluation returns
  HTTP 500 without an accepted alpha gap.
- Server `192.168.12.146` is stale, unreachable, or not mapped to the commit
  being validated.
- Agent config tamper/config-protection silently fails when claimed.
- MCP/action-like tools allow cross-tenant or unaudited high-impact actions.
- DNS blocklist/feed claims cannot be tied to event IDs or request IDs.
- Scheduled scan claims cannot be tied to scan job IDs and result records.
- Alerts/timeline/storyline cannot be tied to alert IDs and event IDs.
- Evidence lacks commit SHA or target environment.

