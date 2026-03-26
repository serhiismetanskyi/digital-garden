# Client Architecture

## 9.1 Data Fetching

Modern clients separate data fetching from UI rendering. Use a data-fetching
layer, not raw `fetch()` calls scattered in components.

### REST calls

- Use a centralized HTTP client (axios, httpx, ky).
- Define typed request functions per domain.
- Use a query library for cache management.

```ts
// Centralized HTTP client — not scattered fetch() calls
const api = axios.create({ baseURL: "/api/v1" });

export const getUser = (id: string) => api.get<User>(`/users/${id}`);
```

### GraphQL queries

- Apollo Client or TanStack Query with a GraphQL fetch function.
- Normalized client cache: data stored by `__typename + id`. One update
  propagates everywhere.
- Optimistic updates: assume success, update UI immediately, roll back on error.

### gRPC clients

- Generated stubs from `.proto` files.
- Used on mobile (Swift/Kotlin) and Node.js backends, not in browsers
  (use grpc-web proxy).

### WebSocket subscriptions

- Connect once on app load.
- Subscribe to channels/topics.
- Update local state/cache on each received event.

---

## 9.2 State Management

Separate server state from UI state:

| Type             | What it is                       | Tools                         |
| ---------------- | -------------------------------- | ----------------------------- |
| Server state     | Data from API, cached locally    | TanStack Query, SWR, Apollo   |
| UI state         | Modals, tabs, form inputs        | React state, Zustand, Redux   |
| URL state        | Filters, pagination in URL       | Router query params           |
| Persistent state | User prefs in localStorage       | localStorage, IndexedDB       |

Do not put API data in Redux/Zustand. Use a dedicated server-state library. It
handles caching, revalidation, and background refresh automatically.

### Client cache

Cache API responses in memory to avoid redundant requests.

- **TTL:** revalidate after N seconds.
- **Stale-while-revalidate:** show stale data immediately, fetch fresh in
  background.
- **Deduplicate:** if the same query fires twice simultaneously, fire one
  request and share the result.

### Server state sync

After a mutation, invalidate related queries to trigger a refetch:

```
User clicks "Save"
  → PATCH /profile
  → on success → invalidate ["profile", userId]
  → profile query refetches automatically
```

---

## 9.3 Network Optimization

### Request batching

Group multiple related requests into one.

- GraphQL: one query for all needed data.
- REST: `/users/batch?ids=1,2,3` instead of three separate calls.
- Reduces round-trips and total latency.

### Caching layers

| Layer                    | Scope           | Persistence      |
| ------------------------ | --------------- | ---------------- |
| In-memory (TanStack Q.)  | Current session | Lost on refresh  |
| Service Worker cache     | Origin          | Across reloads   |
| HTTP browser cache       | Per URL         | Per Cache-Control |

### Debounce and throttle

- **Debounce:** wait N ms after last call before firing. Use for
  search-as-you-type (avoid API call on every keystroke).
- **Throttle:** fire at most once per N ms. Use for scroll events and window
  resize.

```ts
// Debounce — fire only after user stops typing for 300ms
const searchUsers = debounce((query: string) => {
  queryClient.fetchQuery(["users", query], () => api.get(`/users?q=${query}`));
}, 300);
```

---

## Key Rules

1. Never call `fetch()` directly in a React component. Use a data layer.
2. Do not store server data in Redux/Zustand — use a server-state library.
3. Invalidate cache after mutations; do not manually update nested state trees.
4. Debounce user-input-driven requests. Throttle event-driven ones.
5. Keep the number of active WebSocket subscriptions minimal; unsubscribe on
   component unmount.
