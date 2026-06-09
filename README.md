# Tamandua Community

Community, governance, and contribution hub for the [Tamandua EDR](https://github.com/treant-lab)
project — a hybrid, OSS-led EDR with a Rust agent, an Elixir/Phoenix backend, and
a Python ML service.

This repository is **documentation and process only**. It holds the canonical
contribution guidelines, code of conduct, security policy, issue/discussion
templates, and community programs. There is no code to build here.

## Where the code lives

Tamandua is developed in a monorepo and mirrored to standalone component repos
under the [`treant-lab`](https://github.com/treant-lab) organization:

| Repo | Component |
| --- | --- |
| [`tamandua-agent`](https://github.com/treant-lab/tamandua-agent) | Rust endpoint agent |
| [`tamandua-server`](https://github.com/treant-lab/tamandua-server) | Elixir/Phoenix backend (bundles the rustler NIF) |
| [`tamandua-ml`](https://github.com/treant-lab/tamandua-ml) | Python/FastAPI ML service |
| [`tamandua-core`](https://github.com/treant-lab/tamandua-core) | Embeddable Rust core library |
| [`tamandua-ctl`](https://github.com/treant-lab/tamandua-ctl) | Command-line control tool |
| [`tamandua-gui`](https://github.com/treant-lab/tamandua-gui) | Tauri desktop GUI |
| [`tamandua-browser-extension`](https://github.com/treant-lab/tamandua-browser-extension) | Browser extension |
| [`tamandua-detection-validation`](https://github.com/treant-lab/tamandua-detection-validation) | Detection validation probes & scorecards |

Build, test, and run instructions are component-specific and live in each repo's
own `README.md`. Per-component build steps below refer to the monorepo layout.

## Start here

- **Code of Conduct** — [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md)
- **Contributing** — [`CONTRIBUTING.md`](CONTRIBUTING.md)
- **Security policy** — [`SECURITY.md`](SECURITY.md)
- **Acknowledgements** — [`ACKNOWLEDGEMENTS.md`](ACKNOWLEDGEMENTS.md)

## Community programs

- [Community overview](docs/community/COMMUNITY.md)
- [Contribution tracks](docs/community/CONTRIBUTION_TRACKS.md) — code, detection rules, benchmarks, docs
- [Good first issues](docs/community/GOOD_FIRST_ISSUES.md)
- [Open-source roadmap](docs/community/OPEN_SOURCE_ROADMAP.md)
- [Discord operating guide](docs/community/DISCORD_OPERATING_GUIDE.md)
- [Donate / support](docs/community/DONATE.md)

## License

Project code is licensed under Apache-2.0 (see each component repo). Documentation
in this repository is provided under the same terms unless noted otherwise.
