# MoneyWise Changelog

## v0.48 — Refactor stabilization

- Restored the complete v0.47 runtime as the functional baseline.
- Preserved the existing MoneyWise financial behaviour and UI while beginning the architecture refactor safely.
- Updated the application data version to 0.48 so v0.47 saves migrate forward without being discarded.
- Bumped the service-worker cache to v048.
- Added `architecture.png` showing the target modular JavaScript architecture.
- Added `docs/ARCHITECTURE.md` describing the planned separation of models, financial engines, UI, and storage.
- Added this changelog for iteration-by-iteration tracking.

### Refactor policy

The runtime is intentionally **not** split into multiple JavaScript modules in this iteration. The previous attempt did that too aggressively and caused runtime regressions. Future refactor iterations will move one responsibility at a time and preserve a working build after every iteration.
