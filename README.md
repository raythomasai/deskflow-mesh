# Deskflow Mesh

A public [Deskflow](https://github.com/deskflow/deskflow) fork exploring role-neutral, zero-configuration discovery for sharing a keyboard and mouse across nearby computers.

## Project status

**Architecture proposal only.** This fork does not yet implement LAN discovery, mesh transport, or new pairing behavior. Do not use it as a finished product.

The goal is to let devices discover compatible peers on the same local network without asking users to designate a server/client or enter IP addresses, while preserving an explicit trust step and Deskflow's screen-edge/corner handoff model. Bonjour/DNS-SD/mDNS is a candidate to investigate, not a chosen dependency. A hidden or elected coordinator may still be compatible with the role-neutral user experience; whether a coordinator-free mesh is required remains open.

Start with the [project kickoff](docs/mesh-project/README.md), [architecture options](docs/mesh-project/architecture-options.md), and the [OpenSpec proposal](openspec/changes/lan-discovery-roleless-onboarding/proposal.md).

## Upstream and license

This is a fork of [deskflow/deskflow](https://github.com/deskflow/deskflow). Preserve its attribution and license metadata. The upstream repository's REUSE declarations include GPL-2.0-only with an OpenSSL exception for applicable files; see [`REUSE.toml`](REUSE.toml), [`LICENSE`](LICENSE), and [`LICENSES/`](LICENSES/).
