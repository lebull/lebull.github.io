### Requirement: Resume site is publicly accessible via GitHub Pages
The system SHALL publish the resume as a static HTML page at the repository's GitHub Pages URL, accessible without authentication.

#### Scenario: Visitor loads the resume page
- **WHEN** a user navigates to the GitHub Pages URL in a browser
- **THEN** the browser SHALL render the resume with all sections (Personal Information, Education, Skills, Roles) visible and properly formatted

### Requirement: Resume page is styled for screen viewing
The HTML page SHALL include CSS styles that present the resume in a clean, readable, professional layout on screen.

#### Scenario: Screen layout renders correctly
- **WHEN** the page is loaded in a modern browser at desktop viewport width
- **THEN** the resume SHALL display with clear visual hierarchy, readable typography, and appropriate spacing between sections

#### Scenario: Contact information is prominent
- **WHEN** the page is rendered
- **THEN** the name, email, and phone number SHALL appear in a visually distinct header section at the top of the page

### Requirement: Resume page produces a print-ready single-page PDF
The HTML page SHALL include `@media print` CSS that produces a clean, professional resume document when printed or exported to PDF.

#### Scenario: Print margins follow resume conventions
- **WHEN** the user prints the page or exports to PDF
- **THEN** all four margins SHALL be set to 0.5 inches via the `@page` rule

#### Scenario: Print font size is appropriate for paper
- **WHEN** the user prints the page or exports to PDF
- **THEN** body text SHALL render at 10pt and section headings SHALL render at no larger than 12pt

#### Scenario: Decorative screen styles are suppressed in print
- **WHEN** the user prints the page or exports to PDF
- **THEN** background colors, box shadows, and non-essential borders SHALL be removed so the output matches standard black-and-white resume conventions

#### Scenario: Job entries do not break across pages
- **WHEN** the user prints the page or exports to PDF
- **THEN** each individual role entry (company, title, dates, bullet points) SHALL use `page-break-inside: avoid` to prevent splitting across pages where possible

#### Scenario: Section headings are not orphaned at page bottom
- **WHEN** the user prints the page or exports to PDF
- **THEN** section headings (Education, Skills, Experience) SHALL use `page-break-after: avoid` so they are never the last element on a page

### Requirement: Deployment is automated via GitHub Actions
The repository SHALL include a GitHub Actions workflow that automatically deploys the site to GitHub Pages on every push to the `main` branch.

#### Scenario: Push to main triggers deployment
- **WHEN** a commit is pushed to the `main` branch
- **THEN** the GitHub Actions workflow SHALL run and publish the updated site to GitHub Pages without manual intervention

#### Scenario: Deployment uses only repository root files
- **WHEN** the workflow runs
- **THEN** it SHALL deploy the repository root (containing `index.html` and `styles.css`) as the GitHub Pages source, requiring no build step
