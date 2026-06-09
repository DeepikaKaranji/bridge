# Smoot [WIP]

Welcome to **Smoot**, an open-source cross-chain interoperability framework under the [Linux Foundation Decentralized Trust (LFDT)](https://www.lfdecentralizedtrust.org). Smoot provides a modular, extensible bridge infrastructure for transferring assets and data across heterogeneous blockchain networks.

<!-- TODO: Add a project banner image here -->
<!-- ![Smoot Banner](link-to-banner-image) -->

## What is Smoot?

Smoot is a cross-chain bridge framework designed to enable secure, verifiable asset transfers between different blockchain networks. The project originated as a Stellar–Polygon asset bridge and has since evolved into a general-purpose interoperability solution that can be extended to support additional chains.

Smoot's architecture is organized into distinct layers:

- **Application Layer (`apps/`)** — User-facing interfaces including a GUI for interacting with the bridge, initiating transfers, and monitoring transaction status.
- **Contract Layer (`contracts/`)** — On-chain smart contracts (Solidity, Rust) that handle locking, minting, burning, and releasing of assets on each supported chain. Includes reference implementations such as ERC-3643 compliant token contracts.
- **Agent / Relay Layer (`agent/`)** — Off-chain relay services that listen for cross-chain events, verify proofs, and submit corresponding transactions on destination chains.
- **SDK Layer (`sdks/`)** — Developer libraries for programmatically interacting with the bridge infrastructure.
- **Services (`services/`)** — Supporting microservices for the bridge ecosystem.

This layered design allows developers to build cross-chain applications on top of Smoot, customize individual components, or extend the framework to support new blockchain networks.

## Supported Standards

Smoot currently supports the following token standards and integration targets:

| Standard / Integration | Status | Notes |
|---|---|---|
| ERC20 | Supported | Fungible token transfers through the bridge framework |
| ERC721 | Supported | NFT transfer support |
| ERC3643 | Supported | Permissioned token support; implemented in a way that is compatible with ERC20-style interactions |
| Stellar | Supported / Origin implementation | Smoot originated from a Stellar–Polygon asset bridge |
| Polygon | Supported / Origin implementation | Part of the original Stellar–Polygon bridge implementation |
| Cardano | In progress | Integration is pending and under review |

Additional standards and chain integrations may be added based on roadmap priorities, community demand, and partner contributions.


## Repository Guide

| Repository | Description |
|---|---|
| [**bridge**](https://github.com/LFDT-Smoot/bridge) | The core bridge implementation — smart contracts, relay agents, SDKs, application interfaces, deployment scripts, and tests. This is where the main development happens. |
| [**governance**](https://github.com/LFDT-Smoot/governance) | Project governance documents including the [Smoot Technical Charter](https://github.com/LFDT-Smoot/governance/blob/main/Smoot%20Technical%20Charter%20Final%204-17-2025.md), configuration files, and the project license. |

### Inside the `bridge` Repository

| Directory | Purpose |
|---|---|
| `apps/` | Front-end application and GUI for end users |
| `contracts/` | On-chain smart contracts (Solidity, Rust) |
| `agent/` | Off-chain relay/agent services |
| `sdks/` | Developer SDKs for programmatic bridge interaction |
| `services/` | Supporting backend services |
| `deployment/` | Deployment scripts and infrastructure configuration |
| `design/` | Architecture and design documents |
| `docs/` | Project documentation |
| `requirement/` | Requirements and specifications |
| `test/` | Test suites and testing utilities |

## Getting Started

<!-- TODO: Replace with actual getting-started steps once documentation is ready -->

1. **Explore the architecture** — Review the design documents in [`bridge/design/`](https://github.com/LFDT-Smoot/bridge/tree/main/design) and the docs in [`bridge/docs/`](https://github.com/LFDT-Smoot/bridge/tree/main/docs) to understand how Smoot works.
2. **Set up locally** — Clone the [bridge](https://github.com/LFDT-Smoot/bridge) repository and follow the setup instructions in the README.
3. **Try the examples** — XYZ directory demonstrates end-to-end cross-chain transfers. <!-- TODO: are there examples here? --> 
4. **Read the contracts** — Smart contracts in `contracts/` are the on-chain component of the bridge and a good starting point for understanding the trust model.  <!-- TODO: check with maintainers -->

## Roadmap

<!-- TODO: Maintainers should fill in concrete milestones, timelines, and links to tracking issues -->

Smoot's initial code migration from its predecessor project is complete. Current and planned areas of development include:

- **Multi-party computation (MPC) for relayers** — Enhancing the relay layer with threshold signatures to remove single-point-of-trust assumptions.
- **Zero-knowledge proof integration** — Adding ZK-based verification for cross-chain state proofs.
- **Additional chain support** — Extending the framework to new networks including Cardano, with further integrations planned based on community demand.
- **Hybrid bridging modes** — Supporting both lock-and-mint and liquidity-pool-based transfer mechanisms.

We welcome community input on roadmap priorities. Please open an issue in the [bridge repository](https://github.com/LFDT-Smoot/bridge/issues) or raise it in our community calls.

## Resources

The following documents and links will help you understand Smoot's vision, governance, and community processes:

- Our [Code of Conduct](https://www.lfdecentralizedtrust.org/code-of-conduct).
- The [Smoot Technical Charter](https://github.com/LFDT-Smoot/governance/blob/main/Smoot%20Technical%20Charter%20Final%204-17-2025.md) describes the project's governance structure and decision-making processes.
- Community presentations and recordings are available in the [Smoot YouTube playlist](https://www.youtube.com/playlist?list=PL0MZ85B_96CE-gF5178qvm0-kdt5xggPE).
- All Smoot repositories are licensed under the [Apache 2.0 License](https://github.com/LFDT-Smoot/governance/blob/main/LICENSE).
<!-- TODO: Add these files and uncomment the links
- Our [CONTRIBUTING.md](https://github.com/LFDT-Smoot/bridge/blob/main/CONTRIBUTING.md) explains how to contribute code, documentation, and ideas.
- Our [MAINTAINERS.md](https://github.com/LFDT-Smoot/bridge/blob/main/MAINTAINERS.md) lists the current project maintainers and their affiliations.
- Our [SECURITY.md](https://github.com/LFDT-Smoot/bridge/blob/main/SECURITY.md) describes how to responsibly report security vulnerabilities. Do not post security issues publicly.
-->

### Files to Be Added

The following standard LFDT project files are in progress, and will be updated soon:
<!-- TODO: Maintainers: please create these in the `bridge` repository as soon as possible. -->

- `CONTRIBUTING.md` — Contribution guidelines (coding standards, PR process, commit conventions)
- `MAINTAINERS.md` — List of maintainers with names, organizations, and GitHub handles
- `SECURITY.md` — Vulnerability disclosure and reporting policy
- `CODE_OF_CONDUCT.md` — Or a link to the [LFDT Code of Conduct](https://www.lfdecentralizedtrust.org/code-of-conduct)
- `ADOPTERS.md` — Organizations and projects using Smoot in production or development

## Discord Communication Channels

Discord is the primary communication platform for LFDT projects, including Smoot.

### How to Join

1. **Join the LFDT Discord Server** — Click the invite link: **[LFDT Discord](https://discord.gg/hyperledger)**. Create a free Discord account if you don't already have one.
2. **Agree to the server rules** — You'll land in a welcome or rules channel. Read and accept the rules to unlock the full set of channels.
3. **Find the Smoot channels** — Look for Smoot-related channels under the LFDT channel categories.

<!-- TODO: Replace with actual Smoot Discord channel links once they exist -->

| Channel | Purpose |
|---|---|
| **#smoot-general** | General discussion, questions, and conversation about Smoot |


## Community Meetings

<!-- TODO: Replace with actual Zoom/LFX calendar links and registration URLs -->

Smoot holds regular community calls open to everyone. These are the best way to stay up to date, ask questions, and contribute to the project direction.

| Meeting | Frequency | Calendar Link |
|---|---|---|
| Smoot Community Call | Bi-weekly | https://zoom-lfx.platform.linuxfoundation.org/meetings/smoot?view=week | 

### Meeting Recordings

Past meeting recordings and presentations can be accessed through:

1. **[LFX Individual Dashboard](https://openprofile.dev/)** — Create your profile, then check [My Meetings](https://openprofile.dev/my-meetings) for recordings of meetings you're registered for.
2. **LFDT Calendar** — Browse past meeting recordings in the [LFDT project calendars](https://zoom-lfx.platform.linuxfoundation.org/meetings/lf-decentralized-trust).

## LFX Tooling

LFDT projects benefit from the Linux Foundation's LFX platform for project health monitoring and community management.

- [**LFX Insights**](https://insights.linuxfoundation.org/) — Track project health metrics including contributor activity, commit trends, and community growth. [Learn more](https://insights.linuxfoundation.org/docs/introduction/what-is-insights/).
- [**LFX Individual Dashboard**](https://openprofile.dev/) — Manage your open-source profile and access meeting recordings. [Learn more](https://docs.linuxfoundation.org/lfx/my-profile).

## Contributing

We welcome contributions of all kinds — code, documentation, testing, design feedback, and use-case ideas. Here's how to get started:

1. **Check the issues** — Browse [open issues](https://github.com/LFDT-Smoot/bridge/issues) in the bridge repository for tasks that interest you. Look for issues labeled `good first issue` or `help wanted`.
2. **Join the conversation** — Introduce yourself on Discord or attend a community call. We're happy to help newcomers find a good starting point.
3. **Open a PR** — Fork the repository, make your changes on a branch, and submit a pull request with a clear description of what you've done and why.
4. **Report bugs** — If you find a problem, open an issue with steps to reproduce it.
5. **Propose features** — Have an idea? Open an issue describing the use case and your proposed approach. Discussing first helps align efforts and avoids duplicate work.

## Current Status

Smoot is an **incubation** project under LFDT. The initial code migration from its predecessor project is complete, and the team is actively developing new features and working to grow the contributor community. We are looking for collaborators from organizations interested in cross-chain interoperability — whether you want to integrate a new chain, contribute to the relay infrastructure, or build applications on top of Smoot.

## License

All Smoot repositories are licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).