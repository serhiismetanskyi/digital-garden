# Digital Garden: Knowledge Base

## Architecture & Design

| Section | Topics |
|---------|--------|
| [API Architectures](./api-architectures/README.md) | REST, GraphQL, gRPC, WebSocket, cross-cutting concerns, architecture decision factors |
| [Client-Server Architecture](./client-server-architecture/README.md) | Core model, edge layer, traffic/service mesh, connections, scalability, reliability, testing |
| [Software Design Patterns](./software-design-patterns/README.md) | OOP, SOLID, DRY/KISS, clean code, creational/structural/behavioral patterns, architecture, testing |
| [Agentic AI Architecture](./agentic-ai-architecture/README.md) | Agent fundamentals, multi-agent patterns, memory/RAG, tool integration, LLM config, security, testing |

## Security

| Section | Topics |
|---------|--------|
| [OWASP API Security](./owasp-api-security/README.md) | API Top 10 (2023), per-risk controls, OAuth2/webhooks/gateway, testing checklist, incident response |
| [OWASP LLM Security](./owasp-llm-security/README.md) | LLM Top 10 (2026), prompt injection, output handling, agent/tool security, RAG hardening, testing checklist |

## QA & Testing

| Section | Topics |
|---------|--------|
| [QA Methodology](./qa-methodology/README.md) | Fundamentals, test design, execution, defects, automation/SDLC, metrics, TDD/BDD, quality gates, coverage |
| [Test Design Techniques](./test-design-techniques/README.md) | EP, BVA, Decision Table, State Transition, CRUD, Metamorphic, Pairwise, Fuzz testing |
| [Test Design Patterns](./test-design-patterns/README.md) | POM, Screenplay, Data Builder, API test patterns, mocking, execution, reliability, CI/CD |
| [Testing Pyramid](./testing-pyramid/README.md) | Unit / Integration / E2E strategy, common mistakes per level, anti-patterns |
| [Test Automation Framework](./test-automation-framework/README.md) | Architecture, UI/API patterns, test data, parallel execution, flakiness, mocking, CI/CD |
| [LLM Evaluation](./llm-evaluation/README.md) | DeepEval: RAG / quality / agent / chatbot / MCP metrics, red teaming, benchmarks, practical guides |
| [Performance Testing](./performance-testing/README.md) | Load / stress / spike / soak testing, core metrics, Locust, bottlenecks, monitoring, SLA/SLO |

## Infrastructure & Tools

| Section | Topics |
|---------|--------|
| [CI/CD Approaches](./ci-cd-approaches/README.md) | Pipeline architecture, build/artifacts, testing, deployment, security, release, advanced patterns |
| [Databases](./databases/README.md) | Database types and selection guide, PostgreSQL: commands, schema, queries, performance, admin |
| [Tools](./tools/README.md) | Docker (lifecycle, Compose, networking, security), Git (commands, branching, hooks, recovery) |
| [Python Libraries](./libs/README.md) | Requests, HTTPX, Pytest, Playwright, LangChain |

## Section Details

### API Architectures

| Resource | Topics |
|----------|--------|
| [REST API](./api-architectures/01-rest/) | HTTP semantics, schema modeling, querying, caching, security, testing |
| [GraphQL](./api-architectures/02-graphql/) | Schema design, resolver execution, performance, APQ/safelist rollout |
| [gRPC](./api-architectures/03-grpc/) | Protobuf contracts, transport patterns, retries, streaming reliability |
| [WebSocket](./api-architectures/04-websocket/) | Protocol communication, state/scaling, reconnect/replay, resilience |
| [Cross-Cutting](./api-architectures/05-cross-cutting/) | Security, observability, reliability, SLO and incident playbooks |
| [Decision Factors](./api-architectures/06-decision-factors/) | Comparison matrix and architecture selection guidance |

### Client-Server Architecture

| Resource | Topics |
|----------|--------|
| [Core Model](./client-server-architecture/01-core-model/) | Responsibilities, protocol models, API architecture overview |
| [Edge Layer](./client-server-architecture/02-edge-layer/) | CDN, load balancing, reverse proxy, API gateway, BFF |
| [Traffic & Service Mesh](./client-server-architecture/03-traffic-service-mesh/) | Routing, rate limiting, canary, service mesh patterns |
| [Connections & Backpressure](./client-server-architecture/04-connections-backpressure/) | Connection lifecycle, flow control, backpressure strategies |
| [Scalability & Performance](./client-server-architecture/05-client-scalability-performance/) | Client state/data architecture, scalability and performance tuning |
| [Reliability & Security](./client-server-architecture/06-reliability-security-observability/) | Fault tolerance, security controls, telemetry and tracing |
| [Testing & Patterns](./client-server-architecture/07-testing-risks-patterns/) | Testing strategy, anti-patterns, decision factors from production |

### Software Design Patterns

| Resource | Topics |
|----------|--------|
| [Design Principles](./software-design-patterns/01-design-principles/) | OOP, SOLID, DRY/KISS/YAGNI, clean code, code quality tools |
| [Creational Patterns](./software-design-patterns/02-creational-patterns/) | Factory, Builder, Prototype, Singleton and trade-offs |
| [Structural Patterns](./software-design-patterns/03-structural-patterns/) | Adapter, Facade, Decorator, Proxy, Composite, Bridge, Flyweight |
| [Behavioral Patterns](./software-design-patterns/04-behavioral-patterns/) | Strategy, Observer, Command, State, Mediator, Visitor |
| [Composition & Architectural](./software-design-patterns/05-composition-architectural/) | Layered/Clean/Hexagonal, queues vs streams, event-driven |
| [View Layer & Cross-Layer](./software-design-patterns/06-frontend-cross-layer/) | View layer patterns (templates, BFF), shared contracts, cross-layer integration |
| [Decisions & Anti-Patterns](./software-design-patterns/07-decisions-testing-production/) | Pattern comparison, testing, anti-patterns, production readiness |

### QA Methodology

| Resource | Topics |
|----------|--------|
| [Fundamentals, Levels & Types](./qa-methodology/01-fundamentals-levels-types.md) | QA vs QC, shift-left, ISTQB principles, test levels, types |
| [Test Design & Planning](./qa-methodology/03-design-planning.md) | Black/white-box techniques, test case structure, plans |
| [Execution, Defects & Envs](./qa-methodology/04-execution-defects-envs.md) | Execution process, defect lifecycle, severity vs priority |
| [Automation, SDLC & Agile](./qa-methodology/05-automation-sdlc-agile.md) | When to automate, QA in Scrum, risk-based testing |
| [Metrics, Docs & Practices](./qa-methodology/06-metrics-docs-practices-roles.md) | Metrics, traceability, anti-patterns, career levels |
| [TDD, BDD & ATDD](./qa-methodology/07-tdd-bdd-atdd.md) | Red/Green/Refactor, Gherkin, ATDD, combining approaches |
| [Quality Gates — Domain QA](./qa-methodology/08-release-quality-gates-checklists.md) | Gates, exploratory, coverage, estimation, domain-specific QA (files 08–15) |

### Test Design Patterns

| Resource | Topics |
|----------|--------|
| [Fundamentals](./test-design-patterns/01-fundamentals/) | Test types, pyramid, core principles, test architecture |
| [Core Patterns](./test-design-patterns/02-core-patterns/) | POM, Screenplay, Data Builder, Fixture, Factory |
| [Advanced Patterns](./test-design-patterns/03-advanced-patterns/) | Wrapper, Fluent Interface, Assertion helpers, Data-Driven |
| [API Test Patterns](./test-design-patterns/04-api-test-patterns/) | REST/GraphQL/gRPC/WebSocket test patterns |
| [Data, Mocking & Env](./test-design-patterns/05-data-mocking-env/) | Test data, mocking/stubbing/fakes, environments |
| [Execution & Reliability](./test-design-patterns/06-execution-reliability/) | Parallel, flakiness, performance SLOs, observability |
| [Decisions & Production](./test-design-patterns/07-decisions-production/) | CI/CD, security testing, anti-patterns, heuristics |

### Databases

| Resource | Topics |
|----------|--------|
| [PostgreSQL Overview](./databases/postgresql/README.md) | Features, ecosystem, extensions, cheat sheet |
| [Commands & psql](./databases/postgresql/01-commands-psql.md) | Connection, navigation, psql shortcuts, import/export |
| [Schema & Data Types](./databases/postgresql/02-schema-data-types.md) | Tables, types, constraints, indexes, views |
| [Queries & Performance](./databases/postgresql/03-queries-performance.md) | EXPLAIN ANALYZE, indexing, pagination, anti-patterns |
| [Admin & Operations](./databases/postgresql/04-admin-operations.md) | Users, backup, Docker setup, tuning, monitoring |
| [Basic Query Commands](./databases/postgresql/05-basic-query-commands.md) | SQL cheat sheet: CRUD, filters, joins, CTEs, window functions |

### Tools

| Resource | Topics |
|----------|--------|
| [Docker Overview](./tools/docker/README.md) | Architecture, lifecycle, cheat sheet, when to containerize |
| [Git Overview](./tools/git/README.md) | Object model, three-area workflow, cheat sheet |

<!-- child-readmes:start -->
## Child READMEs

- [Agentic Ai Architecture](./agentic-ai-architecture/README.md)
- [Api Architectures](./api-architectures/README.md)
- [Ci Cd Approaches](./ci-cd-approaches/README.md)
- [Client Server Architecture](./client-server-architecture/README.md)
- [Databases](./databases/README.md)
- [Libs](./libs/README.md)
- [Llm Evaluation](./llm-evaluation/README.md)
- [Owasp Api Security](./owasp-api-security/README.md)
- [Owasp Llm Security](./owasp-llm-security/README.md)
- [Performance Testing](./performance-testing/README.md)
- [Qa Methodology](./qa-methodology/README.md)
- [Software Design Patterns](./software-design-patterns/README.md)
- [Test Automation Framework](./test-automation-framework/README.md)
- [Test Design Patterns](./test-design-patterns/README.md)
- [Test Design Techniques](./test-design-techniques/README.md)
- [Testing Pyramid](./testing-pyramid/README.md)
- [Tools](./tools/README.md)

<!-- child-readmes:end -->
