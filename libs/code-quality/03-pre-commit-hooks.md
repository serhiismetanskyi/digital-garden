# Pre-Commit Hooks

Run linters, formatters, and type checkers automatically on every `git commit`.

## Install

```bash
uv add --dev pre-commit
uv run pre-commit install           # activate hooks in repo
uv run pre-commit run --all-files   # manual run on everything
```

---

## `.pre-commit-config.yaml`

```yaml
repos:
  # --- General file hygiene ---
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v5.0.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-toml
      - id: check-added-large-files
        args: [--maxkb=500]
      - id: detect-private-key
      - id: check-merge-conflict

  # --- Ruff (lint → format) ---
  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.15.8
    hooks:
      - id: ruff-check
        args: [--fix]
      - id: ruff-format

  # --- mypy ---
  - repo: https://github.com/pre-commit/mirrors-mypy
    rev: v1.15.0
    hooks:
      - id: mypy
        additional_dependencies:
          - types-requests
          - types-PyYAML
          - pydantic

  # --- wemake-python-styleguide ---
  - repo: https://github.com/PyCQA/flake8
    rev: "7.3.0"
    hooks:
      - id: flake8
        args: [--select=WPS]
        additional_dependencies:
          - wemake-python-styleguide
```

---

## Hook Ordering Rules

1. **`ruff-check --fix`** first — auto-fixes imports, unused vars, etc.
2. **`ruff-format`** second — reformats code after linter changes.
3. **`mypy`** third — type-checks the clean code.
4. **`flake8 --select=WPS`** last — strictness layer.

---

## Key Commands

```bash
uv run pre-commit run --all-files     # check all files
uv run pre-commit autoupdate          # update hook versions
uv run pre-commit run ruff-check      # run single hook
SKIP=mypy git commit -m "wip"         # skip specific hook once
```

---

## CI Integration (GitHub Actions)

```yaml
steps:
  - uses: actions/checkout@v4
  - uses: astral-sh/setup-uv@v5
    with:
      enable-cache: true
  - run: uv sync --locked
  - run: uv run pre-commit run --all-files
```

---

## Common Issues

| Problem | Fix |
|---------|-----|
| mypy can't find third-party types | Add stubs to `additional_dependencies` |
| Hook fails on generated files | Add `exclude` pattern to the hook |
| Slow mypy in pre-commit | Use `pass_filenames: false` + `--incremental` |
| Ruff version mismatch | Pin same version in `.pre-commit-config.yaml` and `pyproject.toml` |

---

## Skip vs Commit Hooks in CI

| Strategy | Pre-commit | CI Pipeline |
|----------|-----------|-------------|
| Purpose | Catch issues before commit (dev machine) | Gate before merge (server) |
| Speed | Must be fast (seconds) | Can be thorough (minutes) |
| Scope | Changed files only | Full repo |

Run the same tools in both; pre-commit catches early, CI catches everything.
