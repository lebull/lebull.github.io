## Context

The resume is maintained as a single Markdown file (`source.md`). There is currently no web presence or shareable link. The goal is to publish a styled static page to GitHub Pages so the resume can be viewed in a browser and printed/exported to PDF with professional formatting.

The output must be fully static (no framework, no JS bundler) so it remains easy to maintain and GitHub Pages can serve it directly without any configuration beyond enabling the feature. The HTML is hand-authored rather than generated, because the web presentation is expected to diverge from the plain-text Markdown in structure and wording.

## Goals / Non-Goals

**Goals:**
- Publish the resume as a GitHub Pages site at the repository's `github.io` URL
- Style the page attractively for screen viewing
- Apply `@media print` styles that follow resume print best practices: correct margins, no background colors, no widow/orphan headings, single-column layout, font sizes appropriate for paper
- Automate deployment on every push to `main` via GitHub Actions
- Hand-author `index.html` so the web presentation can be tuned independently of `source.md`

**Non-Goals:**
- Dark mode or theme switching
- Multiple page/version support
- JavaScript interactivity
- A "Download PDF" button (users can use browser Print → Save as PDF)

## Decisions

### Hand-authored `index.html`
**Decision**: Maintain `index.html` directly rather than generating it from `source.md`.

**Rationale**: The web presentation is expected to deviate from the plain-text Markdown — different wording, richer structure, custom groupings. A generation step would impose a lowest-common-denominator constraint on both files. Keeping them separate lets each be optimised for its medium (`source.md` for ATS/plain-text; `index.html` for the browser).

**Alternative considered**: pandoc with `--template`. Rejected because anticipated content divergence means the generated output would need manual overrides anyway, removing the benefit of automation.

**Alternative considered**: Jekyll. Rejected because it requires `_config.yml`, Gemfile, and Liquid templates — significant overhead for a single document.

### CSS-only styling (no JavaScript)
**Decision**: All layout and print behavior implemented via CSS only.

**Rationale**: JavaScript is unnecessary for a static resume page and would add complexity. CSS `@media print` is the standard, well-supported mechanism for controlling printed output.

### GitHub Actions deploy workflow
**Decision**: The workflow publishes the repository root directly (no build step) using the official `actions/upload-pages-artifact` / `actions/deploy-pages` actions.

**Rationale**: With no build step, `index.html` and `styles.css` at the repo root are the deployable artifact. Publishing the root avoids any intermediate directory management and keeps the workflow trivially simple.

### Print CSS approach
- Set `@page` margins to 0.5in (standard resume margin)
- Use `font-size: 10pt` for body, 11-12pt for headings
- Remove box shadows, background colors, and decorative borders in print
- Apply `page-break-inside: avoid` to job entries and `page-break-after: avoid` to headings
- Ensure contact/header section does not break across pages

## Risks / Trade-offs

- **Manual sync between `source.md` and `index.html`** → Resume content exists in two files. Mitigation: `source.md` is updated first (ATS/plain-text record), then `index.html` is updated to match. Structure is stable and changes infrequently.
- **Print output varies by browser** → CSS print rendering differs between Chrome, Firefox, and Safari. Mitigation: target Chrome/Chromium (most common for PDF export via "Print to PDF") as the primary print surface; test Firefox as secondary.
- **GitHub Pages URL depends on repo visibility and org settings** → If the repo is private the Pages URL may not be publicly accessible without a paid plan. Mitigation: documented in the deploy workflow README comment.

## Open Questions

_All open questions resolved._

- **PDF button?** → No. Users use browser Print → Save as PDF.
- **Source of truth?** → `source.md` is the canonical content record; `index.html` is a curated web version maintained in parallel.
