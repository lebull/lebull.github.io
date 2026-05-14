## Why

The resume page currently has a flat, cool-toned background that provides no visual depth or personality. Adding a warm, linen-toned parallax background with soft blob shapes will make the page feel more inviting and visually distinctive while keeping the resume card as the clear focal point.

## What Changes

- Replace the flat `--page-bg` color with a warm linen/stone gradient base
- Add layered, blurred blob shapes (soft sand and warm taupe) that drift with mouse position, creating a subtle parallax depth effect
- Scope the parallax effect to desktop only — mobile/print unaffected

## Capabilities

### New Capabilities
- `parallax-background`: Mouse-position-driven parallax background with warm linen base and layered blob shapes, visible only on desktop

### Modified Capabilities

## Impact

- `styles.css`: New `--page-bg` token value, background blob styles, desktop media query scope
- `index.html`: New background layer elements (or CSS-only approach via pseudo-elements)
- Small vanilla JS snippet for mouse-position tracking (no dependencies)
- `@media print`: Background suppressed — no impact on print output
