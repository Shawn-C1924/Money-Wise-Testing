# MoneyWise Architecture

MoneyWise remains a plain JavaScript PWA. No framework is required and GitHub Pages remains the deployment target.

## Current structure — Iteration 1

```text
MoneyWise/
├── index.html                 # PWA shell
├── manifest.webmanifest
├── sw.js                      # offline/cache layer
├── css/
│   └── app.css                # all application styles
├── js/
│   ├── config.js              # version/cache metadata
│   ├── projections.js         # projection/calculation engine
│   └── app.js                  # current application coordinator
├── architecture.png           # architecture + evolution diagram
├── CHANGELOG.md
└── README.md
```

## Responsibility rule

The long-term rule is:

```text
UI → asks for data
Domain → defines financial data
Calculations → computes financial results
Storage → persists data
App coordinator → wires everything together
```

A screen should not independently calculate theoretical max, allowance history, pay periods, or savings projections.

## Why the projection engine is first

Projection logic has become the most interconnected part of MoneyWise. It depends on:

- start/end dates
- payday rules
- salary history
- paycheck count
- allowance history
- budget costs
- actual transactions
- wallets and transfers
- target calculations

Giving this logic one home means a change to a projection can be made and tested in one file instead of searching the whole application.

## GitHub Pages workflow

The application intentionally stays framework-free:

```text
Edit files → Commit → Push to GitHub → GitHub Pages → Safari → iPhone Home Screen
```

There is no server-side database requirement. User data remains in the browser and can be exported through MoneyWise's backup system.
