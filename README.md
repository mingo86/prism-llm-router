# Prism

**A privacy-first, cost-aware multi-LLM router and note dispatcher.**

> **Status: pre-application skeleton.** This repository accompanies an application to the
> [NLnet Restack fund](https://nlnet.nl/) (call window: 3 September – 3 November 2026).
> Code lands milestone by milestone; the roadmap below is the build plan.

## The problem

Most conversational-AI features today are wired directly to a single, opaque, non-European
model provider. That creates vendor lock-in, unpredictable cost, and a privacy problem:
user text — often deeply personal — is shipped wholesale to a remote API.

## What Prism ships

- **Policy-based routing** across multiple LLM backends — including European and
  self-hostable models (e.g. Mistral, llama.cpp) — by cost, latency, quality tier and
  privacy tier, with hard budget caps and fallback chains.
- **Data minimisation by default**: PII redaction before any remote call, and a
  first-class fully local path so sensitive text never leaves the user's infrastructure.
- **A natural-language note dispatcher**: classifies free-form notes (typed or
  transcribed) into structured destinations, runnable on a self-hosted quantized model.
- **Reusable packaging**: SDK on npm and PyPI, a reference server, runnable examples,
  reproducible cross-provider benchmarks.

## Architecture (planned)

```
application ──> Prism SDK ──> policy engine ──> provider adapters (≥4, incl. self-hosted)
                                │                     │
                            PII redaction        token accounting,
                            local-only path      budget caps, fallbacks
```

## Roadmap

| # | Deliverable |
|---|---|
| M1 | Core router + adapters for ≥4 backends (≥1 European, ≥1 self-hosted/llama.cpp) |
| M2 | Policy engine: cost/latency/quality/privacy routing, budget caps, fallback chains, token accounting |
| M3 | Pluggable NL→schema dispatcher, runnable on a self-hosted quantized model |
| M4 | Privacy layer: pre-call PII redaction, 100% local path, data minimisation by default |
| M5 | Packaging: npm + PyPI SDKs, semantic versioning, runnable examples |
| M6 | Reproducible cost/quality/latency benchmarks across providers (public suite + report) |
| M7 | Full test suite + threat model + NGI security review + hardening |
| M8 | Complete documentation, 2 reference integrations, community issue triage |
| M9 | 1.0 release + 12-month maintenance plan + launch write-up |

## Dogfooding

Every release is validated against a real consumer life-logging product in production —
continuous, honest validation rather than laboratory fixtures.

## Comparison with existing efforts

LiteLLM and LangChain offer provider abstraction; OpenRouter offers commercial
multi-model routing. Prism differs on three axes: (a) privacy-first by design — PII
redaction and a first-class local path, not an afterthought; (b) an integrated
self-hostable note dispatcher, which routing libraries do not provide; (c) governance and
licence — genuine community OSS under EUPL, aimed at European digital sovereignty.

## Licence

[EUPL-1.2](LICENSE).
