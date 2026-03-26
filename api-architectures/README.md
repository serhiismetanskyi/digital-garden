# API Architectures

## Section Descriptions

### 1) REST API

| File | Topics |
|------|--------|
| [01-architecture-http.md](./01-rest/01-architecture-http.md) | REST constraints, resource design, uniform interface, method semantics (safe/idempotent), HEAD/OPTIONS, PATCH (RFC 6902/7396), status code mapping, header strategy |
| [02-data-schema.md](./01-rest/02-data-schema.md) | OpenAPI 3.1 + JSON Schema 2020-12, strict validation, nullable vs missing, enum/range constraints, `additionalProperties`, mass-assignment prevention |
| [03-querying.md](./01-rest/03-querying.md) | Field selection, search vs filtering, sort conventions, pagination models (offset/cursor/page), metadata, mutation edge cases |
| [04-caching-concurrency.md](./01-rest/04-caching-concurrency.md) | Cache-Control, ETag/If-None-Match, Last-Modified, stale directives, CDN caveats, optimistic locking via If-Match, idempotency-key patterns |
| [05-errors-security-versioning.md](./01-rest/05-errors-security-versioning.md) | Error models (incl. RFC 9457 Problem Details), authN/authZ, rate limiting, injection defenses, CORS/HTTPS, versioning and deprecation (`Sunset`, `Deprecation`) |
| [06-testing-risks.md](./01-rest/06-testing-risks.md) | End-to-end test plan (schema/query/cache/auth/perf), concurrency and rate-limit checks, conditional write policy (`428`/`412`), risk register |
| [07-code-examples.md](./01-rest/07-code-examples.md) | Pydantic contracts, Playwright API fixtures, CRUD/query/schema/idempotency/concurrency tests |

### 2) GraphQL

| File | Topics |
|------|--------|
| [01-schema-execution.md](./02-graphql/01-schema-execution.md) | Type system, resolver design, N+1 mitigation (DataLoader), execution behavior |
| [02-queries-performance.md](./02-graphql/02-queries-performance.md) | Query shaping, fragments, depth/complexity limits, caching and cost controls |
| [03-testing-risks.md](./02-graphql/03-testing-risks.md) | Schema and resolver tests, subscriptions test strategy, risk scenarios |
| [04-code-examples.md](./02-graphql/04-code-examples.md) | Python + Pydantic + Playwright GraphQL testing patterns |
| [05-apq-safelist-rollout.md](./02-graphql/05-apq-safelist-rollout.md) | APQ vs safelisting, rollout guardrails, CI/CD governance |

### 3) gRPC

| File | Topics |
|------|--------|
| [01-contract-transport.md](./03-grpc/01-contract-transport.md) | Protobuf contracts, field numbering strategy, HTTP/2 transport specifics |
| [02-patterns-codegen-errors.md](./03-grpc/02-patterns-codegen-errors.md) | Unary/streaming patterns, code generation lifecycle, status/error handling |
| [03-testing-risks.md](./03-grpc/03-testing-risks.md) | Contract testing, RPC reliability tests, streaming/backpressure risks |
| [04-code-examples.md](./03-grpc/04-code-examples.md) | Python + grpcio + Pydantic + gRPC-Gateway examples |
| [05-retry-hedging-policy.md](./03-grpc/05-retry-hedging-policy.md) | Retry/hedging service-config baseline, idempotency and safety limits |

### 4) WebSocket

| File | Topics |
|------|--------|
| [01-protocol-communication.md](./04-websocket/01-protocol-communication.md) | Upgrade handshake, frame/message contracts, ACK strategy |
| [02-state-scaling.md](./04-websocket/02-state-scaling.md) | Connection lifecycle, fan-out, horizontal scaling patterns |
| [03-testing-risks.md](./04-websocket/03-testing-risks.md) | Ordering, reconnect/replay, fault-injection and resilience tests |
| [04-code-examples.md](./04-websocket/04-code-examples.md) | Python + Pydantic + Playwright WebSocket examples |
| [05-reliability-pattern.md](./04-websocket/05-reliability-pattern.md) | Sequence + dedup + replay-window reliability model |

### 5) Cross-Cutting Concerns

| File | Topics |
|------|--------|
| [01-security-observability.md](./05-cross-cutting/01-security-observability.md) | Security controls, OWASP-focused checks, structured logs, metrics, traces |
| [02-performance-reliability.md](./05-cross-cutting/02-performance-reliability.md) | Latency/throughput tuning, resilience patterns, capacity concerns |
| [03-slo-error-budget-incident-playbook.md](./05-cross-cutting/03-slo-error-budget-incident-playbook.md) | SLO design, error-budget policy, burn-rate alerts, incident response flow |

### 6) Decision Factors

| File | Topics |
|------|--------|
| [01-comparison-guide.md](./06-decision-factors/01-comparison-guide.md) | Protocol comparison matrix, detailed decision factors, hybrid-architecture combinations, quick selection flow |
