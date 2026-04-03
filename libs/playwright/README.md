# Playwright — Python Browser & API Testing

End-to-end testing framework: UI automation, API testing, network mocking, cross-browser support.

## Installation

```bash
uv add --dev pytest-playwright
playwright install  # downloads browser binaries (Chromium, Firefox, WebKit)
```

## Section Map

| File | Topics |
|------|--------|
| [01 UI Testing](./01-ui-testing.md) | Locators, actions, assertions, auto-waiting, fixtures, isolation |
| [02 API Testing](./02-api-testing.md) | APIRequestContext, HTTP methods, auth, mixed UI+API flows |
| [03 Page Objects](./03-page-objects.md) | POM pattern, component objects, best practices |
| [04 Advanced Patterns](./04-advanced-patterns.md) | Network mocking, conftest config, async API, CI, debugging |
| [05 UI Playbook](./05-ui-playbook.md) | Auth state, forms, downloads, dialogs, tables, multi-tab, screenshots |
| [06 API Playbook](./06-api-playbook.md) | CRUD lifecycle, schema validation, errors, pagination, headers, uploads |

## Quick Commands

| Command | Use |
|---------|-----|
| `pytest` | Run all tests (headless) |
| `pytest --headed` | Run with visible browser |
| `pytest --browser firefox` | Run on specific browser |
| `pytest --browser chromium --browser firefox` | Cross-browser |
| `pytest --slowmo 500` | Slow down actions by 500ms |
| `pytest --tracing on` | Record trace for each test |
| `pytest --screenshot only-on-failure` | Capture on failure |
| `pytest --video retain-on-failure` | Record video on failure |
| `pytest -n auto` | Parallel via pytest-xdist |
| `pytest --base-url http://localhost:8080` | Set base URL |

## Locator Cheat Sheet

| Priority | Locator | Example |
|----------|---------|---------|
| 1 | `get_by_role` | `page.get_by_role("button", name="Submit")` |
| 2 | `get_by_label` | `page.get_by_label("Email")` |
| 3 | `get_by_placeholder` | `page.get_by_placeholder("Search...")` |
| 4 | `get_by_text` | `page.get_by_text("Welcome back")` |
| 5 | `get_by_test_id` | `page.get_by_test_id("login-form")` |
| 6 | CSS/XPath | `page.locator(".btn-primary")` (last resort) |

## Assertion Cheat Sheet

```python
from playwright.sync_api import expect

# page-level
expect(page).to_have_title(re.compile("Dashboard"))
expect(page).to_have_url("https://example.com/dashboard")

# element-level
expect(locator).to_be_visible()
expect(locator).to_be_enabled()
expect(locator).to_have_text("Success")
expect(locator).to_contain_text("created")
expect(locator).to_have_attribute("href", "/home")
expect(locator).to_have_count(3)
expect(locator).to_have_value("alice@example.com")
expect(locator).to_be_checked()
```

## Built-in Fixtures (pytest-playwright)

| Fixture | Scope | Purpose |
|---------|-------|---------|
| `page` | function | Fresh page per test |
| `context` | function | Browser context (cookies, storage) |
| `browser` | session | Browser instance |
| `playwright` | session | Playwright instance |
| `new_context` | function | Create additional contexts (multi-user) |

## Quick Rules

1. **Use `get_by_role` first** — resilient, accessible, user-facing.
2. **Never use `time.sleep`** — Playwright auto-waits for elements.
3. **Use `expect()` assertions** — auto-retry until condition met.
4. **One behavior per test** — isolated, independent tests.
5. **Page Object Model** for real projects — maintainable locators.
6. **Mock external APIs** — `page.route()` for stability and speed.
7. **Trace on failure** — `--tracing retain-on-failure` for debugging.
