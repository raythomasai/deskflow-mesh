# LAN discovery and role-transparent onboarding

## Why

Deskflow currently expects users to configure a server/client relationship and network address. The product goal is to start the application on nearby computers, discover compatible peers on the local network, arrange screens spatially, and move keyboard/mouse focus by crossing a screen boundary—without asking the user to choose a server, client, host, or IP address.

This is a material change to discovery, pairing, and possibly the transport model. It should be approached as a staged fork of Deskflow, preserving its existing input pipeline and security behaviors until alternatives are justified.

## Scope

- Specify role-neutral local discovery and explicit trust.
- Preserve the screen-edge/corner layout and keyboard/mouse focus handoff as core behavior.
- Compare keeping Deskflow's server/client data plane behind role-transparent discovery with an elected coordinator and a fully coordinator-free peer mesh.
- Define the first LAN discovery/pairing experiment and its security constraints.

## Non-goals

- WAN relay, cloud rendezvous, or public discovery.
- Automatically trusting every device found on a LAN.
- Replacing Deskflow's native input pipeline before an architecture decision.
- Claiming that a web preview can capture or inject native keyboard/mouse events.
- Selecting permanent macOS-only support merely because Bonjour was named in the source idea.

## Proposed first slice

Complete a source-grounded architecture and threat-model pass, then prototype local peer advertisement/discovery on a controlled LAN with explicit pairing and no input injection. Demonstrate whether role-transparent setup can coexist with Deskflow's current transport. Keep coordinator-free mesh as an unresolved decision until this evidence exists.

## Decisions and questions

- User-facing rolelessness is a firm goal; a hidden/elected transport coordinator is not yet ruled out.
- “Mesh” is a creator-stated direction, not yet a precise protocol requirement.
- Target OS and simultaneous-input behavior remain unresolved and should be decided before the first native implementation slice.
- Bonjour/DNS-SD/mDNS is a candidate to evaluate, not a committed dependency.
