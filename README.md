# ⚡ Laravel CI Workflows

A collection of reusable, high-performance GitHub Actions workflows designed specifically for Laravel applications. Easily automate your testing, coverage reporting, and code quality checks without repeating yourself.

---

## 📊 Workflows

### 🧪 Test Coverage Commenter (`coverage-comment.yml`)

Runs your Pest test suite, generates a detailed coverage report, and posts a clean, sticky comment on your Pull Requests with the coverage percentage and file breakdown.

#### Features
- 🚀 Setup PHP 8.3 with optimized Composer caching
- 🧪 Executes [Pest PHP](https://pestphp.com/) with coverage enabled
- 💬 Formats and posts an interactive coverage summary directly to the PR
- 💾 Automatically uploads Laravel logs (`storage/logs`) on failure

---

## 🛠️ Usage

To use this workflow in your Laravel projects, reference it inside your GitHub Actions workflow configuration (e.g. `.github/workflows/ci.yml`):

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

# Required permissions for the coverage commenter
permissions:
  contents: read
  pull-requests: write

jobs:
  coverage:
    uses: youngmayor/laravel-ci/.github/workflows/coverage-comment.yml@v1
    secrets: inherit
```

> [!IMPORTANT]
> Ensure your target repository allows GitHub Actions to read/write PR contents (`pull-requests: write`). If you are running tests on PRs from forks, note that standard fork restrictions may apply to write tokens.

---

## 📄 License

This repository is open-sourced under the [MIT License](file:///Volumes/Codes/Laravel/Untitled/laravel-ci/LICENSE).
