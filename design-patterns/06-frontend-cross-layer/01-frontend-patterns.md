# Frontend Architecture Patterns

This note describes common frontend structures. Text is simple English (B1). Terms stay precise for senior engineers.

## Component-Based Architecture

The UI is built from small, isolated parts. Each part owns its markup, styles, and local logic.

**Principles:**

- **Single responsibility:** one main job per component.
- **Reusability:** components do not depend on one fixed page.
- **Composability:** big screens are built from small pieces.

**Atomic Design levels:**

1. **Atoms** — `Button`, `Input`, `Label`.
2. **Molecules** — `SearchBar` (input + button).
3. **Organisms** — `Header` (logo + nav + search).
4. **Templates** — layout skeleton without real data.
5. **Pages** — template plus real content.

## Container / Presentational Pattern

Split work into two roles:

| Type | Role | Example |
|------|------|---------|
| Presentational | Draw UI; data comes from props | `ProductCard`, `UserAvatar` |
| Container | Load data, hold state, pass props down | `ProductListContainer` |

```tsx
// Presentational — easy to test (pure output from props)
const UserCard = ({ name, email }: { name: string; email: string }) => (
  <div>
    <h2>{name}</h2>
    <p>{email}</p>
  </div>
);

// Container — owns fetching and loading state
const UserCardContainer = ({ userId }: { userId: string }) => {
  const { data } = useQuery(["user", userId], () => fetchUser(userId));
  if (!data) return <Spinner />;
  return <UserCard name={data.name} email={data.email} />;
};
```

## Hooks / Composition API

Move stateful logic into reusable functions. No need for deep class trees.

```tsx
function useUserProfile(userId: string) {
  return useQuery(["user", userId], () => api.get(`/users/${userId}`));
}

const Profile = ({ userId }: { userId: string }) => {
  const { data, isLoading } = useUserProfile(userId);
  if (isLoading) return <Spinner />;
  return <UserCard {...data} />;
};
```

Vue 3 uses the same idea: composables with `ref`, `computed`, and `watch`.

## State Management

| State kind | Typical tool | Rule |
|------------|--------------|------|
| Server state | TanStack Query, SWR | Do not mirror server rows in a global client store by default. |
| UI state | `useState`, Zustand | Keep local when only one subtree needs it. |
| Shared UI | Zustand, Redux | Use when many distant components need the same UI flag. |
| URL state | Router query params | Filters, page number, sort key. |

**Anti-pattern:** one huge Redux store with all server and UI data. Result: wide re-renders and hard reasoning.

## BFF Integration

The frontend team often owns the BFF (Backend for Frontend). The BFF answers one question: “What does this screen need?”

- **No over-fetching:** response fields match the view.
- **No under-fetching:** avoid many small calls for one screen.
- **UI-ready values:** dates, money, and labels formatted for display.

```python
# BFF handler — shape matches the dashboard (Python example)
def get_order_summary(order_id: str) -> dict[str, object]:
    order = order_service.get(order_id)
    return {
        "id": order.id,
        "label": f"Order #{order.short_id}",
        "total_display": format_money(order.total, order.currency),
    }
```

## Short Summary

Use small components, split smart vs dumb when it helps tests, reuse logic with hooks, put server state in async libraries, and let the BFF serve view-shaped JSON.
