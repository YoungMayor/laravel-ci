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

#### Requirements
- **Test Framework**: Pest PHP
- **Permissions**: Requires `pull-requests: write` and `contents: read` permissions.

> [!NOTE]
> For PRs from external forks, GitHub downgrades the `GITHUB_TOKEN` to read-only for security reasons. As a result, the sticky comment step will be skipped or fail for external fork PRs unless using `pull_request_target` (which should be done with caution).

---

## 📄 License

This repository is open-sourced under the [MIT License](file:///Volumes/Codes/Laravel/Untitled/laravel-ci/LICENSE).
