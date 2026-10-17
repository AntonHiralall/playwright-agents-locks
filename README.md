# Playwright Agents, Locks & Allure

Minimal TypeScript/Playwright demo framework with:

- **Heuristic agents** — Planner, Generator, Healer (+ Runner executor; no LLM)
- **File-based test locks** — exclusive resource mutex for parallel runs
- **Allure reporting** — agent recovery steps and lock metadata in the HTML report

**New here?** Start with [Getting started](docs/GETTING_STARTED.md).

## Prerequisites

- Node.js 20+
- Chromium (installed via Playwright)

## Setup

```bash
npm install
npx playwright install chromium
```

## Run tests

```bash
npm test
npm run test:headed
```

## CI

GitHub Actions runs Chromium Playwright tests on every push to `main` and on every pull request (workflow: [`.github/workflows/ci.yml`](.github/workflows/ci.yml)).

1. Open the repo on GitHub → **Actions** tab → select the **CI** workflow run.
2. Download the **test-and-allure-artifacts** artifact from the run summary (includes `allure-report/`, `allure-results/`, and `test-results/` when present).
3. Unzip and open `allure-report/index.html` locally to view the report.

No secrets are required for v1.

## Allure report

```bash
npm test
npm run allure:generate
npm run allure:open
```

Generate and open in one command:

```bash
npm run allure:serve
```

Or run tests then open the report:

```bash
npm run report
```

## Project layout

| Path | Purpose |
|------|---------|
| `src/agents/` | Planner, Healer, Runner agents |
| `src/locks/` | File-based lock manager |
| `src/allure/` | Allure step/attachment helpers |
| `fixtures/demo-app/` | Local HTML demo pages |
| `tests/demo.spec.ts` | Self-healing + concurrent lock demos |
| `docs/GETTING_STARTED.md` | Newbie-friendly overview |
| `docs/ARCHITECTURE.md` | System design |
| `docs/AGENT_SPEC.md` | Agent I/O and recovery rules |

## Docs

- [Getting started](docs/GETTING_STARTED.md)
- [Demo report script](docs/DEMO_REPORT_SCRIPT.md) — walkthrough of Agents & Locks in Allure
- [Architecture](docs/ARCHITECTURE.md)
- [Agent specification](docs/AGENT_SPEC.md)
