# MoneyWise

MoneyWise is a mobile-first personal budgeting and savings PWA designed for GitHub Pages and iPhone Home Screen use.

## v0.49

This release is a **refactor stabilization release**. The complete v0.47 application runtime is retained so the app remains functional while the new architecture is documented and prepared for incremental migration.

### Target architecture

See:

- `docs/ARCHITECTURE.md` — modular JavaScript design and migration plan
- `architecture.png` — visual architecture diagram
- `CHANGELOG.md` — iteration history

### Deployment

The app remains a static GitHub Pages PWA. No server or database is required. User data remains local to the browser and can be exported through MoneyWise's existing backup system.

## Refactor approach

The target structure separates:

1. Domain models
2. Financial calculation engines
3. Screens and reusable UI components
4. Storage, backup, and migration
5. PWA/bootstrap code

The migration will be incremental. A working application is required after each iteration before another responsibility is moved.


## v0.50 funds model
MoneyWise now treats Bank Savings, Cash Savings, and Pockets as three internal stores of the same savings pool. Funds can be moved between any two stores. Such movements are blue internal transfers and do not change total Current Savings.
