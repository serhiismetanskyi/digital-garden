# Playwright — Advanced Patterns

## Network Mocking

Intercept requests and return fake data — no real backend needed.

### Mock an API Endpoint

```python
from playwright.sync_api import Page, Route, expect


def test_shows_mocked_users(page: Page):
    # intercept /api/users and return fake data
    def handle_users(route: Route):
        route.fulfill(json=[
            {"id": 1, "name": "Alice"},
            {"id": 2, "name": "Bob"},
        ])

    page.route("**/api/users", handle_users)
    page.goto("/users")
    expect(page.get_by_role("listitem")).to_have_count(2)
```

### Modify Real Response

```python
def test_inject_extra_item(page: Page):
    def add_item(route: Route):
        # fetch real response, then append data
        response = route.fetch()
        data = response.json()
        data.append({"id": 999, "name": "Injected"})
        route.fulfill(response=response, json=data)

    page.route("**/api/items", add_item)
    page.goto("/items")
```

### Block Resources (Speed Up Tests)

```python
# block images, fonts, and analytics to speed up page load
page.route("**/*.{png,jpg,jpeg,gif,svg,woff2}", lambda route: route.abort())
page.route("**/analytics/**", lambda route: route.abort())
```

### HAR Replay

Record network traffic to a HAR file, replay in tests:

```python
context.route_from_har("tests/data/api.har", update=True)   # record once
context.route_from_har("tests/data/api.har", url="**/api/**")  # replay
```

---

## Conftest Configuration

### Base Fixtures

```python
# tests/conftest.py
import pytest
from playwright.sync_api import Page


@pytest.fixture(scope="session")
def browser_context_args(browser_context_args):
    """Override default context options for all tests."""
    return {
        **browser_context_args,
        "viewport": {"width": 1280, "height": 720},
        "ignore_https_errors": True,
    }


@pytest.fixture(scope="function", autouse=True)
def goto_base(page: Page):
    """Navigate to base URL before every test."""
    page.goto("/")
    yield
```

### Custom Device / Multi-User

```python
@pytest.fixture(scope="session")
def browser_context_args(browser_context_args, playwright):
    device = playwright.devices["iPhone 14"]
    return {**browser_context_args, **device}
```

```python
from pytest_playwright.pytest_playwright import CreateContextCallback
from playwright.sync_api import Page, expect


def test_two_users_chat(page: Page, new_context: CreateContextCallback):
    page.goto("/chat")
    page.get_by_label("Message").fill("Hello from A")
    page.get_by_role("button", name="Send").click()

    ctx_b = new_context()
    page_b = ctx_b.new_page()
    page_b.goto("/chat")
    expect(page_b.get_by_text("Hello from A")).to_be_visible()
```

---

## Async API

Use `playwright.async_api` + `pytest-asyncio`. Every sync method has an `await` equivalent.

```bash
uv add --dev pytest-asyncio
```

```python
import pytest
import pytest_asyncio
from playwright.async_api import async_playwright, Browser, Page, expect


@pytest_asyncio.fixture(scope="session")
async def browser():
    async with async_playwright() as pw:
        b = await pw.chromium.launch()
        yield b
        await b.close()


@pytest_asyncio.fixture
async def page(browser: Browser):
    ctx = await browser.new_context()
    page = await ctx.new_page()
    yield page
    await ctx.close()


@pytest.mark.asyncio
async def test_login(page: Page):
    await page.goto("/login")
    await page.get_by_label("Email").fill("alice@test.com")
    await page.get_by_role("button", name="Sign in").click()
    await expect(page).to_have_url("/dashboard")
```

> `resp.ok`, `resp.status`, `resp.headers` — sync properties. `await resp.json()`, `await resp.text()` — async.

---

## CI & Parallel

```toml
[tool.pytest.ini_options]
addopts = "--tracing retain-on-failure --screenshot only-on-failure"
base_url = "http://localhost:8080"
```

```yaml
- name: Install Playwright
  run: uv add --dev pytest-playwright pytest-xdist && playwright install --with-deps chromium
- name: Run E2E
  run: pytest tests/e2e/ --browser chromium -n auto
- name: Upload traces
  if: failure()
  uses: actions/upload-artifact@v4
  with: { name: playwright-traces, path: test-results/ }
```

---

## Debugging

| Technique | How |
|-----------|-----|
| Headed / Slow | `pytest --headed --slowmo 500` |
| Trace viewer | `pytest --tracing on` → `playwright show-trace trace.zip` |
| Screenshot | `page.screenshot(path="debug.png")` |
| Video | `pytest --video retain-on-failure` |
| Breakpoint | `breakpoint()` in test + `pytest -s` |

---

## Best Practices

| Practice | Why |
|----------|-----|
| Mock external APIs with `page.route()` | Stable, fast, no third-party flakiness |
| `--tracing retain-on-failure` in CI | Post-mortem debugging without reproduction |
| `base_url` in config, not in tests | One place to change per environment |
| Parallel via `pytest-xdist` (`-n auto`) | Reduce CI wall time |
