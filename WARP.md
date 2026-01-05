# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project overview

This repository is a minimal Node.js (CommonJS) project used to experiment with CI/CD using GitHub Actions.

- Entry point: `index.js` – prints simple messages to stdout.
- Basic "tests": `test.js` – a small script that logs messages and simulates a delay.
- CI pipeline: `.github/workflows/pipeline.yaml` – GitHub Actions workflow that checks out the code, sets up Node.js, installs dependencies, and runs tests on pushes to the `main` branch.

## Commands

All commands below are intended to be run from the repository root.

- Install dependencies (required before running or testing):
  - `npm install`

- Run the application locally (uses the `run` script):
  - `npm run run`
  - Equivalent direct invocation: `node index.js`

- Run the current tests (executes `test.js`):
  - `npm test`
  - This runs the script defined in `package.json`: `node test.js`.

- Run a single test file:
  - There is only one test entrypoint (`test.js`). Running `npm test` executes all test logic.
  - No test framework (e.g., Jest, Mocha) is configured, so there is no built-in mechanism for running individual test cases.

## Code structure

- `index.js`
  - Simple console-based script that outputs informational messages.
  - Can be extended with actual application logic if this project grows.

- `test.js`
  - Console-based script acting as a minimal test harness.
  - Uses `setTimeout` to demonstrate asynchronous behavior and timing.

- `.github/workflows/pipeline.yaml`
  - Defines a single `build` job that runs on `ubuntu-latest` for pushes to `main`.
  - Key steps:
    - `actions/checkout@v5` – checks out the repository.
    - `actions/setup-node@v3` with `node-version: 16` – configures Node.js.
    - Install dependencies step currently runs `npm Install`.
    - Test step currently runs `npm text`.
  - The install/test commands in the workflow appear intended to be `npm install` and `npm test`, but are currently spelled differently; if the workflow fails, these commands are the first place to check.
