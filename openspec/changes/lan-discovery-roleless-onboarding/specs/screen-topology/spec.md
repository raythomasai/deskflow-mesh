## ADDED Requirements

### Requirement: Spatial screen handoff
The application SHALL allow a user to define screen adjacency by side, edge, or corner and SHALL route pointer focus and keyboard control according to that arrangement.

#### Scenario: Pointer crosses an adjacent screen boundary
- **GIVEN** two trusted devices are arranged as neighbors
- **WHEN** the pointer crosses the configured boundary
- **THEN** pointer focus moves to the adjacent device
- **AND** keyboard input follows the active focus according to the selected ownership model
