# Advanced Framework

A Playwright-based end-to-end automation framework written in TypeScript. It includes a Chromium test project, a custom reporter, JSON and Allure reporting, and a GitHub Actions workflow for CI.

## Project structure

```text
.
├── .agent/
│   └── rules/                  # Agent guidance
├── .cursor/
│   └── rules/                  # Cursor guidance
├── .github/
│   ├── workflows/
│   │   └── playwright.yml      # CI test workflow
│   └── copilot-instructions.md # Copilot guidance
├── .windsurf/
│   └── rules/                  # Windsurf guidance
├── DokcerFile/
│   └── .gitkeep                # Empty directory placeholder
├── docs/
│   └── Phase One/
│       └── prompts.md          # Captured Phase One request
├── Rule/
│   └── README.md               # Test-file validation guidance
├── src/
│   ├── api/                    # API helpers (placeholder)
│   ├── config/                 # Test/framework configuration (placeholder)
│   ├── fixtures/               # Shared Playwright fixtures (placeholder)
│   ├── pages/                  # Page objects (placeholder)
│   ├── testdata/               # Test data (placeholder)
│   ├── tests/
│   │   └── example.spec.ts     # Example end-to-end tests
│   └── Utils/
│       └── CustomReportet.ts   # Custom Playwright reporter
├── .gitignore
├── package.json                # Scripts and dependencies
├── package-lock.json
├── playwright.config.ts        # Playwright projects and reporters
└── tsconfig.json               # TypeScript compiler options
```

The `src/api`, `src/config`, `src/fixtures`, `src/pages`, and `src/testdata` directories currently contain only `.gitkeep` placeholders so the framework layout is preserved in Git. Add the corresponding helpers, fixtures, page objects, and data as the project grows.

## Prerequisites

- Node.js 18 or newer
- npm
- A supported browser installed through Playwright

Install dependencies and the Playwright browser:

```sh
npm ci
npm run install:browsers
```

## Running tests

```sh
npm test                 # Run the Playwright test suite
npm run test:headed       # Run with a visible browser
npm run test:debug        # Run with the Playwright debugger
npm run test:ui           # Open Playwright UI mode
npm run test:chrome       # Run the Chromium project
npm run test:allure       # Run tests with line and Allure reporters
```

The test suite is configured in `playwright.config.ts`, with tests under `src/tests`. The current project targets Chromium using the installed Chrome channel.

## Reports

The Playwright configuration writes an HTML report to `playwright-reporter/`, JSON results to `test-results/results.json`, and Allure results to `allure-results/`. The GitHub Actions workflow uploads the Playwright report as an artifact.

```sh
npm run report             # Open the configured Playwright HTML report
npm run allure:report      # Generate an Allure report from allure-results
```

## Continuous integration

`.github/workflows/playwright.yml` runs on pushes and pull requests targeting `main` or `master`. It installs dependencies and Playwright browsers, runs the test suite, and uploads the Playwright report.
