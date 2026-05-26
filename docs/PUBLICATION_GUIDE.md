# Publication Guide

Use this guide before adding public evidence, screenshots, logs, benchmark summaries, or community docs.

## Safe to Publish

- High-level methodology.
- Sanitized benchmark summaries.
- Aggregate counts.
- Public-safe detection ideas.
- Reproduction steps that are non-destructive.
- Links to component repositories.
- Community process and templates.

## Review Before Publishing

- Raw benchmark JSON.
- Command output.
- Hostnames and usernames.
- Internal IPs.
- VM IDs and lab topology.
- Screenshots with paths, names, or telemetry.
- Generated files over a few megabytes.

## Do Not Publish

- Credentials.
- Private keys.
- Tokens.
- Customer telemetry.
- Live malware samples.
- Exploit payloads.
- Private vulnerability details before coordinated disclosure.
- Signing or production deployment secrets.

## Benchmark Publication Rule

Prefer this order:

1. Curated summary.
2. Methodology.
3. Redacted markdown artifact.
4. Redacted JSON excerpt only if needed.
5. Full raw artifact only through an explicit evidence repository or release asset after review.
