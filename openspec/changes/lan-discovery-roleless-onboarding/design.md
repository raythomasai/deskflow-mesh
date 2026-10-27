# Design — LAN discovery and role-transparent onboarding

## Current boundary

Deskflow's documented protocol remains client/server: a server listens and one or more clients connect. Its configuration includes host and peer-trust details, while screen topology controls where pointer focus transfers. The forks wiki says auto-discovery is not currently a Deskflow goal. Keep those facts separate: discovering peers does not itself require a fully decentralized data plane.

## Candidate architecture stages

1. **Discovery:** advertise a minimal, non-secret compatible-service record on the local network using a cross-platform DNS-SD/mDNS implementation. Discovery only populates a peer list.
2. **Trust:** require an explicit local action to pair, then bind a durable peer identity/fingerprint and establish an encrypted session. A spoofed advertisement must not authorize input.
3. **Topology:** represent the user's arrangement as screen-to-screen edge/corner relationships. Reuse the proven Deskflow transition behavior where possible.
4. **Transport roles:** prototype role-transparent discovery over the current data plane. If the user requires no coordinator, separately evaluate elected ownership or true peer sessions, reconnection, conflicting layouts, and concurrent input.

## Security and failure behavior

- Treat the LAN and multicast advertisements as untrusted.
- Never accept or route input from a discovered-but-unpaired peer.
- Keep TLS/fingerprint validation and permission prompts; do not weaken them to make pairing appear automatic.
- Handle blocked multicast with a deliberate fallback (e.g. one-time pairing code); do not fall back to unauthenticated IP auto-connect.
- Document the OS's local-network and accessibility/input-capture permissions as separate from network discovery.

## Constraints and unresolved decisions

- Deskflow spans Windows, macOS, and Linux; the first experimental OS is not confirmed.
- Bonjour is mentioned in the source idea, but platform portability and its API licensing/packaging implications need investigation.
- It is unknown whether multiple peers may concurrently originate input, or whether one transiently owns focus.
- No public protocol change is specified in this proposal; compatibility/migration needs a separate decision.
