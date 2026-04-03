# OWASP LLM Security

Practical knowledge-base section focused on **OWASP Top 10 for LLM Applications (2026)** — risk guidance, architecture controls, and a release-gate testing checklist.

## Structure

| File | Topics |
|---|---|
| [01 OWASP LLM Security Guide](./01-owasp-llm-security-guide.md) | LLM01–LLM10 risk guidance, architecture blueprint, CI/CD gates, memory/authz/compliance controls |
| [02 OWASP LLM Security Testing Checklist](./02-owasp-llm-security-testing-checklist.md) | Prioritized checklist (P0/P1/P2) with how-to-test steps, red teaming, and release criteria |

## What to Start With

1. Read `01` and map controls to your current LLM architecture.
2. Prioritize `LLM01` (Prompt Injection), `LLM05` (Output Handling), `LLM06` (Agency), and `LLM02` (Disclosure).
3. Use `02` as a release gate for every LLM feature change and for periodic red-team exercises.
