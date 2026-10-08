# MoneyWise Changelog

## v0.50
- Added a unified three-way internal funds transfer system: Bank Savings ↔ Cash Savings ↔ Pockets.
- Added a single **Move funds** action from savings areas instead of limiting transfers to Bank ↔ Cash.
- Pocket-to-bank, pocket-to-cash, bank-to-pocket, cash-to-pocket, and bank ↔ cash transfers are all treated as internal blue movements.
- Internal transfers do not change Total / Current Savings because the money remains owned by the user.
- Transfer transactions store both source and destination so deletion and whole-period deletion can reverse the movement correctly.
- Existing legacy Bank ↔ Cash transfer records remain supported.

## v0.49 — Savings sources, pockets & allowance/paycheck corrections

- Fixed Theoretical Max presentation with a clear formula hint and retained the detailed info breakdown.
- Added rename controls for built-in Budget sections as well as existing custom-section renaming.
- Fixed manual `Set allowance` so the effective date defaults to the start of the current pay period and the displayed current allowance updates immediately.
- Added a current-period-only allowance override accessible from Home and Cash Flow; it feeds Projected Finish without rewriting historical/future allowance rules.
- Corrected Auto Assign to size allowance from the configured number of paychecks per year rather than dividing income by 12.
- Added Bank savings and Cash savings balances to Current Savings, with an editor and Bank ↔ Cash transfer action.
- Added Bank/Cash source selection for spending and Bank/Cash destination selection for income.
- Pocket spending reduces the selected pocket and total Current Savings but does not count against allowance spending.
- Pocket funding is treated as an internal movement: Bank savings decreases while the pocket increases, leaving total Current Savings unchanged.
- Removed the Extra paychecks UI from Cash Flow; paycheck-count logic remains available to calculations and automatic pay scheduling.
- Renamed the user-facing Wallet concept to **Pockets** while preserving existing storage keys for migration compatibility.
- Bumped data version and service-worker cache to v0.49.

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
