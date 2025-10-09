---
title: How to Diagnose a Generic, Configurable Braking System Without Losing Sight of SOTIF
author: Mauro Cerrato
series: Diagnostics Demystified
date: 2025-10-10
tags: [SOTIF, ISO 21448, ISO 34505, ISO 20730, diagnostics, braking systems, safety]
layout: post
---

## Introduction

Modern braking systems are no longer just mechanical—they're software-defined, sensor-driven, and safety-critical. Diagnosing them requires more than fault codes: it demands understanding of standards like **SOTIF**, best practices like **FMEA**, and **service-oriented diagnostics**.

## Why FMEA Is Not Just a Document

FMEA (Failure Mode and Effects Analysis) is often treated as paperwork. But in safety-relevant diagnostics, it's the blueprint for runtime fault detection, mitigation, and de-validation.

Here’s a simple way to explain it:

- **Failure Modes**: What could go wrong?
- **Effects**: What happens if it does?
- **Likelihood & Detection**: How often and how easily can it be found?

In braking systems and ADAS, this simple methodology becomes a complex source of trade-offs and reality checks.

## Safety Evolution: Euro 1 to Euro 6

| Euro Level   | Safety Features          | Horror Story                                    |
| Euro         | None                     | Brake failure undetected due to lack of sensors |
| Euro 2       | Basic ABS                | ABS valve stuck, no diagnostics                 |
| Euro 3       | ABS + ESP                | ESP logic disabled due to missing config        |
| Euro 4       | ABS + ESP + EBD          | Speed sensor intermittency, no fault raised     |
| Euro 5       | Full suite               | Fault raised but not de-validated               |
| Euro 6       | Redundant logic          | Fault masked by fallback logic                  |

## My Experience: Diagnostics Without Standards (1998–2004)

Back then, I was tasked with building a configurable diagnostics test system for braking systems in commercial vehicles (Euro 3–5). Each vehicle had different ECUs, sensors, actuators, and wiring layouts.

My system could:
- Detect vehicle type
- Choose the best test sequence
- Stimulate the ECU to override fault monitoring
- Harmonize diagnostics protocols (KWP2000, UDS)
- Control a wireless HMI and roller test bench

It was creative, hands-on, and deeply integrated with manufacturing realities.

## Standards in Focus

While my early work predated formal standards, today’s diagnostics landscape is shaped by:

### ISO 21448 (SOTIF) — Safety of the Intended Functionality

Published between 2019–2022, SOTIF addresses safety risks that arise not from system faults, but from limitations in functionality or environmental perception. For braking systems, this includes behavior under ambiguous sensor inputs or unexpected road conditions.

### ISO 20730 — ePTI Diagnostics for Periodic Inspection

Finalized in 2022, this standard defines diagnostics for vehicles during periodic inspections. It introduces standardized Diagnostic IDs (DIDs) and UDS services to assess system health. In SOVD-Lab, I will simulate some of these DIDs to validate braking system readiness.

### ISO 34505 — Scenario-Based Test Case Generation

Expected in 2025, this standard formalizes how to derive test cases from real-world driving scenarios. My goal is to align SOVD-Lab’s braking system simulations with this methodology, especially for fault injection and response validation.

> Note: All descriptions are paraphrased for educational purposes. For official definitions, refer to ISO.org or your organization's licensed access.

## Diagnosing Safety-Relevant Events

Events I could actively stimulate and monitor:

- **Speed sensor signal loss**: broken or intermittent wiring
- **ABS valve activation failure**: wiring mismatch
- **ESP logic disabled**: missing configuration/calibration

Real-world questions challenged my assumptions:

- Why does the vehicle spin on gravel despite no fault codes?
- Why is there brake fluid leakage with no warning lamp?

These questions pushed me to rethink diagnostics beyond documentation.

## A New Methodology

I proposed a layered approach:

### 0.1 Define Braking System Architecture

- **Sensors**: wheel speed, steering angle
- **Actuators**: ABS valves, brake calipers/drums
- **ECUs**: logic for monitoring, overriding, configuration

### 0.2 Define Test System Architecture

- F1: Detect physical OBD-II plug (Euro 4+)
- F2: Scan ECU address and protocol (UDS service 0x3E, 0x22)
- F3: Read vehicle safety system config (ISO ePTI)
- F4: Check fault events (UDS service 0x19)
- F5: Compare live data with fault logic
- F6: Stimulate system via IOControl (UDS service 0x2F)

### 1. Define Fault/Event Types

- Mechanical faults (e.g. misaligned sensors)
- Electrical faults (e.g. open/short circuits)
- Hydraulic faults (e.g. low fluid pressure)
- Logical faults (e.g. misconfigured ECU software)

### 2. Map to FMEA Documentation

Discussions focused on:
- Probability of fault occurrence
- Severity of fault effects
- Realistic vs unrealistic fault scenarios

I’ve seen all kinds of “non-monitored” faults — no DTCs, no lamps, but real safety risks.

### 3. Create Diagnostics Test Functions

Today, these would be service endpoints. In SOVD-Lab, I model braking systems as components with subcomponents and apps (ABS, ESP). The challenge: which app monitors diagnostics, and how is fault status exposed?

### 4. Validate via Integration Tests

Use UDS or SOVD sequences to:
- Observe fault codes
- Compare signal values
- Stimulate one part and observe the other

### 5. Use Healthchecks and Orchestration
After stimulation, new faults may be stored. Always end with fault clearing, ECU reset, and post-drive readback.

## Conclusion

Safety diagnostics is not just about detecting faults—it’s about understanding intent, configuration, and runtime behavior.

With legacy protocols (KWP2000, UDS), I built complex but effective test systems. With SOVD-Lab, I’m recreating this using service-oriented design, microservices, and modern standards.

I invite safety experts to reflect:  
**Is it now easier with SOTIF to address real-world problems and build more functionally aware braking systems—or not?**

---

## ⚠️ Disclaimer

This article reflects my personal experience and interpretation of safety diagnostics practices, including references to ISO standards such as ISO 21448 (SOTIF), ISO 20730 (ePTI), and ISO 34505 (scenario-based testing).  
No part of this article reproduces or quotes proprietary ISO content. All descriptions are paraphrased for educational and illustrative purposes only.  
For official definitions and usage, please consult https://www.iso.org/ or your organization's licensed standards library.