## ADDED Requirements

### Requirement: Discover compatible local peers without manual address entry
The application SHALL make compatible peers on the same local network discoverable without requiring the user to enter an IP address or designate a user-facing server/client role.

#### Scenario: A compatible peer appears on the same LAN
- **WHEN** a user runs the application on a network with another compatible device
- **THEN** the peer can be shown by a human-readable device identity without manual IP entry
- **AND** discovery alone does not establish trust or route input

#### Scenario: Multicast discovery is unavailable
- **WHEN** a local network suppresses the discovery mechanism
- **THEN** the application provides an intentional authenticated fallback
- **AND** it does not silently connect to an unverified address
