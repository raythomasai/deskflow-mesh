# Deskflow Mesh — project kickoff

## Vision

Turn Deskflow's explicit server/client and address configuration into a role-neutral, local-network experience: devices discover one another, users arrange screens by edge/corner, and pointer focus crossing a boundary routes keyboard/mouse control to the adjacent device. The intended product remains a native desktop application; a browser mockup would validate UX only, not input capture or LAN transport.

## Grounded baseline

- This repository is a public fork of [deskflow/deskflow](https://github.com/deskflow/deskflow), not a clean-room rewrite.
- Deskflow's protocol still uses a listening server and connecting clients; discovery and UI roles are separate product questions. See the [protocol reference](https://github.com/deskflow/deskflow/blob/master/docs/dev/protocol_reference.md) and [configuration reference](https://github.com/deskflow/deskflow/blob/master/docs/Configuration.md).
- The project's [forks wiki](https://github.com/deskflow/deskflow/wiki/Project-Forks) currently says automatic discovery is not a Deskflow goal and contrasts historical Bonjour discovery and Synergy 3 mDNS. The page may be stale, so it is evidence of documented direction, not a current maintainer commitment.
- The source's REUSE metadata identifies GPL-2.0-only with an OpenSSL exception for the applicable component. Preserve upstream license notices and verify per-file SPDX data before distributing changes.
- Symless describes Deskflow as its upstream open-source project and Synergy as a downstream commercial distribution: [Symless open-source information](https://symless.com/synergy/open-source). The source concept did not specify which Synergy generation it meant.

## Product boundary and first sequence

1. **Feasibility:** map current server/client, TLS identity, and screen-topology boundaries; compare cross-platform DNS-SD/mDNS and pairing options; document OS permission constraints.
2. **Discovery slice:** prove compatible peers can be found on one LAN without manual IP entry. Discovery alone does not connect or trust a peer.
3. **Trust and layout:** make pairing explicit, then reuse the existing screen-edge/corner layout and focus-handoff behavior.
4. **Role-transparent transport:** evaluate whether role-neutral UX can run over discovered direct connections plus a hidden/elected coordinator, or whether a coordinator-free mesh is required.

The first implementation target is not chosen yet. A macOS/Bonjour spike is a reasonable experiment because the memo raises it, but the architecture must remain open to the upstream's Windows/Linux platforms.

## Open decisions

- Does “no server/client” mean no **user-configured roles**, or no coordinator at all?
- Which platforms are required for the first usable release? Is macOS-only acceptable for the initial discovery spike?
- Can each peer be an input source simultaneously, or is one active keyboard/mouse owner expected at a time?
- What pairing UX is acceptable, and what should happen when the LAN blocks multicast discovery?
- Should the first functional slice preserve Deskflow's current protocol and add discovery/pairing, or change the data plane immediately?

## Scope and security

- Local-LAN-first; no WAN relay or public discovery in this kickoff.
- No automatic input acceptance from an unpaired device. Require user-visible trust and a secure session.
- Keep OS input permissions and screen topology explicit; never claim discovery means the OS permits remote input injection.
- No code implementation or native build is claimed by this proposal. Product requirements and staged architecture are in [OpenSpec](../../openspec/changes/lan-discovery-roleless-onboarding/proposal.md).
