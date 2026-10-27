# LAN discovery and role-transparent networking — options

**Status:** Initial comparison; no data-plane architecture selected.

| Option | User setup | Internal roles | Main trade-off |
|---|---|---|---|
| Discover an existing Deskflow server via DNS-SD/mDNS | No IP entry; may still require choosing an input host | Existing server/client | Smallest upstream change, but does not satisfy a strict no-server requirement |
| Discover peers, establish trust, dynamically elect/assign transport roles | No visible server/client choice | Temporary or elected coordinator may exist | Likely incremental path; election, recovery and conflict semantics need proof |
| Fully decentralized peer mesh with shared topology and direct control sessions | No visible roles | No fixed coordinator | Closest literal reading of “mesh”; highest complexity for focus ownership, concurrent input, trust and topology consistency |

## Recommendation for the next decision

Do not rewrite Deskflow's input pipeline before testing discovery. Start by mapping the server/client boundary and TLS/fingerprint handling, then run a LAN discovery/pairing spike that keeps input forwarding disabled until explicit trust. In parallel, decide whether an invisible/elected coordinator is acceptable. This separates “I never configure a server” (a UX goal) from “the transport has no coordinating peer” (an architectural constraint).

Bonjour is Apple's DNS-SD/mDNS implementation and was mentioned as a candidate, not a commitment. Compare the platform-neutral APIs and permissions already used by Deskflow on macOS, Windows, and Linux; retain a manual pairing-code or hostname fallback for networks that suppress multicast.

## Evidence references

- [Deskflow protocol reference](https://github.com/deskflow/deskflow/blob/master/docs/dev/protocol_reference.md)
- [Deskflow configuration reference](https://github.com/deskflow/deskflow/blob/master/docs/Configuration.md)
- [Deskflow project forks wiki](https://github.com/deskflow/deskflow/wiki/Project-Forks)
- [Symless: Deskflow and Synergy](https://symless.com/synergy/open-source)
