# QA & SDET Portfolio

A set of small, working projects that show how I approach quality engineering end to end:
UI and API automation, mobile automation, performance testing, analytics validation, and
reusable AI skills that speed up everyday QA work.

Each project is its own repository with a CI pipeline, a clear README and design notes.
The business apps behind them are proprietary, so every project here is a **clean-room rebuild
on a public demo app or vendor-neutral data**. No real customer data or credentials are used,
and the code projects include a PII check where relevant.

## Projects

| Project | What it shows | Tech |
|---|---|---|
| [**playwright-java-showcase**](https://github.com/Mcube333/playwright-java-showcase) | UI + API test automation framework for an e-commerce site: thread-isolated parallel sessions, API-assisted setup, cross-layer UI-vs-API checks, failure traces and Allure reports | Java 17, Playwright, TestNG, AssertJ, Allure, GitHub Actions, Docker |
| [**appium-java-mobile-showcase**](https://github.com/Mcube333/appium-java-mobile-showcase) | Android automation that runs on a local emulator or LambdaTest real devices with one flag; thread-local drivers, accessibility-id locators, explicit waits only | Java 17, Appium 2 (UiAutomator2), TestNG, Allure, GitHub Actions |
| [**k6-performance-showcase**](https://github.com/Mcube333/k6-performance-showcase) | Performance tests with SLO thresholds that make performance a pass/fail CI gate; smoke, load, stress, spike, soak and breakpoint profiles | k6 (JavaScript), GitHub Actions |
| [**analytics-event-validator**](https://github.com/Mcube333/analytics-event-validator) | Checks analytics tracking against a tracking plan, from a HAR file or live inside Playwright tests; catches PII leaks, missing or renamed events, wrong types and double fires | Java, Maven, Playwright, GitHub Actions |
| [**claude-skills-for-qa**](https://github.com/Mcube333/claude-skills-for-qa) | 19 reusable AI skills for QA work: PRD to test cases, test automation writers, flaky-test debugging, analytics audits, RCA, regression planning and more | Markdown skills, Python helpers |

## How the pieces fit

- **One system, several test layers.** The Playwright (UI + API) and k6 (performance) projects
  test the same public e-commerce API, so functional, API and performance coverage line up.
- **Mobile.** The Appium project covers the Android side with the same engineering patterns:
  stable locators, no sleeps, per-test clean state, failure evidence.
- **Quality of the data, not just the UI.** The analytics validator checks that what the app sends
  to analytics matches the plan and contains no personal data.
- **Speed.** The skills repo captures the repeatable thinking behind this work as reusable skills.

## Engineering practices used across the projects

- Condition-based waits only; no `Thread.sleep` in tests
- Parallel-safe design (thread-local sessions and drivers)
- Failure evidence attached to reports (screenshots, traces, device logs)
- Secrets only from environment variables or CI secrets, never in files
- Automated PII check in CI (Playwright, Appium and analytics projects)
- Multi-environment config with command-line overrides
- CI on the four code projects (GitHub Actions), with readable reports

## Getting started

Each project documents its own run steps. For example:

```bash
git clone https://github.com/Mcube333/playwright-java-showcase.git
cd playwright-java-showcase
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="install chromium"
mvn test -Dsuite=smoke
```

See the README in each repository for prerequisites and options.

## About

I'm Mohammed Mudassir Maniyar, an SDET working on e-commerce quality. My day-to-day work includes:

- Building a production Playwright + Java suite (98 E2E tests) with parallel-safe sessions and CI reporting
- Migrating a mobile suite from Python/Appium on LambdaTest to Java
- Auditing analytics tracking (MoEngage) on a checkout revamp, which led to the event validator in this portfolio

The projects above are clean-room rebuilds of those patterns on public apps.

[LinkedIn](https://linkedin.com/in/mohammed-mudassir03)
