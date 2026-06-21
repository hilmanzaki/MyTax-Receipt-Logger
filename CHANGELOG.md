# Change Log
All notable changes to this project will be documented in this file.

## [1.0.1] - 2026-06-21

Hotfix for the blank-page bug discovered a week after the first deployment. No feature changes, fix is applied only to `index.html`.

### Added

### Changed

### Fixed

- [BUG-001](../../issues/1)
  MAJOR Blank page on GitHub Pages with console error `Uncaught SyntaxError:
  Cannot use import statement outside a module` at `transformScriptTags.ts`.
  Caused by Babel Standalone defaulting to the "automatic" JSX runtime, which
  injects an ES module `import` statement that plain (non-module) browser
  `<script>` tags cannot execute. Fixed by loading `app.js` manually via
  `fetch()` and explicitly transforming it with Babel's `classic` JSX runtime
  (`presets: [['react', { runtime: 'classic' }]]`) before injecting it as a
  script. Reproduced locally with `npx serve`, verified clean console and full
  functionality before committing.

## [1.0.0] - 2026-06-14

Initial release of the UI-only prototype with CI/CD pipeline.

### Added

- [FEAT-001](../../issues/2)
  MAJOR User registration and login (browser-storage based authentication).
- [FEAT-002](../../issues/3)
  MAJOR Receipt upload supporting JPEG, PNG and PDF formats.
- [FEAT-003](../../issues/4)
  MINOR Client-side OCR auto-fill using Tesseract.js, with manual override of
  all extracted fields.
- [FEAT-004](../../issues/5)
  MINOR UI for receipt categorisation against official LHDN MyTax relief categories.
- [FEAT-005](../../issues/6)
  MINOR UI for dashboard with real-time claimable amount tracking per category.
- [FEAT-006](../../issues/7)
  MINOR UI for search and filter receipts by merchant, category and date range.
- [FEAT-007](../../issues/8)
  MINOR UI for Hot --> Cold storage lifecycle simulation, modelled after Azure Blob
  Storage lifecycle management policy, 30 days move from Hot tier to Cold tier
- [FEAT-008](../../issues/9)
  MINOR Annual tax claim summary report with PDF export via browser print.
- [FEAT-009](../../issues/10)
  MAJOR GitHub Actions CI/CD pipeline: a CI job compiles the React/JSX source
  with Babel to verify the build, and a CD job deploys to GitHub Pages only
  if the CI job passes.

### Changed

### Fixed
