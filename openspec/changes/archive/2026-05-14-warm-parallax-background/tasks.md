## 1. CSS — Base Background

- [x] 1.1 Update `--page-bg` token in `styles.css` to warm linen (`#ede8df`)
- [x] 1.2 Add `#bg-layer` styles: fixed position, full viewport, `pointer-events: none`, `z-index: -1`
- [x] 1.3 Add blob base styles: `position: absolute`, `border-radius: 50%`, `will-change: transform`
- [x] 1.4 Add blob A styles: ~70vw size, `background: rgba(226,213,191,0.55)`, `filter: blur(100px)`, initial position top-left area
- [x] 1.5 Add blob B styles: ~60vw size, `background: rgba(217,205,176,0.40)`, `filter: blur(120px)`, initial position bottom-right area
- [x] 1.6 Add blob C styles: ~55vw size, `background: rgba(235,225,208,0.35)`, `filter: blur(80px)`, initial position top-right area
- [x] 1.7 Scope `#bg-layer` to desktop only with `@media (max-width: 767px) { #bg-layer { display: none; } }`
- [x] 1.8 Add `@media print { #bg-layer { display: none; } }`

## 2. HTML — Blob Elements

- [x] 2.1 Add `<div id="bg-layer">` with three child `<div>` elements (`.blob-a`, `.blob-b`, `.blob-c`) directly inside `<body>`, before `.resume`

## 3. JS — Mouse Parallax

- [x] 3.1 Add inline `<script>` at end of `<body>` that listens for `mousemove` on `window`
- [x] 3.2 Compute cursor offset from viewport center (`x - vw/2`, `y - vh/2`)
- [x] 3.3 Apply `transform: translate()` to each blob at multipliers: A=0.025, C=0.016, B=0.010
- [x] 3.4 Wrap listener activation in `matchMedia('(min-width: 768px)')` check

## 4. Verification

- [x] 4.1 Confirm warm linen background visible on desktop and mobile
- [x] 4.2 Confirm blobs visible and moving on desktop mouse interaction
- [x] 4.3 Confirm no blobs or JS active on mobile viewport
- [x] 4.4 Confirm `@media print` hides bg layer (use browser print preview)
