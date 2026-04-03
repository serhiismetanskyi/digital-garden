# CI/CD Integration

## Pipeline Design Principles

Tests in CI must be:
- **Fast** — fast feedback prevents context switching
- **Reliable** — false positives kill trust in the pipeline
- **Informative** — failures must point to root cause immediately

---

## Pipeline Stages

```
Push / PR
    │
    ▼
[1] Lint & Type Check    (ruff, mypy) — ~30s
    │
    ▼
[2] Unit Tests           (-m unit, no I/O) — ~1 min
    │
    ▼
[3] Integration Tests    (-m integration) — ~3 min
    │
    ▼
[4] API Tests            (-m api) — ~5 min
    │
    ▼
[5] Smoke E2E            (-m smoke and e2e) — ~3 min
    │
    ▼
[6] Report & Publish     (Allure, coverage badge)
```

Each stage gates the next. Linting failures block all test stages.

---

## GitHub Actions Example

{% raw %}
```yaml
name: Test Suite

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: astral-sh/setup-uv@v3
      - run: uv run ruff check .
      - run: uv run mypy .

  unit-tests:
    needs: lint
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: astral-sh/setup-uv@v3
      - run: uv run pytest -m unit -n auto --junitxml=test-results/junit.xml
      - uses: actions/upload-artifact@v4
        if: always()
        with:
          name: unit-test-results
          path: test-results/

  api-tests:
    needs: unit-tests
    runs-on: ubuntu-latest
    env:
      TEST_ENV: staging
      TEST_API_TOKEN: ${{ secrets.STAGING_API_TOKEN }}
    steps:
      - uses: actions/checkout@v4
      - uses: astral-sh/setup-uv@v3
      - run: |
          uv run pytest -m api -n auto \
            --timeout=60 \
            --reruns=2 \
            --junitxml=test-results/junit.xml \
            --alluredir=test-results/allure-results
      - uses: actions/upload-artifact@v4
        if: always()
        with:
          name: api-test-results
          path: test-results/

  e2e-smoke:
    needs: api-tests
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: astral-sh/setup-uv@v3
      - run: uv run playwright install chromium --with-deps
      - run: |
          uv run pytest -m "smoke and e2e" \
            --timeout=90 \
            --junitxml=test-results/e2e-junit.xml
      - uses: actions/upload-artifact@v4
        if: always()
        with:
          name: e2e-results
          path: test-results/
```
{% endraw %}

---

## Quality Gates

Gates prevent merging code that degrades test quality.

| Gate | Threshold | Action on Fail |
|------|-----------|---------------|
| Test pass rate | 100% (excluding quarantined) | Block merge |
| Coverage | ≥ 90% (unit), ≥ 80% (integration) | Block merge |
| Flakiness reruns | ≤ 2% of total tests | Warning |
| E2E duration | ≤ 5 min for smoke suite | Warning |

### Coverage Gate

```bash
uv run pytest --cov=src --cov-fail-under=90 -m "unit or integration"
```

### Coverage Badge in README

```yaml
- name: Generate coverage badge
  run: |
    uv run coverage-badge -o coverage.svg -f
```

---

## Pre-Commit Integration

Catch issues before push — saves CI time:

```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.4.0
    hooks:
      - id: ruff
      - id: ruff-format

  - repo: local
    hooks:
      - id: unit-tests
        name: Unit Tests
        entry: uv run pytest -m unit -q
        language: system
        pass_filenames: false
```

---

## Nightly Full Suite

{% raw %}
```yaml
name: Nightly Full Regression

on:
  schedule:
    - cron: "0 2 * * *"  # 02:00 UTC daily

jobs:
  full-regression:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: astral-sh/setup-uv@v3
      - run: uv run playwright install --with-deps
      - run: |
          uv run pytest -n auto \
            --timeout=120 \
            --reruns=1 \
            --alluredir=test-results/allure
      - name: Notify on failure
        if: failure()
        uses: slackapi/slack-github-action@v1
        with:
          payload: '{"text":"Nightly regression failed: ${{ github.run_url }}"}'
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK }}
```
{% endraw %}
