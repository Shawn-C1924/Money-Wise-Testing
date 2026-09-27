# MoneyWise PWA v0.48

Personal budgeting and savings planning PWA.

## v0.48 architecture refactor

This release begins an incremental JavaScript restructure without changing the existing financial model or deployment approach.

- `index.html` is the PWA shell.
- `css/app.css` contains application styling.
- `js/config.js` centralizes version metadata.
- `js/calculations/Projections.js` contains the projection engine.
- `js/app.js` continues coordinating the existing application while further modules are extracted in later iterations.

See `docs/ARCHITECTURE.md` and `CHANGELOG.md` for the staged migration plan.

## Deployment

The project remains static and is designed for GitHub Pages. Push the repository contents to the configured Pages branch/root and open the Pages URL in Safari. The PWA can then be added to the iPhone Home Screen.
