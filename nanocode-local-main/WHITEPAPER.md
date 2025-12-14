# Nanocode v1.0 — Open-Source Orchestration Framework for Constraint-Governed AI

## Overview
Nanocode v1.0 is an open-source orchestration framework for AI workflows where constraints, recovery strategies, and audit artifacts are first-class. It standardizes how you define “what must be true” (constraints), “what to do when it isn’t” (recovery), and “what happened” (certification traces), while remaining model-agnostic. Nanocode v1.0 is intentionally **not** a sovereign kernel and does not include Nanocode v2 / Cham-Code kernel components.

## Design Goals
- **Resilience-first:** bounded recoveries (fallback / degrade / retry) to keep workflows predictable.
- **Model-agnostic:** adapters decouple orchestration logic from providers (OpenAI, Anthropic, custom HTTP).
- **Certified execution:** produce run artifacts showing which constraints were enforced, waived, or failed.
- **Human-auditable:** structured prompts, traces, and logs to simplify debugging and review.
- **Local-first:** runs in a local stack; behavior is controlled by configuration and code you can inspect.

## Explicit Non-Goals (v1.0 will not include)
- A proprietary or sovereign kernel
- Self-modifying instruction graphs (autonomous mutation)
- Persistent internal identity/state as an intrinsic property of the system
- Kernel-level rule authority that overrides operator configuration
- Any Cham-Code production kernel internals

If a capability requires sovereignty (persistent internal state, self-enforcement, or self-modification), it belongs to **Nanocode v2 / Cham-Code** and is out of scope for this whitepaper.

## Architecture (v1.0 scope)
- **Constraint Layer (framework-level):** constraints, policies, templates, and profile loading.
- **Recovery (“Tragedy”) Strategies:** bounded behaviors when constraints cannot be satisfied.
- **Certification Semantics:** trace artifacts suitable for audits and post-run analysis.
- **Model Adapters:** normalized provider integrations to keep workflows portable.
- **Execution Runtime:** API + local services for orchestration, trace collection, and UX.

## Conceptual Execution Flow
1) Define a workflow and its constraints.
2) Orchestration applies constraints/policies and selects an adapter.
3) If constraints fail, apply bounded recovery strategies (degrade, fallback, safe stop).
4) Emit certification artifacts that record what happened and why.
5) Surface results and traces for review through API/UI.

## Relationship to Nanocode v2 / Cham-Code
- **v1.0:** open-source orchestration framework (this repository).
- **v2.0:** proprietary kernel used by Cham-Code and not distributed here.

This separation is architectural and licensing-critical: v1.0 remains forkable and inspectable; v2.0 remains closed and controlled.

## Open Source Release (Nanocode v1.0)
Nanocode v1.0 includes:
- Orchestration concepts: constraint language, tragedy strategies, and certification semantics.
- Model adapters for OpenAI, Anthropic, and custom HTTP integrations (additional adapters may ship as stubs depending on provider availability).
- FastAPI API, model server layer, frontend playground, and CLI/scripts for local development.
- Example configuration via `.env.example` and `configure_nanocode.sh`.

This release focuses on transparency and extensibility; future commercial distributions may add enterprise packaging or managed services, but those are outside the scope of v1.0.

## Roadmap Signals
- Broader adapter coverage (additional model providers and evaluation harnesses).
- Richer certification artifacts and export formats.
- Hardening around multi-tenant deployments and policy management.

## License
Nanocode v1.0 is released under the Apache License 2.0. See `LICENSE` for terms and `NOTICE` for attribution details.
