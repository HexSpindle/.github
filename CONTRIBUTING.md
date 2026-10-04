# Contributing to HexSpindle

Thank you for your interest in contributing to HexSpindle.

HexSpindle is a browser-based data transformation workbench built with vanilla JavaScript and browser APIs. Contributions to the application, operations, documentation, tests, and project infrastructure are welcome.

## Before You Start

For significant changes or new features, consider opening an issue first so the proposed approach can be discussed before substantial work is done.

For security vulnerabilities, do not open a public issue. Please follow the [Security Policy](SECURITY.md).

## Development Setup

Clone the main repository:

```bash
git clone https://github.com/HexSpindle/HexSpindle.git
cd HexSpindle
```

HexSpindle does not require a build step for normal application development. The application source is served directly to the browser.

Development and CI tooling is located in the `tools/` directory.

Install the tooling dependencies with:

```bash
cd tools
npm ci
```

## Project Structure

The main application is organized as follows:

```text
HexSpindle/
├── core/               Core engine, registry, codecs, and shared utilities
├── modules/            Transformation and analysis operations
├── tools/              Development and CI tooling
├── app.js              Main browser application logic
├── app.css             Application styling
├── index.html          Application entry point
└── .github/            Repository-specific GitHub configuration
```

Operations are organized by category under:

```text
modules/<category>/
```

## Adding or Removing Operations

When adding, removing, or renaming operation files, regenerate `modules/index.js`.

From the repository root:

```bash
node tools/gen-index.mjs
```

`modules/index.js` is generated automatically and should not be edited by hand.

After regeneration, review the resulting diff before committing it.

## Testing

HexSpindle uses a Playwright-based browser smoke test.

From the `tools/` directory:

```bash
npm ci
npx playwright install chromium
node ci-smoke.mjs
```

GitHub Actions also runs the smoke test automatically for pushes and pull requests.

A pull request should not intentionally break the existing CI workflow.

## Contribution Guidelines

Please keep contributions focused and easy to review.

When submitting changes:

- Keep unrelated changes out of the same pull request.
- Follow the existing project structure and coding style.
- Prefer browser-native APIs where practical.
- Avoid introducing dependencies unless they provide a clear benefit.
- Do not commit `node_modules/`, browser binaries, editor files, or other generated local artifacts.
- Do not commit API keys, tokens, credentials, private keys, or other secrets.
- Update documentation when behavior or user-facing functionality changes.
- Regenerate `modules/index.js` when operation files change.
- Verify that existing functionality still works before submitting the pull request.

## Commit Messages

Use concise commit messages that describe the change.

Examples:

```text
Add GitHub link to application header
Fix Base64 decoding edge case
Add operation for XYZ transformation
Improve browser smoke test coverage
```

## Pull Requests

When opening a pull request:

1. Describe what the change does.
2. Explain why the change is needed.
3. Include relevant testing details.
4. Reference related issues where applicable.
5. Include screenshots for meaningful user-interface changes when useful.

Pull requests may be reviewed for correctness, maintainability, security, browser compatibility, and consistency with the goals of HexSpindle.

## Reporting Bugs

Please use the issue tracker in the [HexSpindle source repository](https://github.com/HexSpindle/HexSpindle/issues).

Include enough information to reproduce the problem, such as:

- What you expected to happen
- What actually happened
- Steps to reproduce the issue
- Browser and operating system
- Relevant input, recipe, or operation
- Screenshots or console errors when useful

Do not include sensitive or private information in public issues.

## Feature Requests

Feature requests are welcome through the [HexSpindle issue tracker](https://github.com/HexSpindle/HexSpindle/issues).

Please describe the use case as well as the requested functionality.

## License

By contributing to HexSpindle, you agree that your contributions will be licensed under the same license as the project.
