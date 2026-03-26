# Software Design Patterns and Principles

## Section Descriptions

### 1. Design Principles

| File | Topics |
|------|--------|
| [01-solid-principles.md](01-design-principles/01-solid-principles.md) | SRP, OCP, LSP, ISP, DIP — with Python examples and violation/fix patterns |
| [02-fundamental-principles.md](01-design-principles/02-fundamental-principles.md) | DRY, KISS, YAGNI, Composition over Inheritance, SoC, High Cohesion/Low Coupling |

### 2. Creational Patterns

| File | Topics |
|------|--------|
| [01-patterns.md](02-creational-patterns/01-patterns.md) | Singleton, Factory Method, Abstract Factory, Builder, Prototype — Python examples, use cases, risks |

### 3. Structural Patterns

| File | Topics |
|------|--------|
| [01-adapter-decorator-facade.md](03-structural-patterns/01-adapter-decorator-facade.md) | Adapter, Decorator, Facade — with Python examples |
| [02-proxy-composite-bridge-flyweight.md](03-structural-patterns/02-proxy-composite-bridge-flyweight.md) | Proxy, Composite, Bridge, Flyweight — with risks table |

### 4. Behavioral Patterns

| File | Topics |
|------|--------|
| [01-strategy-observer-command.md](04-behavioral-patterns/01-strategy-observer-command.md) | Strategy, Observer, Command — real-world uses, risks |
| [02-chain-state-mediator.md](04-behavioral-patterns/02-chain-state-mediator.md) | Chain of Responsibility, State, Mediator — middleware pipeline, order lifecycle |
| [03-iterator-template-visitor.md](04-behavioral-patterns/03-iterator-template-visitor.md) | Iterator, Template Method, Visitor — risks table |

### 5. Composition and Architectural Patterns

| File | Topics |
|------|--------|
| [01-composition-advanced.md](05-composition-architectural/01-composition-advanced.md) | Layout Composer, Aggregator/Composer, Pipeline/Middleware, BFF |
| [02-architectural-patterns.md](05-composition-architectural/02-architectural-patterns.md) | Layered, Clean Architecture, Hexagonal (Ports & Adapters) — Python examples, comparison table |
| [03-event-driven-isomorphic.md](05-composition-architectural/03-event-driven-isomorphic.md) | Microservices, Event-Driven (Outbox, idempotency), Isomorphic/Universal Architecture |

### 6. Frontend and Cross-Layer Patterns

| File | Topics |
|------|--------|
| [01-frontend-patterns.md](06-frontend-cross-layer/01-frontend-patterns.md) | Component-Based, Atomic Design, Container/Presentational, Hooks, State Management, BFF Integration |
| [02-cross-layer-patterns.md](06-frontend-cross-layer/02-cross-layer-patterns.md) | Shared DTOs, Shared Validation, Type Sharing (OpenAPI/Protobuf/tRPC), versioning risks |

### 7. Decisions, Testing, Anti-Patterns

| File | Topics |
|------|--------|
| [01-comparison-testing.md](07-decisions-testing-production/01-comparison-testing.md) | Pattern comparison matrix (Strategy vs State, Factory vs Builder, etc.), Unit/Integration/Contract/Property/Mutation testing |
| [02-antipatterns-real-world.md](07-decisions-testing-production/02-antipatterns-real-world.md) | God Object, Spaghetti, Cyclic deps, Overengineering, Anemic model, real-world usage table, heuristics, decision factors |
