# Client–Server Architecture

## Section Descriptions

### 1. Core Model

| File | Topics |
|------|--------|
| [01-responsibilities-communication.md](01-core-model/01-responsibilities-communication.md) | Client/server responsibilities, communication models, HTTP/1.1 vs HTTP/2 vs HTTP/3, TCP vs QUIC, connection reuse |
| [02-api-architectures-overview.md](01-core-model/02-api-architectures-overview.md) | REST, GraphQL, gRPC, WebSocket, SSE — quick comparison for architecture decisions |

### 2. Edge Layer

| File | Topics |
|------|--------|
| [01-cdn-load-balancer.md](02-edge-layer/01-cdn-load-balancer.md) | CDN caching, geo distribution, L4/L7 LB, algorithms, health checks, SSL termination, sticky sessions |
| [02-reverse-proxy-api-gateway.md](02-edge-layer/02-reverse-proxy-api-gateway.md) | Reverse proxy, forward proxy, API gateway responsibilities, BFF pattern, API composition, facade, WAF |

### 3. Traffic Management and Service Mesh

| File | Topics |
|------|--------|
| [01-traffic-management.md](03-traffic-service-mesh/01-traffic-management.md) | Path/host routing, rate limiting, throttling, canary releases, blue-green deployment, failover |
| [02-service-layer-mesh.md](03-traffic-service-mesh/02-service-layer-mesh.md) | Monolith vs microservices, REST/gRPC/async internal comms, service aggregation, Istio vs Linkerd |

### 4. Connections and Backpressure

| File | Topics |
|------|--------|
| [01-connection-management.md](04-connections-backpressure/01-connection-management.md) | HTTP keep-alive, connection pooling, HTTP/2 multiplexing, gRPC keepalive + flow control, WebSocket reconnect + heartbeat |
| [02-backpressure-flow-control.md](04-connections-backpressure/02-backpressure-flow-control.md) | REST rate limiting algorithms, gRPC HTTP/2 flow control, WebSocket bounded queues, drop strategies, flow signals |

### 5. Client Architecture, Scalability, Performance

| File | Topics |
|------|--------|
| [01-client-architecture.md](05-client-scalability-performance/01-client-architecture.md) | Data fetching patterns, state management (server/UI/URL/persistent), batching, caching, debounce/throttle |
| [02-scalability.md](05-client-scalability-performance/02-scalability.md) | Horizontal/vertical scaling, bottlenecks, WebSocket sticky sessions + pub/sub, multi-region geo routing |
| [03-performance.md](05-client-scalability-performance/03-performance.md) | Latency sources, throughput, compression (gzip/brotli), protobuf vs JSON, sparse fieldsets, SLO targets |

### 6. Reliability, Security, Observability

| File | Topics |
|------|--------|
| [01-reliability.md](06-reliability-security-observability/01-reliability.md) | Retry + backoff + jitter, circuit breaker states, timeout policy, graceful degradation, graceful shutdown |
| [02-security.md](06-reliability-security-observability/02-security.md) | JWT, OAuth2, mTLS, TLS config, firewall, rate limiting, input validation, WAF, DDoS, CORS |
| [03-observability.md](06-reliability-security-observability/03-observability.md) | Structured logging, RED metrics, distributed tracing (OpenTelemetry), edge observability (gateway + LB) |

### 7. Testing, Risks, Patterns, Decisions

| File | Topics |
|------|--------|
| [01-testing.md](07-testing-risks-patterns/01-testing.md) | API testing (REST/GraphQL/gRPC/WebSocket), integration testing, load testing, chaos testing |
| [02-risks-anti-patterns.md](07-testing-risks-patterns/02-risks-anti-patterns.md) | Distributed complexity, tight coupling, stateful scaling, security surface, 6 key anti-patterns |
| [03-real-world-decision-factors.md](07-testing-risks-patterns/03-real-world-decision-factors.md) | CDN+REST, GraphQL+BFF, gRPC internal, WebSocket realtime, multi-layer caching, decision guide |
