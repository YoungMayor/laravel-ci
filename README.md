# ⚡ Laravel CI Workflows

A collection of reusable, high-performance GitHub Actions workflows designed specifically for Laravel applications. Easily automate your testing, coverage reporting, code quality checks, and deployment pipelines.

---

## 📦 Available Workflows

| Workflow | Description | File Path |
| :--- | :--- | :--- |
| **🧪 Test Coverage Commenter** | Runs Pest tests, generates coverage reports, and posts sticky comments on PRs. | [coverage-comment.yml](file:///.github/workflows/coverage-comment.yml) |

---

## 🚀 Getting Started

To use these workflows in your repository, reference them in your workflow files (e.g. `.github/workflows/ci.yml`):

### Example: Test Coverage Commenter

```yaml
name: CI

on:
  pull_request:
    branches: [ main ]

permissions:
  contents: read
  pull-requests: write

jobs:
  coverage:
    uses: youngmayor/laravel-ci/.github/workflows/coverage-comment.yml@v1
    secrets: inherit
```

---

## 🛠️ Individual Workflow Reference

### 🧪 Test Coverage Commenter (`coverage-comment.yml`)

Runs your Pest test suite, parses coverage, and posts an interactive summary directly to the PR comments.

#### Configuration Options

You can pass customizable inputs under the `with` block:

| Input | Description | Default |
| :--- | :--- | :--- |
| `php-version` | PHP version to setup. | `8.3` |
| `php-extensions` | Additional PHP extensions to install. | `dom, curl, libxml, ...` |
| `test-command` | The command to run tests and coverage. | `./vendor/bin/pest --ci --coverage` |
| `coverage-driver` | PHP extension for coverage. | `pcov` (much faster than `xdebug`) |
| `min-coverage` | Target minimum coverage percentage. | `0` |
| `fail-on-low-coverage` | Fail build if coverage is below target. | `false` |
| `build-assets` | Build assets before tests. | `false` |
| `asset-build-command` | Install + build command (auto-detects npm, yarn, pnpm, bun if set to `auto`). | `auto` |
| `node-version` | Node version to use for asset builds. | `20` |

Example with inputs:
```yaml
jobs:
  coverage:
    uses: youngmayor/laravel-ci/.github/workflows/coverage-comment.yml@v1
    with:
      min-coverage: 80
      fail-on-low-coverage: true
      build-assets: true
    secrets: inherit
```

#### Requirements
- **Test Framework**: Pest PHP (or PHPUnit configured via `test-command`)
- **Permissions**: Requires `pull-requests: write` and `contents: read` permissions.

> [!NOTE]
> For PRs from external forks, GitHub downgrades the `GITHUB_TOKEN` to read-only for security reasons. As a result, the sticky comment step will be skipped or fail for external fork PRs unless using `pull_request_target` (which should be done with caution).

---

## 📄 License

This repository is open-sourced under the [MIT License](file:///Volumes/Codes/Laravel/Untitled/laravel-ci/LICENSE).
