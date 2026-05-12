## Why

The resume exists only as a Markdown source file with no way to share or print it. Publishing it as a GitHub Pages site provides a publicly accessible, well-formatted, and print-ready version without any additional hosting cost.

## What Changes

- Add an `index.html` that renders the resume content with web and print styles
- Add a GitHub Actions workflow to publish the site to GitHub Pages on every push to `main`
- Add a `styles.css` with a screen layout and `@media print` rules tuned for resume best practices (single page, no orphaned headings, correct margins)

## Capabilities

### New Capabilities

- `resume-site`: A static HTML page hosted on GitHub Pages that displays the resume content styled for both web viewing and print/PDF export

### Modified Capabilities

<!-- None - this is a net-new capability with no existing specs -->

## Impact

- Adds `index.html`, `styles.css`, and `.github/workflows/deploy.yml` to the repository root
- No changes to `source.md`
- Requires GitHub Pages to be enabled (set to deploy from the `gh-pages` branch or via GitHub Actions)
- No external dependencies beyond a standard browser
