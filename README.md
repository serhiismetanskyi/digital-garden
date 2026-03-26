<<<<<<< HEAD
# digital-garden
Digital Garden: Knowledge Base
=======
# Digital Garden

## Section Descriptions

### 1. API Architectures

| Resource | Topics |
|------|--------|
| [README.md](./api-architectures/README.md) | REST, GraphQL, gRPC, WebSocket, cross-cutting concerns, architecture decision factors |
| [01-rest](./api-architectures/01-rest/) | HTTP semantics, schema modeling, querying, caching, security, testing, code examples |
| [02-graphql](./api-architectures/02-graphql/) | Schema design, resolver execution, performance, APQ/safelist rollout |
| [03-grpc](./api-architectures/03-grpc/) | Protobuf contracts, transport patterns, retries, streaming reliability |
| [04-websocket](./api-architectures/04-websocket/) | Protocol communication, state/scaling, reconnect/replay, resilience patterns |
| [05-cross-cutting](./api-architectures/05-cross-cutting/) | Security, observability, reliability, SLO and incident playbooks |
| [06-decision-factors](./api-architectures/06-decision-factors/) | Comparison matrix and architecture selection guidance |

### 2. Client-Server Architecture

| Resource | Topics |
|------|--------|
| [README.md](./client-server-architecture/README.md) | End-to-end client/server model, edge layer, traffic, performance, reliability |
| [01-core-model](./client-server-architecture/01-core-model/) | Responsibilities, protocol models, API architecture overview |
| [02-edge-layer](./client-server-architecture/02-edge-layer/) | CDN, load balancing, reverse proxy, API gateway, BFF |
| [03-traffic-service-mesh](./client-server-architecture/03-traffic-service-mesh/) | Routing, rate limiting, canary, service mesh patterns |
| [04-connections-backpressure](./client-server-architecture/04-connections-backpressure/) | Connection lifecycle, flow control, backpressure strategies |
| [05-client-scalability-performance](./client-server-architecture/05-client-scalability-performance/) | Client state/data architecture, scalability and performance tuning |
| [06-reliability-security-observability](./client-server-architecture/06-reliability-security-observability/) | Fault tolerance, security controls, telemetry and tracing |
| [07-testing-risks-patterns](./client-server-architecture/07-testing-risks-patterns/) | Testing strategy, anti-patterns, decision factors from production |

### 3. Software Design Patterns and Principles

| Resource | Topics |
|------|--------|
| [README.md](./design-patterns/README.md) | Principles and pattern families with practical architecture guidance |
| [01-design-principles](./design-patterns/01-design-principles/) | SOLID, DRY, KISS, YAGNI, cohesion/coupling, SoC |
| [02-creational-patterns](./design-patterns/02-creational-patterns/) | Factory, Builder, Prototype, Singleton and usage trade-offs |
| [03-structural-patterns](./design-patterns/03-structural-patterns/) | Adapter, Facade, Decorator, Proxy, Composite, Bridge, Flyweight |
| [04-behavioral-patterns](./design-patterns/04-behavioral-patterns/) | Strategy, Observer, Command, State, Mediator, Visitor |
| [05-composition-architectural](./design-patterns/05-composition-architectural/) | Composition-first thinking, layered/clean/hexagonal architecture |
| [06-frontend-cross-layer](./design-patterns/06-frontend-cross-layer/) | Frontend patterns, shared contracts, cross-layer integration |
| [07-decisions-testing-production](./design-patterns/07-decisions-testing-production/) | Pattern comparison, testing tactics, anti-patterns, production heuristics |

## How to Use This Knowledge Base

1. Start with a section `README` to get the conceptual map.
2. Move to numbered files for deep dives from fundamentals to real-world decisions.
3. Use comparison and risk chapters before implementation choices.
>>>>>>> 1fb1960 (Initial commit for digital garden knowledge base.)
