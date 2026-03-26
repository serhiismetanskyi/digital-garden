# Architectural Patterns: Microservices, Event-Driven, Isomorphic

## Microservices

Each domain is a separate service: its own codebase, deployment, and data store.
Services communicate via API (sync) or events (async).

**Service boundaries:** define by bounded context (Domain-Driven Design).
One service = one subdomain. Payment service does not share a DB with Order service.

**Communication patterns:**

| Pattern | When to use |
|---|---|
| REST / gRPC (sync) | Caller needs an immediate response |
| Async events | Side effects that can happen later |

```
Order Service publishes "order.placed" → Kafka
Payment Service consumes event → charges card
Fulfillment Service consumes event → prepares shipment
```

**Testing:**
- **Contract testing:** verify producer and consumer agree on event shape (Pact).
- **Integration testing:** spin up real dependencies with testcontainers.

**Risks:** partial failures, eventual consistency, distributed complexity.
Design for failure: timeout + circuit breaker + retry on every service call.

---

## Event-Driven Architecture

Services communicate by publishing and consuming events.
No direct synchronous calls for non-critical flows.

**Key characteristics:**
- Producer publishes event to a broker (Kafka, RabbitMQ, SQS).
- Consumer receives and processes at its own pace.
- Producer does not know who consumes or when.

**Event consistency patterns:**

**Outbox pattern:** write event to DB in the same transaction as the state change.
A relay process reads the outbox and publishes to the broker.
Prevents lost events if the service crashes after DB write but before publish.

```python
def place_order(order_id: str, amount: float, db) -> None:
    # Both writes are in one DB transaction — atomic
    db.execute(
        "INSERT INTO orders (id, amount) VALUES (?, ?)",
        (order_id, amount),
    )
    db.execute(
        "INSERT INTO outbox (event_type, payload) VALUES (?, ?)",
        ("order.placed", f'{{"order_id": "{order_id}"}}'),
    )
    db.commit()
    # Separate relay process reads outbox and publishes to Kafka
```

**Idempotency:** consumers must handle duplicate events safely.
Store processed event IDs and skip already-processed ones.

```python
def handle_order_placed(event_id: str, order_id: str, db) -> None:
    if db.scalar("SELECT 1 FROM processed_events WHERE id=?", (event_id,)):
        return  # already processed — skip
    # ... process ...
    db.execute("INSERT INTO processed_events (id) VALUES (?)", (event_id,))
    db.commit()
```

---

## Isomorphic / Universal Architecture

Code runs on both server and client without modification.

**Shared scope:**

| Feature | How |
|---|---|
| SSR + CSR | Server renders initial HTML (fast first paint, SEO). Client hydrates for interaction. |
| Shared validation | Pydantic (server) + Zod (client) mirror each other, or generate both from JSON Schema. |
| Shared types | TypeScript types shared via a monorepo package (tRPC, OpenAPI codegen). |

**Hydration:** server renders HTML → browser loads JS → React/Vue attaches
event listeners to existing DOM. If server HTML and client virtual DOM differ,
you get a hydration mismatch error.

**Challenges:**

- Browser-only APIs (`localStorage`, `window`, `document`) are not available
  on the server. Guard: `if typeof window !== "undefined"`.
- Server-only secrets must not be included in client bundles.
- Requires two build targets: Node.js (server) and browser (client).

**Testing:**
- **Hydration correctness:** verify server-rendered HTML matches client
  virtual DOM on first render.
- **Environment-specific:** run the same logic test in both Node.js and
  browser environments to catch divergence.

**Frameworks:** Next.js, Remix, SvelteKit, Nuxt.js — all built on this model.

---

## Choosing an Architecture

| Need | Recommended pattern |
|---|---|
| Small team, clear domain, fast iteration | Layered monolith |
| Domain-heavy, complex business rules | Clean Architecture |
| Need to swap DB or add protocols | Hexagonal (Ports & Adapters) |
| Independent team scaling, per-service load | Microservices |
| Decoupled side effects, audit trail | Event-Driven + Outbox |
| SEO + interactive UI with shared logic | Isomorphic (SSR + CSR) |

---

## Architecture Testing and Risks

### Testing focus

- **Boundary validation:** verify layer and service boundaries are respected
  (controller does not call DB directly; service uses ports/interfaces).
- **Contract testing:** verify API/event schema compatibility between producer
  and consumer.
- **Integration testing:** run real DB/broker/framework adapters together with
  use cases.

### Common risks

- **Distributed complexity:** retries, partial failures, and eventual consistency
  make debugging harder.
- **Overengineering:** introducing microservices, event buses, and many adapters
  too early adds operational cost without clear business value.
