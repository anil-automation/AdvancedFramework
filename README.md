# Advanced Framework

A Playwright-based end-to-end automation framework written in TypeScript. It includes a Chromium test project, a custom reporter, JSON and Allure reporting, and a GitHub Actions workflow for CI.

## Project structure

```text
.
├── .github/
│   ├── workflows/
│   │   └── playwright.yml      # CI test workflow
├── src/
│   ├── config/                 # Test configuration and data
│   ├── fixtures/               # Shared Playwright fixtures
│   ├── pages/                  # Page objects for the shopping workflow
│   ├── tests/
│   │   ├── e2e-checkout.spec.ts
│   │   └── example.spec.ts
│   └── Utils/
│       ├── CustomTTAReporter.ts
│       ├── DataGenerator.ts
│       ├── Logger.ts
│       └── UtiliElementLocators.ts
├── .gitignore
├── package.json                # Scripts and dependencies
├── playwright.config.ts        # Playwright projects and reporters
└── tsconfig.json               # TypeScript compiler options
```

The framework uses shared fixtures, page objects, data-generation and logging utilities, and a custom reporter to support end-to-end checkout tests.

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

The test suite is configured in `playwright.config.ts`, with tests under `src/tests`. The current project targets Chromium using the installed Chrome channel, runs headed with a 1420 × 870 viewport, and runs test files in parallel by default. On CI, retries are enabled and the worker count is limited to one.

Set `BASE_URL` to run against a different environment. By default, tests use `https://app.thetestingacademy.com/playwright/ttacart`.

## Reports

The default Playwright configuration writes an HTML report to `playwright-reporter/`, JSON results to `test-results/results.json`, Allure results to `allure-results/`, and output from the custom reporter. The `test:allure` script runs with line and Allure reporters. The GitHub Actions workflow uploads the HTML report as an artifact.

```sh
npm run report             # Open the configured Playwright HTML report
npm run allure:report      # Generate an Allure report from allure-results
```

## Code quality

```sh
npm run typecheck          # Check TypeScript types
npm run lint               # Run ESLint
```

## Continuous integration

`.github/workflows/playwright.yml` runs on pushes and pull requests targeting `main` or `master`. It installs dependencies and Playwright browsers, runs the test suite, and uploads the Playwright report.
