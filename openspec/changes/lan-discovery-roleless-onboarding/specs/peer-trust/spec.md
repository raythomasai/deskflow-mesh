## ADDED Requirements

### Requirement: Discovery does not authorize remote input
The application SHALL require an explicit user trust action and a validated secure peer session before accepting keyboard or mouse input from another device.

#### Scenario: An unknown peer advertises itself
- **WHEN** a compatible but unpaired device is discovered
- **THEN** it is presented as untrusted
- **AND** it cannot send input events or change the local screen topology

#### Scenario: A user approves a peer
- **WHEN** the user explicitly pairs a peer and its identity/session validation succeeds
- **THEN** the peer may be configured for input sharing subject to local OS permissions
- **AND** the trust decision is visible and revocable
