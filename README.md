# MoneyWise

MoneyWise is a mobile-first personal budgeting and savings PWA designed for GitHub Pages and iPhone Home Screen use.

## v0.48 architecture refactor

This release begins the modular JavaScript refactor while deliberately preserving the known-working v0.47 runtime. See `docs/ARCHITECTURE.md` and `CHANGELOG.md`.

## Local structure

- `index.html` — shell
- `css/app.css` — styles
- `js/config.js` — version/config boundary
- `js/app.js` — current application runtime
- `js/calculations/` — calculation modules being extracted
- `sw.js` — PWA service worker

## GitHub Pages

The project remains a static site. Push the repository to GitHub and configure GitHub Pages to deploy from the branch/root containing these files.
