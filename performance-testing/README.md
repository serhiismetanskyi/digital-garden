# Performance Testing

Performance testing answers one question: **does the system behave correctly under load?**

This section covers the full spectrum — from theory to Locust tooling.

---

## Structure

| Folder | What's Inside |
|--------|---------------|
| `01-fundamentals-metrics/` | Goals, test types, all core metrics, metric relationships |
| `02-locust/` | Locust architecture, load modeling, test design, analysis, advanced usage |
| `03-bottlenecks-monitoring/` | Where systems break and how to observe it |
| `04-execution-results/` | SLA/SLO, execution strategy, interpreting results, pitfalls |

---

## When to Apply Which Test Type

| Situation | Test Type |
|-----------|-----------|
| Regular deploy validation | Load test |
| Finding system limits | Stress test |
| Flash sale, viral traffic | Spike test |
| Memory leaks, long sessions | Soak test |
| Horizontal scaling plan | Scalability test |

---

## Key Principle

> Always analyze p95/p99. Average latency hides the pain of real users.
