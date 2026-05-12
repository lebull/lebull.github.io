## 1. HTML Structure

- [x] 1.1 Create `index.html` at the repository root with semantic HTML5 structure (header, main, sections)
- [x] 1.2 Add a `<head>` with `<meta charset>`, `<meta name="viewport">`, a descriptive `<title>`, and a `<link>` to `styles.css`
- [x] 1.3 Add name, email, and phone to a visually distinct `<header>` element
- [x] 1.4 Add Education section with degree, institution, and year
- [x] 1.5 Add Skills section with skill categories rendered as labeled groups
- [x] 1.6 Add Experience section with all three roles (Cox Automotive, Veseris, International Paper), each including company name, title, location/date range, and bullet points

## 2. Screen Styles

- [x] 2.1 Create `styles.css` at the repository root
- [x] 2.2 Set a readable base font (system font stack or web-safe serif/sans-serif), comfortable line height, and max-width for the content area
- [x] 2.3 Style the header with name prominently sized and contact info below it
- [x] 2.4 Style section headings with clear hierarchy and a visual separator (e.g., bottom border)
- [x] 2.5 Style job role entries so company, title, and date/location are clearly distinguished
- [x] 2.6 Style bullet lists with appropriate spacing and no excessive indentation

## 3. Print Styles

- [x] 3.1 Add `@media print` block to `styles.css`
- [x] 3.2 Add `@page` rule setting all margins to `0.5in`
- [x] 3.3 Set body `font-size: 10pt` and headings to `11pt`–`12pt` within the print block
- [x] 3.4 Remove background colors, box shadows, and decorative borders in print styles
- [x] 3.5 Apply `page-break-inside: avoid` to each role/job entry element
- [x] 3.6 Apply `page-break-after: avoid` to all section headings (`h2`)
- [x] 3.7 Ensure the page header (name + contact) does not break across pages

## 4. GitHub Actions Deployment

- [x] 4.1 Create `.github/workflows/deploy.yml`
- [x] 4.2 Configure the workflow to trigger on push to `main`
- [x] 4.3 Set workflow permissions for `pages: write` and `id-token: write`
- [x] 4.4 Add a job that uses `actions/configure-pages`, `actions/upload-pages-artifact` (pointing at the repository root), and `actions/deploy-pages` to publish the site
- [x] 4.5 Add a comment in the workflow file noting that GitHub Pages must be enabled in repo Settings → Pages → Source: GitHub Actions

## 5. Verification

- [ ] 5.1 Open `index.html` in a browser and confirm all resume sections render correctly
- [ ] 5.2 Use browser Print Preview (Chrome recommended) to verify margins, font sizes, and page breaks
- [ ] 5.3 Confirm no section heading is orphaned at the bottom of a page in the print preview
- [ ] 5.4 Push to `main` and confirm the GitHub Actions workflow runs successfully and the page is live at the GitHub Pages URL
