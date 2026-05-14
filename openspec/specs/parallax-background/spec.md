## ADDED Requirements

### Requirement: Warm linen base background
The page body SHALL use a warm linen color (`#ede8df`) as the base background color on all screen sizes.

#### Scenario: Page loads on any device
- **WHEN** the page loads on any screen size
- **THEN** the body background SHALL be warm linen (`#ede8df`) rather than the previous cool blue-gray

---

### Requirement: Blob layer rendered on desktop
The system SHALL render a fixed background layer containing 3 soft, heavily-blurred blob shapes on screens 768px wide and above.

#### Scenario: Desktop viewport
- **WHEN** the viewport width is 768px or greater
- **THEN** a `#bg-layer` element SHALL be visible with 3 blob child elements styled as large, blurred warm-tone radial shapes

#### Scenario: Mobile viewport
- **WHEN** the viewport width is less than 768px
- **THEN** `#bg-layer` SHALL NOT be visible and the plain linen background SHALL show

---

### Requirement: Mouse-position parallax on blobs
Each blob SHALL move in response to mouse cursor position at an independent multiplier, creating a depth effect.

#### Scenario: User moves mouse across viewport
- **WHEN** the user moves the mouse cursor
- **THEN** each blob SHALL translate by a fraction of the cursor's offset from viewport center, with blob A moving most (multiplier ~0.025), blob C mid (~0.016), and blob B least (~0.010)

#### Scenario: Parallax is desktop-only
- **WHEN** the viewport is less than 768px wide
- **THEN** no mouse listener SHALL be active and blobs SHALL remain stationary (or hidden)

---

### Requirement: Print suppression
The background blob layer SHALL not appear in print output.

#### Scenario: User prints page
- **WHEN** the page is printed or rendered in print media
- **THEN** `#bg-layer` SHALL be hidden and no background color or blob shapes SHALL appear on the printed output
