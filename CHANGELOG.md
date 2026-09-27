# MoneyWise Changelog

## [0.48.0] - Modular architecture, iteration 1

### Added
- Extracted the PWA shell into `index.html`.
- Moved all existing styles into `css/app.css`.
- Moved the working application runtime into `js/app.js`.
- Added `js/config.js` as the single application-version/config boundary.
- Added the first `ProjectionEngine` module boundary for the next calculation extraction pass.
- Added architecture documentation and diagram.

### Changed
- Preserved the v0.47 application behaviour while restructuring the file layout.
- Service-worker cache bumped to v048.
- Saved-data loader now accepts the v0.48 schema during migration.

### Refactor iterations
1. **0.48 — Safe extraction:** separate HTML, CSS, application runtime, configuration, and calculation boundary without changing financial behaviour.
2. **Next — Domain models:** extract PayHistory, AllowanceHistory, Wallets, Transactions, Budget and Plan state.
3. **Next — Financial engines:** move pay periods, projections, allowance assignment and savings calculations into dedicated modules.
4. **Next — Screens/components:** isolate Home, Budget, Cash Flow, Plan and reusable UI components.
5. **Final — Storage/migrations:** isolate persistence, backups and data migrations.
