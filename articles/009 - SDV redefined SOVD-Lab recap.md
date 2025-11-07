---
title: "Demystifying Diagnostics – S.D.V. redefined: From Software-Defined to Standards-Driven, Service-Defined, Self-Diagnosing"
date: 2025-11-07
layout: default
tags: [SDV, SOVD, ASAM, ISO17978, AUTOSAR, OpenSOVD, diagnostics, OpenAPI, Kaizen, Aikido]
---

# S.D.V. redefined — From Software-Defined to Standards-Driven, Service-Defined, Self-Diagnosing  
*Aikidō, Kaizen, and the practice of continuous improvement in vehicle diagnostics*

In Aikidō, we learn to blend with energy, not fight it.  
Kaizen teaches us to improve a little, every day.  

Working on **service-oriented vehicle diagnostics (SOVD)** these past months, I’ve found both principles essential:  
blend with the “energy” of existing tools, standards, and organizations; and iterate code-first, test-driven, small steps toward something clearer and more humane.

SOVD sits right at that hinge of change. It acknowledges that modern vehicles are **networks of software and services**, not just collections of ECUs.  
It moves diagnostics toward **web-style, self-describing APIs** that scale from proximity to remote and in-vehicle use cases — without throwing away what works today.

---

## Two months of *sovd-lab*: what we practiced and what we learned

I’ve set up a lean, code-first sandbox with:
- A minimal SOVD gateway skeleton  
- A simple “classic diagnostics adapter” bridging to legacy flows  
- A thin client for smoke tests  
- CI basics and a few end-to-end scenarios (fault read, measurement, routine call)

Cadence is key to maintaining motivation and learning through practice:  
~3 PRs merged (with my dear bots helping),  
~0 issues closed (maybe I need to add templates first!),  
~3 contributors (mostly insightful LinkedIn comments that triggered changes).  

Weekly learning demos kept me honest.  

I focused on **TDD workflows**, adding test vectors before feature stubs, and enforcing **small PRs + pre-commit hooks**.  
API surfaces followed **OpenAPI descriptions**, keeping app layers **tech-stack-agnostic** — swappable runtimes, pluggable transport adapters, and fixtures hardening the contract, not the plumbing.

What surprised me most:  
> The fastest wins came from **self-describing endpoints** and **stateless calls** — they simplify back-end integration and reduce hidden coupling.  

That aligns beautifully with the spirit of SOVD’s use of REST/HTTP, JSON, and OAuth-style flows, even if I haven’t yet added proper security (coming soon 😄).

---

## S.D.V. — alternative meanings that shaped my approach

In automotive we all say “Software-Defined Vehicle.”  
But over the last months, I’ve started hearing “SDV” differently:

### **a) Standards-Driven Vehicle**
Without shared APIs, every company will re-invent “diagnostics via web.”  
SOVD (standardized first at ASAM, now progressing in ISO 17978) offers a **common, modern substrate** — HTTP/REST, JSON, OpenAPI, OAuth — spanning proximity, remote, and in-vehicle diagnostics, while coexisting with UDS via translation.

### **b) Service-Defined Vehicle**
In a service-oriented architecture, diagnostics becomes a service: **discoverable, versioned, testable, observable**.  
AUTOSAR Adaptive explains how SOVD Gateway, Diagnostic Manager, and UDS translation tie together in practice, while the middleware beneath (SOME/IP, increasingly DDS via ara::com) carries the bits.

### **c) Self-Diagnosing Vehicle**
If the API is self-describing and securely reachable, we can finally **shift left** — enabling continuous monitoring, predictive workflows, and safe self-tests.  
SOVD’s stateless model lowers integration barriers with IT backends, but I believe *Self-Diagnosing* should stay focused on **meaningful vehicle data for users**, not just protocol details.

### **d) Stack-Decoupled Vehicle**
Diagnostics apps — inside or outside the car — should **survive stack churn**.  
That means **code-first contracts**, **test doubles for adapters**, and **semantic payloads** the apps can reason about, regardless of whether the node runs Adaptive or sits behind a Classic Adapter.

---

## Standards and open source — the ecosystem is moving

- **ASAM SOVD** defines a unified API for diagnostics across HPCs and ECUs, spanning proximity, remote, and in-vehicle use.  
- **ISO 17978** continues the work as a multi-part standard (general principles, use cases, API).  
- **AUTOSAR Adaptive** provides the reference architecture for SOVD components and their evolution.  
- **OpenSOVD (Eclipse Automotive)** brings open-source governance and code-first experimentation.

Each piece moves us toward a **shared diagnostic language** that bridges OEMs, suppliers, and open-source contributors.

---

## From silos to flows

Real value emerges when a diagnostic app connects **faults with functional telemetry** — correlating real-world context, observability, and continuous improvement loops.

SOVD’s stateless, self-describing pattern helps bridge SDV software factories and aftersales/fleet operations — the missing link between *development* and *field*.  
Diagnostics becomes part of the software flow.

---

## The human body analogy

Think of vehicle components as organs and systems — and **SOVD as the nervous system interface**.

- Local reflexes = quick checks and routine calls  
- Remote specialists = authenticated experts triaging logs, running targeted tests, advising interventions  

That’s the promise of standardized, secure **remote diagnostics at scale**.

---

## Aikidō × Shu-Ha-Ri × Kaizen

**Shu (守)** — Follow: respect standards, implement the basics faithfully, stay IP-friendly.  
**Ha (破)** — Break: isolate seams (adapters, protocols) to experiment safely.  
**Ri (離)** — Transcend: let logic focus on outcomes — resilience, clarity, user trust.  
**Kaizen (改善)** — Improve daily: treat every PR as a chance to reduce friction and increase observability.

---

## Next steps for *sovd-lab*
1. Add a “monitoring-first” sample (faults + measurements → time-series backend)  
2. Expand Classic Adapter tests (UDS mapping scenarios)  
3. Publish a kata showing TDD against an OpenAPI contract  
4. Add proper security and Auth + Auth  
5. Provide PR/Issue templates for contributors  
6. Post short demo clips to lower entry barriers  

---

If you see value in a **standards-driven, service-defined, self-diagnosing** approach — let’s pair up on a scenario.  
I’m especially keen to collaborate on **stack-agnostic diagnostics apps** and **owner-facing UX experiments**.

> *Demystifying diagnostics means staying curious while standards, stacks, and skills evolve — one test, one improvement, one connection at a time.*
