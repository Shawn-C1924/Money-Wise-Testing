# MoneyWise Changelog

## [0.48.0] — 2026-09-28 — Architecture Refactor, Iteration 1

### Added
- Introduced a dedicated `js/calculations/projections.js` financial projection engine.
- Added `js/config.js` so application/cache versioning has a single source of truth.
- Moved all inline CSS into `css/app.css`.
- Added architecture documentation and the staged refactor roadmap.
- Added an architecture diagram covering the current structure and intended future iterations.

### Changed
- `index.html` is now primarily the PWA shell and asset entry point.
- Projection functions in the application now delegate to the projection engine rather than owning the calculation implementation.
- Service-worker caching now includes the extracted CSS and JavaScript files.
- Version is now defined centrally instead of being duplicated in the application and cache configuration.

### Preserved
- Existing v0.47 financial behaviour and saved-data format.
- Existing UI, themes, wallets, pay history, allowance history, pay-period logic, backups/import/export, and PWA deployment model.

### Refactor principle
The refactor is intentionally incremental. Each iteration should move one responsibility into a clear module while preserving behaviour. No feature should be rewritten merely because its file moved.

---

## Refactor roadmap

### Iteration 0 — Legacy monolith (v0.47)
- Large inline script in `index.html`.
- Financial rules, UI rendering, storage, and helpers lived together.
- Hard to locate a single financial rule and easy for changes to affect unrelated screens.

### Iteration 1 — Application shell + calculation boundary (v0.48)
- `index.html` becomes a shell.
- `css/app.css` owns styling.
- `js/app.js` remains the application coordinator for now.
- `js/calculations/projections.js` owns theoretical max, projected finish, essentials-only, pay-rate projection, and allowance auto-assignment calculations.
- `js/config.js` owns version metadata.

### Iteration 2 — Domain model extraction
Planned modules:
- `js/models/PayHistory.js`
- `js/models/AllowanceHistory.js`
- `js/models/Budget.js`
- `js/models/Wallet.js`
- `js/models/Transaction.js`
- `js/models/Plan.js`

The goal is for these modules to define the application's data concepts without rendering UI.

### Iteration 3 — Financial engines
Planned modules:
- `js/calculations/PayPeriods.js`
- `js/calculations/Financials.js`
- `js/calculations/Projections.js`
- `js/calculations/Allowance.js`

The goal is for every calculation to have one authoritative implementation.

### Iteration 4 — Storage and migration
Planned modules:
- `js/storage/State.js`
- `js/storage/Backup.js`
- `js/storage/Migration.js`

The goal is to isolate localStorage, JSON backup/import, schema migration, and automatic backup behaviour.

### Iteration 5 — Screens and reusable components
Planned modules:
- `js/screens/Home.js`
- `js/screens/Budget.js`
- `js/screens/CashFlow.js`
- `js/screens/Plan.js`
- `js/components/Card.js`
- `js/components/Modal.js`
- `js/components/Toggle.js`
- `js/components/Navigation.js`

The goal is for screens to ask the financial/domain layers for data rather than calculating it themselves.

### Iteration 6 — Final application coordinator
`js/app.js` should eventually become a small coordinator responsible for:
- startup
- navigation
- wiring events
- rendering screens
- connecting the domain, calculation, and storage layers

It should not contain the financial rules themselves.
