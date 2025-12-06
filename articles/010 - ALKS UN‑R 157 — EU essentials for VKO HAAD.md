---
title: "ALKS (UN-R 157) — EU essentials for VKO HAAD"
date: 2025-12-06
tags: [ALKS, UN-R157, EU, Type-Approval, DSSAD, SMS, SOVD]
summary: Paraphrased, IP-safe notes mapping ALKS obligations to approval and in-service evidence, with synthetic ToC/MRM event examples integrated in sovd-lab.
---

# ALKS (UN-R 157): EU essentials for VKO HAAD

This article is the first step of a new experiment: transforming my VKO HAAD regulatory reading into **small, verifiable, IP-safe artifacts** that engineers can reuse or adapt.

I’ve spent the last weeks reading and summarizing UNECE regulations, especially **UN-R 157**, which defines ALKS — the Automated Lane Keeping System for L3 driving.  
Instead of keeping notes hidden in a folder, I want to turn them into open, Apache-friendly content:

- *Regulatory Master Table entries*  
- a compact *EU “ALKS essentials” Action Pack*  
- *synthetic JSON evidence* (ToC / MRM) implemented in `sovd-lab`  
- clear mappings toward *DSSAD* and *SMS* expectations  

The goal:  
**connect Reg → Behaviour → Evidence** in a lightweight and transparent way.

---

# Why ALKS matters for VKO HAAD

ALKS is the first UNECE regulation enabling L3 automated driving in Europe.  
From a VKO perspective, three elements define both system behaviour and evidence obligations:

### **1) ODD – Operational Design Domain**  
ALKS must declare explicitly where it drives, which boundaries apply, and how those boundaries are monitored.

### **2) ToC – Transition of Control**  
The system must detect when the driver needs to take over, warn them promptly, and follow escalation steps.

### **3) MRM – Minimum Risk Manoeuvre**  
If neither the ADS nor the driver can continue safely, ALKS must execute a defined MRM.

These pillars appear across multiple approval layers:  
Type-approval → SMS governance → in-service monitoring → evidence retention.

---

# Key acronyms (IP-safe, paraphrased)

- **HAAD** — Highly Automated Autonomous Driving  
- **ODD** — Operational Design Domain  
- **ToC** — Transition of Control  
- **MRM** — Minimum Risk Manoeuvre  
- **DSSAD** — Data Storage System for Automated Driving  
- **SMS** — Safety Management System  

---

# Compliance mapping (paraphrased)

Below is an IP-friendly, non-verbatim mapping of ALKS obligations toward approval/in-service evidence.

| Topic | Homologation | Type Approval | SMS | DSSAD | In-Service |
|-------|--------------|---------------|-----|--------|-----------|
| **ODD declaration** | Context document | Declared boundaries & limits | Governance & change control | ODD mode flag | Operational field checks |
| **ToC timing / HMI** | — | Escalation behaviour | Operating procedure | ToC record | Event review |
| **MRM behaviour** | — | Start conditions & safe stop logic | Safety governance | MRM record | Incident review |
| **Speed / Lane Change** | — | Conditions & limits for special manoeuvres | Change mgmt | Mode transitions | Field observation |
| **Logging & Records** | — | Sufficiency of evidence | Retention policy | Data types | Reporting cadence |

This structure anticipates later additions for UN-R 155/156 and EU GSR.

---

# Synthetic evidence in `sovd-lab`

To avoid any proprietary information, I created **synthetic ToC and MRM events**, fully decoupled from real data and validated through local schemas.

### Evidence examples (generated or TODO stubs)

- `sovd-lab/docs/haad/compliance-mapping/evidence/2025-12-06_toc_demo.json`  
- `sovd-lab/docs/haad/compliance-mapping/evidence/2025-12-06_mrm_demo.json`

### Event schemas (AJV-friendly)

- `controlTransitionRequest.schema.json`  
- `minimumRiskManeuver.schema.json`  

### Rationale

These JSON events let us illustrate:

- how a ToC begins  
- how escalation evolves  
- when an MRM is triggered  
- which DSSAD-relevant fields appear  

All without touching real vehicle logs.

---

# A minimal ToC → MRM flow (synthetic)

ALKS active → detects external limit → ToC issued → driver fails to respond →
MRM triggered → vehicle reaches safe stop → DSSAD records → SMS review

This flow is implemented in the upcoming small Kotlin service (`event-generator/`) inside `sovd-lab`.

---

# PlayWithDocker / devcontainer concept

The idea is simple:

1. A tiny Kotlin service emits a `controlTransitionRequest` event  
2. If not “handled” within a synthetic timeout, an `mrmTriggered` event follows  
3. Both events are saved under `evidence/`  
4. Schema validation runs via `ajv` in local or CI  
5. The Action Pack references the corresponding evidence

The service does *not* replicate real ADS logic — it demonstrates **traceability**, not performance.

---

# Connecting ALKS → SOVD → DSSAD/SMS

ALKS obligations (paraphrased) require certain conditions to be:

- **declared** (ODD, manoeuvres),  
- **monitored** (ToC timing, driver engagement),  
- **recorded** (events, mode changes),  
- **retained** (evidence rules).  

DSSAD provides placeholders for:

- mode transitions  
- driver requests  
- control transfers  
- system overrides  
- MRM start and completion  

SOVD-Lab provides a playground for attaching synthetic traces to these concepts and demonstrating how evidence could appear in a minimal environment.

---

# What’s next: UN-R 155/156 interplay

For the next chapter of this series, I’ll work on:

- cybersecurity and software-update touchpoints  
- integrating paraphrased obligations into the master table  
- extending the Action Pack with update-event examples  
- creating a first **DSSAD minimal record set** checklist  
- mapping evidence to SMS governance  

Content will remain lightweight, paraphrased, and Apache-2.0 friendly.

---

"Content licensed under Apache-2.0; paraphrase-only; no quotations from paywalled standards."

