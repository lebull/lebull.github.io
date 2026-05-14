## Context

The resume page uses a flat `#dde2ea` (cool blue-gray) `body` background. The resume card sits centered on top of this. The goal is to replace the flat background with a warm, linen-toned scene using layered, blurred blob shapes that respond to mouse movement — giving the page subtle depth and warmth without distracting from the card.

Current stack: plain HTML + CSS in `index.html` / `styles.css`. No build step for these files. Vanilla JS is acceptable.

## Goals / Non-Goals

**Goals:**
- Warm linen/stone page background (replaces flat `--page-bg`)
- 2–3 soft blob shapes (blurred radial gradients) layered behind the card
- Mouse-position parallax: blobs drift at different speeds as the cursor moves
- Scoped to desktop only (`min-width: 768px`)
- No visible change on mobile or in print

**Non-Goals:**
- Scroll-based parallax (resume is too short for meaningful scroll depth)
- Canvas or WebGL — pure CSS + minimal vanilla JS only
- Animated entrance or loop animations
- Any change to the card itself

## Decisions

### Blob implementation: CSS absolute elements + JS transform

**Decision:** Add 2–3 absolutely-positioned `<div>` blob elements inside a fixed `#bg-layer` container, styled with `border-radius: 50%`, large `filter: blur()`, and semi-transparent warm fill colors. A small JS listener updates `transform: translate()` on each blob at a different multiplier to create depth.

**Alternatives considered:**
- `background-attachment: fixed` on `body` — free parallax with zero JS, but only works for a single image/gradient layer; can't easily do multiple independently-moving blobs.
- CSS `@property` animated custom properties — no mouse tracking, scroll-only.
- Canvas — overkill, adds complexity and a render loop.

**Rationale:** A few DOM elements + 15 lines of JS is the simplest path to independent multi-layer mouse parallax.

---

### Color palette: warm linen/stone

```
base body bg:  #ede8df  (warm linen)
blob A:        rgba(226, 213, 191, 0.55)  (sand, closer layer — moves more)
blob B:        rgba(217, 205, 176, 0.40)  (warm taupe, far layer — moves less)
blob C:        rgba(235, 225, 208, 0.35)  (pale stone, mid layer)
```

Blobs are large (60–80vw), heavily blurred (`blur(80px)–blur(120px)`), ensuring they read as ambient light rather than sharp shapes.

---

### Parallax multipliers

| Layer | Multiplier | Feels like |
|-------|-----------|------------|
| Blob A (near) | 0.025 | Closest, moves most |
| Blob B (far)  | 0.010 | Furthest, barely moves |
| Blob C (mid)  | 0.016 | In between |

Mouse delta from viewport center is multiplied per blob. Max offset clamped to prevent blobs from leaving screen.

---

### Desktop-only scope

The `#bg-layer` and JS listener are activated only inside a `matchMedia('(min-width: 768px)')` check. On mobile the body simply shows the base linen color with no blobs or JS.

## Risks / Trade-offs

- **`filter: blur()` GPU cost** → Mitigation: use `will-change: transform` on blob elements; blobs are few and large (cheap to composite). Test on low-end hardware.
- **Flash before JS loads** → Mitigation: CSS sets the base linen body background unconditionally; blobs are enhancement-only.
- **Print regression** → Mitigation: `@media print { #bg-layer { display: none; } }` already in scope.
