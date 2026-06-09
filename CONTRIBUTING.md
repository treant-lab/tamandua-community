# Contributing to Tamandua

Thank you for your interest in contributing to Tamandua! This guide will help you get started.

## Code of Conduct

Please read and follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## Development Setup

### Prerequisites

- Docker & Docker Compose
- Elixir 1.15+ (backend)
- Rust 1.74+ (agent)
- Python 3.11+ (ML service)
- Node.js 20+ (dashboard assets)

### Quick Setup

```bash
# Clone the repository
git clone https://github.com/treant-lab/tamandua.git
cd tamandua

# Start infrastructure (PostgreSQL, Redis, RabbitMQ)
make dev-up

# Setup each component
make backend-setup   # Elixir dependencies + database
make agent-setup     # Rust dependencies
make ml-setup        # Python dependencies
```

### Running Services

```bash
# Terminal 1: Backend
make backend-run

# Terminal 2: ML Service (optional)
make ml-run

# Terminal 3: Agent
make agent-run
```

Dashboard is available at http://localhost:4000

### Running Tests

```bash
make test           # All tests
make backend-test   # Elixir tests only
make agent-test     # Rust tests only
make ml-test        # Python tests only
```

## Project Structure

```
tamandua/
├── apps/
│   ├── tamandua_server/      # Elixir/Phoenix backend
│   ├── tamandua_agent/       # Rust endpoint agent
│   └── tamandua_ml/          # Python ML service
├── docs/                     # Internal documentation
├── deploy/                   # Deployment configs
└── tests/                    # Integration tests
```

## Making Changes

### Branch Naming

- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation updates
- `refactor/` - Code refactoring

### Commit Messages

Follow conventional commits:

```
feat(agent): add DNS collector for Windows
fix(server): handle nil agent_id in telemetry
docs(readme): update quick start instructions
```

### Pull Requests

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run tests: `make test`
5. Run linters: `make lint`
6. Submit a pull request

### PR Checklist

- [ ] Tests pass (`make test`)
- [ ] Linters pass (`make lint`)
- [ ] Documentation updated if needed
- [ ] Changelog entry added for user-facing changes

## Component-Specific Guides

### Backend (Elixir)

```bash
cd apps/tamandua_server
mix deps.get
mix ecto.setup
mix phx.server
```

Key directories:
- `lib/tamandua_server/` - Business logic
- `lib/tamandua_server_web/` - Web layer, LiveView
- `test/` - ExUnit tests

### Agent (Rust)

```bash
cd apps/tamandua_agent
cargo build
cargo test
```

Key directories:
- `src/collectors/` - Telemetry collectors
- `src/transport/` - WebSocket communication
- `src/response/` - Command execution

### ML Service (Python)

```bash
cd apps/tamandua_ml
uv sync  # or pip install -r requirements.txt
pytest
```

Key directories:
- `malware_smell/` - ML model implementation
- `api/` - FastAPI endpoints
- `tests/` - pytest tests

## Getting Help

- Discord - real-time chat, onboarding, demos, and support triage. See [docs/community/COMMUNITY.md](docs/community/COMMUNITY.md) for the channel map and launch checklist.
- [GitHub Discussions](https://github.com/treant-lab/tamandua/discussions) - Q&A, benchmark interpretation, detection ideas, roadmap proposals, and contributor coordination.
- [GitHub Issues](https://github.com/treant-lab/tamandua/issues) - confirmed bugs and actionable engineering tasks.
- [SECURITY.md](SECURITY.md) - vulnerability reports and sensitive disclosure.

Do not post private keys, credentials, live malware samples, exploit payloads, or sensitive customer logs in public channels.

## Open Source Roadmap

Tamandua is planned as an open-core, staged open-source project. Start with
[docs/community/OPEN_SOURCE_ROADMAP.md](docs/community/OPEN_SOURCE_ROADMAP.md)
before proposing broad features or security-sensitive changes.

For scoped contribution paths, see
[docs/community/CONTRIBUTION_TRACKS.md](docs/community/CONTRIBUTION_TRACKS.md).
For starter tasks, see
[docs/community/GOOD_FIRST_ISSUES.md](docs/community/GOOD_FIRST_ISSUES.md).

Useful contribution tracks include:

- detection engineering: Sigma/YARA, severity, MITRE mapping, suppressions, tests;
- endpoint telemetry: process, parent, command line, user, hash, DNS/network, registry, file context;
- benchmark lab: safe Atomic/CALDERA profiles, benign workloads, validation reports;
- analyst UX: alert evidence, storylines, empty states, provenance, and false-positive clarity;
- infrastructure: self-hosted deployment, health checks, rollback, and config examples.

Security-sensitive areas such as signed updates, live response, driver/kernel code,
agent credentials, and marketplace/bounty mechanics require extra review and
validation evidence.

## License

By contributing, you agree that your contributions will be licensed under Apache 2.0.
