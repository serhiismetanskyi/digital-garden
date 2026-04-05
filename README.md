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
| [Tools](./tools/README.md) | Docker, Git, Linux Terminal — commands, best practices, troubleshooting |
| [Python Libraries](./libs/README.md) | Requests, HTTPX, Pytest, Playwright, Pydantic, SQLAlchemy, FastAPI, uv, LangChain, Code Quality |

## Section Details

### API Architectures

| Resource | Topics |
|----------|--------|
| [REST API](./api-architectures/01-rest/01-architecture-http.md) | HTTP semantics, schema modeling, querying, caching, security, testing |
| [GraphQL](./api-architectures/02-graphql/01-schema-execution.md) | Schema design, resolver execution, performance, APQ/safelist rollout |
| [gRPC](./api-architectures/03-grpc/01-contract-transport.md) | Protobuf contracts, transport patterns, retries, streaming reliability |
| [WebSocket](./api-architectures/04-websocket/01-protocol-communication.md) | Protocol communication, state/scaling, reconnect/replay, resilience |
| [Cross-Cutting](./api-architectures/05-cross-cutting/01-security-observability.md) | Security, observability, reliability, SLO and incident playbooks |
| [Decision Factors](./api-architectures/06-decision-factors/01-comparison-guide.md) | Comparison matrix and architecture selection guidance |

### Client-Server Architecture

| Resource | Topics |
|----------|--------|
| [Core Model](./client-server-architecture/01-core-model/01-responsibilities-communication.md) | Responsibilities, protocol models, API architecture overview |
| [Edge Layer](./client-server-architecture/02-edge-layer/01-cdn-load-balancer.md) | CDN, load balancing, reverse proxy, API gateway, BFF |
| [Traffic & Service Mesh](./client-server-architecture/03-traffic-service-mesh/01-traffic-management.md) | Routing, rate limiting, canary, service mesh patterns |
| [Connections & Backpressure](./client-server-architecture/04-connections-backpressure/01-connection-management.md) | Connection lifecycle, flow control, backpressure strategies |
| [Scalability & Performance](./client-server-architecture/05-client-scalability-performance/01-client-architecture.md) | Client state/data architecture, scalability and performance tuning |
| [Reliability & Security](./client-server-architecture/06-reliability-security-observability/01-reliability.md) | Fault tolerance, security controls, telemetry and tracing |
| [Testing & Patterns](./client-server-architecture/07-testing-risks-patterns/01-testing.md) | Testing strategy, anti-patterns, decision factors from production |

### Software Design Patterns

| Resource | Topics |
|----------|--------|
| [Design Principles](./software-design-patterns/01-design-principles/00-oop-fundamentals.md) | OOP, SOLID, DRY/KISS/YAGNI, clean code, code quality tools |
| [Creational Patterns](./software-design-patterns/02-creational-patterns/01-patterns.md) | Factory, Builder, Prototype, Singleton and trade-offs |
| [Structural Patterns](./software-design-patterns/03-structural-patterns/01-adapter-decorator-facade.md) | Adapter, Facade, Decorator, Proxy, Composite, Bridge, Flyweight |
| [Behavioral Patterns](./software-design-patterns/04-behavioral-patterns/01-strategy-observer-command.md) | Strategy, Observer, Command, State, Mediator, Visitor |
| [Composition & Architectural](./software-design-patterns/05-composition-architectural/01-composition-advanced.md) | Layered/Clean/Hexagonal, queues vs streams, event-driven |
| [View Layer & Cross-Layer](./software-design-patterns/06-frontend-cross-layer/01-frontend-patterns.md) | View layer patterns (templates, BFF), shared contracts, cross-layer integration |
| [Decisions & Anti-Patterns](./software-design-patterns/07-decisions-testing-production/01-comparison-testing.md) | Pattern comparison, testing, anti-patterns, production readiness |

### Agentic AI Architecture

| Resource | Topics |
|----------|--------|
| [Fundamentals & Components](./agentic-ai-architecture/01-fundamentals-components.md) | Agentic AI core, ReAct loop, components, LLM app differences |
| [Multi-Agent Patterns](./agentic-ai-architecture/02-multi-agent-patterns.md) | Supervisor, Hybrid, BDI, Neuro-Symbolic, coordination |
| [Memory & RAG](./agentic-ai-architecture/03-memory-rag.md) | STM/LTM, RAG pipeline, vector DB choices, retrieval methods |
| [Tool Integration & Prompting](./agentic-ai-architecture/04-tool-integration-prompting.md) | Function calling, tool registry, CoT, ReAct, ToT prompting |
| [LLM Config & Security](./agentic-ai-architecture/05-llm-config-security.md) | Model settings, guardrails, prompt injection threats |
| [Testing & Observability](./agentic-ai-architecture/06-testing-observability.md) | Metrics, test layers, observability, failure modes, production checklist |

### OWASP API Security

| Resource | Topics |
|----------|--------|
| [API Recommendations](./owasp-api-security/01-owasp-api-recommendations.md) | Security baseline, per-risk controls (API1–API10), operational hardening, CI/CD gates |
| [API Testing Checklist](./owasp-api-security/02-owasp-api-testing-checklist.md) | Prioritized checklist (P0/P1/P2) with how-to-test guidance, tool references |
| [API Advanced Controls](./owasp-api-security/03-owasp-api-advanced-controls.md) | OAuth2/OIDC, webhooks, gateway, multi-tenancy, uploads, incident response |

### OWASP LLM Security

| Resource | Topics |
|----------|--------|
| [LLM Security Guide](./owasp-llm-security/01-owasp-llm-security-guide.md) | LLM01–LLM10 risk guidance, architecture blueprint, CI/CD gates, compliance |
| [LLM Testing Checklist](./owasp-llm-security/02-owasp-llm-security-testing-checklist.md) | Prioritized checklist (P0/P1/P2), red teaming, release criteria |

### QA Methodology

| Resource | Topics |
|----------|--------|
| [Fundamentals, Levels & Types](./qa-methodology/01-fundamentals-levels-types.md) | QA vs QC, shift-left, ISTQB principles, test levels, types |
| [Test Design & Planning](./qa-methodology/03-design-planning.md) | Black/white-box techniques, test case structure, plans |
| [Execution, Defects & Envs](./qa-methodology/04-execution-defects-envs.md) | Execution process, defect lifecycle, severity vs priority |
| [Automation, SDLC & Agile](./qa-methodology/05-automation-sdlc-agile.md) | When to automate, QA in Scrum, risk-based testing |
| [Metrics, Docs & Practices](./qa-methodology/06-metrics-docs-practices-roles.md) | Metrics, traceability, anti-patterns, career levels |
| [TDD, BDD & ATDD](./qa-methodology/07-tdd-bdd-atdd.md) | Red/Green/Refactor, Gherkin, ATDD, combining approaches |
| [Quality Gates — Domain QA](./qa-methodology/08-release-quality-gates-checklists.md) | Gates, exploratory, coverage, estimation, domain-specific QA |

### Test Design Techniques

| Resource | Topics |
|----------|--------|
| [Equivalence Partitioning](./test-design-techniques/01-input-based/01-equivalence-partitioning.md) | Split inputs into groups; one test per group |
| [Boundary Value Analysis](./test-design-techniques/01-input-based/02-boundary-value-analysis.md) | Test values at and around the edge of each partition |
| [Pairwise Testing](./test-design-techniques/01-input-based/03-pairwise-testing.md) | Cover every pair of parameter values with minimum test count |
| [Decision Table](./test-design-techniques/02-logic-state-based/01-decision-table.md) | Map all condition combinations to expected outcomes |
| [State Transition](./test-design-techniques/02-logic-state-based/02-state-transition.md) | Verify valid/invalid transitions in a state machine |
| [CRUD Testing](./test-design-techniques/03-experience-based/01-crud-testing.md) | Verify full data lifecycle: create, read, update, delete |
| [Metamorphic Testing](./test-design-techniques/03-experience-based/02-metamorphic-testing.md) | Check relationships between outputs when inputs change |
| [Fuzz & Random Testing](./test-design-techniques/03-experience-based/03-fuzz-random-testing.md) | Send unexpected/random data to expose crashes and edge cases |

### Test Design Patterns

| Resource | Topics |
|----------|--------|
| [Fundamentals](./test-design-patterns/01-fundamentals/01-test-types-levels.md) | Test types, pyramid, core principles, test architecture |
| [Core Patterns](./test-design-patterns/02-core-patterns/01-page-object-model.md) | POM, Screenplay, Data Builder, Fixture, Factory |
| [Advanced Patterns](./test-design-patterns/03-advanced-patterns/01-wrapper-fluent-interface.md) | Wrapper, Fluent Interface, Assertion helpers, Data-Driven |
| [API Test Patterns](./test-design-patterns/04-api-test-patterns/01-rest-graphql.md) | REST/GraphQL/gRPC/WebSocket test patterns |
| [Data, Mocking & Env](./test-design-patterns/05-data-mocking-env/01-test-data-management.md) | Test data, mocking/stubbing/fakes, environments |
| [Execution & Reliability](./test-design-patterns/06-execution-reliability/01-execution-strategies.md) | Parallel, flakiness, performance SLOs, observability |
| [Decisions & Production](./test-design-patterns/07-decisions-production/01-ci-cd-security.md) | CI/CD, security testing, anti-patterns, heuristics |

### Testing Pyramid

| Resource | Topics |
|----------|--------|
| [Unit Tests](./testing-pyramid/01-unit-tests/01-concept-and-examples.md) | Isolation, fast feedback, pytest marks, coverage |
| [Integration Tests](./testing-pyramid/02-integration-tests/01-concept-and-examples.md) | Real HTTP via Playwright APIRequestContext, fixtures, cleanup |
| [E2E Tests](./testing-pyramid/03-e2e-tests/01-concept-and-examples.md) | Browser automation with Playwright, stable locators, user flows |
| [Pyramid Strategy](./testing-pyramid/04-pyramid-strategy/01-shape-antipatterns-alternatives.md) | Ice cream cone, Testing Trophy, microservice contracts, CI timing |

### Test Automation Framework

| Resource | Topics |
|----------|--------|
| [Architecture](./test-automation-framework/01-architecture/01-goals-principles.md) | Goals, principles, layers, directory structure |
| [Design Patterns](./test-automation-framework/02-design-patterns/01-ui-patterns.md) | POM, Screenplay, API/data patterns, fluent interface |
| [Test Data](./test-automation-framework/03-test-data/01-strategies-isolation.md) | Strategies, isolation, builders, factories, seeding |
| [API Testing](./test-automation-framework/04-api-testing/01-rest-graphql.md) | REST, GraphQL, gRPC, WebSocket testing |
| [UI Testing](./test-automation-framework/05-ui-testing/01-tools-patterns.md) | Playwright vs Selenium, selectors, waits, retry |
| [Execution & Reliability](./test-automation-framework/06-execution-reliability/01-parallel-execution.md) | Parallel execution, flakiness, mocking, isolation |
| [Config, CI & Decisions](./test-automation-framework/07-config-ci-decisions/01-config-management.md) | Config, logging, CI/CD, performance, anti-patterns, risks |

### LLM Evaluation

| Resource | Topics |
|----------|--------|
| [Introduction](./llm-evaluation/01_introduction.md) | DeepEval overview, LLM-as-Judge, key concepts, setup |
| [RAG Metrics](./llm-evaluation/01_metrics/02_rag_metrics.md) | AnswerRelevancy, Faithfulness, ContextualPrecision/Recall/Relevancy |
| [LLM Quality Metrics](./llm-evaluation/01_metrics/03_llm_quality_metrics.md) | Hallucination, Toxicity, Bias, Summarization, GEval |
| [Agent Metrics](./llm-evaluation/01_metrics/04_agent_metrics.md) | ToolCorrectness, TaskCompletion, GoalAccuracy, PlanQuality |
| [Red Teaming](./llm-evaluation/02_testing/09_red_teaming.md) | RedTeamer, vulnerability scanning, attack enhancements |
| [Practical RAG Testing](./llm-evaluation/03_practical/14_practical_rag_testing.md) | LangChain + Ollama + Chroma pipeline, E2E walkthrough |

### Performance Testing

| Resource | Topics |
|----------|--------|
| [Fundamentals & Metrics](./performance-testing/01-fundamentals-metrics/01-goals-and-types.md) | Goals, test types (load/stress/spike/soak), core metrics |
| [Locust](./performance-testing/02-locust/01-architecture-basics.md) | Architecture, load modeling, test design, analysis, advanced usage |
| [Bottlenecks & Monitoring](./performance-testing/03-bottlenecks-monitoring/01-bottlenecks.md) | Where systems break and how to observe it |
| [Execution & Results](./performance-testing/04-execution-results/01-sla-slo.md) | SLA/SLO, execution strategy, interpreting results, pitfalls |

### CI/CD Approaches

| Resource | Topics |
|----------|--------|
| [Fundamentals](./ci-cd-approaches/01-fundamentals/01-concepts-goals.md) | CI/CD/CD definitions, pipeline architecture, triggers |
| [Build & Artifacts](./ci-cd-approaches/02-build-artifacts/01-build-stage.md) | Build stage, caching, Docker build, artifact management |
| [Testing](./ci-cd-approaches/03-testing/01-test-layers-strategy.md) | Test layers in pipeline, quality gates, coverage |
| [Deployment](./ci-cd-approaches/04-deployment/01-deployment-strategies.md) | Rolling, Blue-Green, Canary, Feature Flags, IaC |
| [Security & Observability](./ci-cd-approaches/05-security-observability/01-security.md) | Secrets, SAST, scanning, pipeline metrics, DORA |
| [Release & Production](./ci-cd-approaches/06-release-production/01-release-management.md) | SemVer, rollback, smoke tests, post-deploy monitoring |
| [Patterns & Decisions](./ci-cd-approaches/07-patterns-decisions/01-advanced-patterns.md) | GitOps, trunk-based, failure handling, anti-patterns |

### Tools

| Resource | Topics |
|----------|--------|
| [Docker Overview](./tools/docker/README.md) | Architecture, lifecycle, Compose, networking, security, debugging |
| [Git Overview](./tools/git/README.md) | Commands, branching, commits, advanced workflows, hooks, recovery |
| [Linux Terminal](./tools/linux-terminal/README.md) | Navigation, files, search, text processing, processes, networking |
