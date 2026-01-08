# Nanocode v1.0  
**Open-Source AI Orchestration & Structural Observability Framework**

## Overview

Nanocode v1.0 is an **open-source, local orchestration and observability framework** for **model-agnostic AI workflows**.

Its purpose is to make AI-driven systems **legible, traceable, and structurally inspectable** by recording how decisions and actions occur step by step, rather than treating AI behavior as an opaque black box.

Nanocode v1.0 focuses on **execution transparency and structured workflow orchestration**. It does **not** act as a sovereign execution kernel and does **not** enforce authority over AI actions.

---

## What Nanocode v1.0 Does

Nanocode v1.0 provides:

- Structured orchestration of AI workflows across models and tools  
- Deterministic execution traces capturing ordered steps, transitions, and outcomes  
- Constraint-aware instrumentation, recording which constraints were configured, evaluated, or bypassed  
- Audit-ready artifacts that allow workflows to be reconstructed and inspected after execution  
- Model-agnostic adapters to keep workflows portable across providers  

Nanocode v1.0 **observes and documents behavior** — it does not govern or prevent it.

---

## Core Capabilities

### 1. Constraint Awareness (Framework-Level)

Nanocode v1.0 supports **operator-defined constraints** as part of workflow configuration, including:

- Constraint profiles  
- Conditional branching logic  
- Structured prompt templates  

These constraints are:

- Explicit  
- Configurable  
- Fully observable in execution traces  

They are **not sovereign**, **not autonomous**, and **not enforced at the execution boundary**.

---

### 2. Recovery (“Tragedy”) Strategies

Nanocode v1.0 includes bounded recovery patterns to improve predictability and resilience, such as:

- Retry strategies  
- Fallback paths  
- Graceful degradation logic  

These strategies are deterministic and traceable, allowing operators to see exactly how and why recovery paths were taken.

---

### 3. Execution Evidence & Trace Artifacts

Nanocode v1.0 produces **execution evidence**, including:

- Ordered run traces  
- Tool and model invocation records  
- Constraint evaluation outcomes  
- Recovery path selection  

These artifacts support debugging, audit workflows, and post-incident analysis.  
They provide **evidence**, not certification or enforcement.

---

### 4. Model Adapters

Nanocode v1.0 includes adapters for:

- OpenAI  
- Anthropic  
- Custom HTTP-compatible backends  

This keeps workflows portable and avoids lock-in to any single model provider.

---

### 5. Local Development Stack

The repository includes a complete local stack for development and experimentation:

- FastAPI backend  
- Model server integration  
- Frontend playground UI  
- Developer scripts and tooling  

Nanocode v1.0 runs fully standalone and does not require any proprietary components.

---

## What Nanocode v1.0 Explicitly Does **Not** Include

Nanocode v1.0 does **not** provide:

- A sovereign or closed execution kernel  
- Autonomous rule enforcement  
- Kernel-level authority over execution  
- Persistent internal identity or state beyond what you explicitly configure  
- Self-modifying instruction graphs  
- Independent rule enforcement outside operator configuration  
- Any Cham-Code or Nanocode v2.0 production kernel components  

If a feature requires **kernel sovereignty**, **autonomous authority**, or **non-bypassable enforcement**, it is intentionally out of scope for this repository.

---

## Relationship to Cham-Code / Nanocode v2.0

- **Nanocode v1.0 (this repository)**  
  Open-source orchestration and structural observability framework.

- **Nanocode v2.0 / Cham-Code**  
  Proprietary, closed-source execution governance kernel.

Nanocode v1.0 does **not** include, embed, or depend on Cham-Code.  
This separation is intentional and enforced to preserve architectural clarity and licensing boundaries.

Nanocode v1.0 is designed to stand on its own as a transparency and orchestration layer.

---

## Prerequisites

- Python 3.10+  
- Node.js 20.19+ and npm (for the frontend)  
- Git  
- (Optional) Python virtual environment  
- API access to at least one model provider:
  - OpenAI  
  - Anthropic  
  - Or a compatible custom model server  

---

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

# Configure providers
./configure_nanocode.sh

# Start everything locally
./dev.sh

