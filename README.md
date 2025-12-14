# Nanocode v1.0 (Open Source Orchestration Framework)

Nanocode v1.0 is an open-source local orchestration framework for constraint-governed, model-agnostic AI workflows. It provides a structured way to apply constraints, recovery strategies, and certification artifacts (execution traces/audit records) to AI calls. This repository is intentionally **not** a sovereign kernel and does not include any closed Nanocode v2 / Cham-Code kernel components.

Any component that persists internal state as an intrinsic property, self-modifies instruction graphs, or enforces rules independently of operator configuration is **out of scope** for v1.0 and belongs exclusively to Nanocode v2 / Cham-Code.

## What this repository includes
- **Constraint engine (framework-level):** constraint profiles, policy gating, and structured prompt templates.
- **Recovery (“tragedy”) strategies:** bounded fallback/degrade/retry patterns for predictable behavior.
- **Certification artifacts:** run traces describing which constraints were applied, waived, or failed.
- **Model adapters:** OpenAI, Anthropic, and custom HTTP backends to keep workflows portable.
- **Local stack:** FastAPI backend + model server layer + frontend playground UI + dev scripts.

## What this repository explicitly does NOT include (Non-Goals)
Nanocode v1.0 does **not** provide:
- A closed or sovereign execution kernel
- Self-modifying instruction graphs or autonomous mutation
- Persistent internal identity/state beyond explicit external storage you configure
- Kernel-level rule authority independent of the user’s runtime configuration
- Any Cham-Code production kernel components

If a feature requires kernel sovereignty (persistent internal state, autonomous rule enforcement, or self-modifying execution), it belongs to Nanocode v2 / Cham-Code and is out of scope for this repo.

## Relationship to Cham-Code / Nanocode v2.0
- **Nanocode v1.0 (this repo):** open-source orchestration framework and reference implementation.
- **Nanocode v2.0 kernel (Cham-Code):** proprietary, closed-source kernel not distributed here.

Nanocode v1.0 runs standalone; it does not require Cham-Code. This separation is intentional and enforced to prevent licensing ambiguity and architectural drift.

## Prerequisites
- Python 3.10+ (or the version used by this project)
- Node.js 20.19+ (for the frontend) and npm
- Git
- (Optional) a Python virtual environment
- An API key for at least one model provider:
  - OpenAI (e.g. gpt-4o)
  - Anthropic
  - Or a compatible custom model server

## Quickstart
```bash
git clone https://github.com/<your-org>/nanocode-local-main.git
cd nanocode-local-main

# Backend dependencies
python3 -m pip install -r requirements.txt

# Frontend dependencies
cd frontend
npm install
cd ..

# Configure providers (from repo root)
./configure_nanocode.sh

# Start everything locally
./dev.sh


Security Notes
Never commit .env or any API keys to source control.
Review configure_nanocode.sh to understand how your .env is written.
When using remote model providers (OpenAI, Anthropic), ensure your usage complies with their terms.
