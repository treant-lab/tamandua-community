# Tamandua Community Setup

Tamandua's public community should use Discord for real-time discussion and GitHub Discussions for searchable technical knowledge.

Permanent invite: https://discord.gg/52Duv5GVDF

## Primary Channels

- **Discord**: public chat, onboarding, demos, support triage, contributor coordination, and hackathon updates.
- **GitHub Discussions**: durable Q&A, design discussions, roadmap proposals, detection-rule ideas, and benchmark interpretation.
- **GitHub Issues**: confirmed bugs, actionable engineering tasks, and security-safe feature requests.
- **Security email**: vulnerability reports and sensitive disclosure only.

Do not use Discord as the source of truth for bugs, security reports, benchmark results, or architectural decisions. Move durable decisions back to GitHub.

## Discord Server Structure

Create these categories and channels first:

### Start Here

- `#announcements`: releases, validation results, public demos, major roadmap updates.
- `#welcome`: short intro, project links, contribution paths.
- `#rules`: community rules and security disclosure reminder.
- `#getting-started`: install, local lab, first validation run.

### Product

- `#support`: general help and environment issues.
- `#benchmarks`: detection validation runs, Atomic Red Team, CALDERA, reproducibility.
- `#detections-and-rules`: Sigma/YARA/rule ideas, false positives, ATT&CK coverage.
- `#threat-intel`: IOC enrichment, feeds, Abuse.ch, provider setup.
- `#live-response`: isolation, quarantine, rollback, command queue, response safety.

### Web3 Security

- `#solana-security`: signer workstations, validator/RPC host protection, proof metadata.
- `#web3-ops`: exchange, custody, protocol, treasury, and developer-machine security workflows.

### Contributors

- `#contributors`: first PRs, repo setup, coordination.
- `#roadmap`: public product direction and requests.
- `#showcase`: demos, screenshots, lab runs, integrations.

### Private/Moderator

- `#mod-log`: moderation notes.
- `#triage`: maintainer-only issue/support triage.
- `#partners`: optional private channel for pilots and integrations.

Avoid creating too many channels at launch. Add enterprise/private Slack later only for customer-specific support.

## Discord Launch Checklist

- Create server named `Tamandua`.
- Add icon and short description: `Self-hosted EDR/XDR for Web3 and security teams.`
- Enable community features and safety screening.
- Create the channels above.
- Pin project links in `#welcome`:
  - Repository
  - README
  - Detection Validation docs
  - Open Source Roadmap
  - Public Alpha Validation Checklist
  - Security policy
- Post the current validation snapshot in `#benchmarks`.
- Post the contribution paths in `#contributors`.
- Permanent invite link: https://discord.gg/52Duv5GVDF.

Most channel creation can be automated after the server exists:

```powershell
$env:DISCORD_BOT_TOKEN = "..."
$env:DISCORD_GUILD_ID = "123456789012345678"
python scripts/community/setup_discord_community.py --post-starter-messages
```

Discord server creation itself is manual; Discord bots can manage channels inside an existing server, not create the server for you.

## GitHub Discussions Setup

Enable Discussions in repository settings and create these categories:

- `Announcements`
- `Q&A`
- `Ideas`
- `Show and Tell`
- `Benchmarks`
- `Detections and Rules`
- `Web3 Security`
- `Contributors`

Use Discussions for anything that should be searchable or referenced later.

Repository labels and a launch checklist issue can be automated:

```powershell
$env:GITHUB_TOKEN = "ghp_..."
$env:GITHUB_REPO = "owner/repo"
python scripts/community/setup_github_community.py --create-tracking-issue
```

The script attempts to enable Discussions through the GitHub repository API. If the token lacks administration permission, enable Discussions manually in repository settings and rerun the script for labels/issues.

## Moderation Rules

- No malware samples, credential dumps, private keys, access tokens, or exploit payloads in public channels.
- Share only safe reproduction steps and sanitized logs.
- Vulnerabilities go through the security disclosure path, not public chat.
- Keep benchmark claims tied to reproducible artifacts.
- Move confirmed bugs to GitHub Issues.

## First Public Posts

Use these as initial messages:

### `#welcome`

Tamandua is a self-hosted EDR/XDR focused on endpoint evidence, response workflows, detection validation, and privacy-safe proof metadata for Web3/security teams.

Start with the README, then try the detection validation docs. Use `#getting-started` for setup help and `#benchmarks` for validation results.

### `#benchmarks`

We publish benchmark artifacts showing what Tamandua saw, what it missed, and whether the alert evidence is usable. Current Windows validation focuses on safe ATT&CK-style tests, with Atomic Red Team and CALDERA integration paths being hardened.

### `#detections-and-rules`

Use this channel for detection ideas, Sigma/YARA mapping, false-positive notes, and ATT&CK coverage gaps. Please include event examples, expected behavior, and why the rule should or should not alert.
