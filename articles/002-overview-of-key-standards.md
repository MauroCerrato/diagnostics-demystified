---
layout: default
title: 002 — Overview of Key Diagnostics Standards
---

# Overview of Key Diagnostics Standards
*How they shape vehicle diagnostics today.*

**Why standards matter**  
Diagnostics standards are agreements that ensure vehicles and tools can “speak the same language.”  
They enable the reading of data, exchange of fault codes, and performance of tests across different ECUs and tools—without reinventing the wheel every time.

---

## ISO 14229 — Unified Diagnostic Services (UDS)  
UDS defines a broad set of services that most modern ECUs utilize today, including reading and writing data, managing fault memory, performing software updates, and running system routines.  
Its strength lies in unifying these use cases into one protocol that both vehicles and diagnostic tools can implement consistently.

---

## ISO 13400 — Diagnostics over Internet Protocol (DoIP)  
DoIP brings diagnostics to the Ethernet world. It allows high-speed data exchange, essential for today’s vehicles, where large data sets (e.g., ADAS, infotainment) need to be inspected or updated quickly.  
It also opens the door for remote diagnostics, connecting vehicles and tools through IP networks.

---

## ISO 11898 & ISO 15765 — CAN and CAN-TP  
CAN (Controller Area Network) is the backbone of in-vehicle communication.  
ISO 15765-2 (CAN-TP) enables long diagnostic messages to be split into smaller pieces and reliably transported across the CAN bus.  
Together they make diagnostics over CAN practical—from simple fault code reads to full firmware updates.

---

## SAE J1979 & J2012 — OBD-II Test Modes and Trouble Codes  
These standards define how emission-relevant data can be retrieved and how fault codes (DTCs) are structured.  
Every scan tool in a workshop relies on them, ensuring mechanics can read codes like “P0300” and know what they mean, regardless of the vehicle brand.

---

## ISO 27145 — WWH-OBD  
World-Wide Harmonized OBD is a step toward global emissions compliance.  
It reuses core UDS services but defines a harmonized data set, so inspection authorities worldwide can rely on consistent diagnostic results.

---

## ISO 14230 & ISO 14229-6 — KWP2000 and UDS on K-Line  
Before CAN and Ethernet, K-Line was the workhorse of diagnostics.  
Many older vehicles still use it, and newer standards like UDS were even adapted to run on top of K-Line.  
It shows how diagnostic concepts evolve while ensuring backwards compatibility.

---

## ISO 14229-5 — UDS on IP  
As Ethernet adoption grows, UDS itself has been extended to run over IP networks.  
This combination allows a smooth transition: legacy UDS use cases, but with high-speed transport.

---

## ISO 15031 & SAE J1930 — Language and Interfaces  
ISO 15031 defines how vehicles and external equipment should communicate, while SAE J1930 standardizes the vocabulary.  
Having a common terminology is as important as having a common protocol: it avoids misinterpretations across brands, regions, and tools.

---

**Putting it all together**  
This collection of standards forms the foundation of today’s diagnostics.  
From legacy K-Line systems to modern DoIP setups, from emission testing to advanced data services, they ensure interoperability, compliance, and innovation across vehicle types and regions.

Diagnostics is not about one single protocol—it’s about connecting the dots.  
Understanding how these standards fit together helps both engineers and technicians build tools and workflows that actually work.

---

💻 *Runnable demos and simplified scenarios are available in my [SOVD-Lab](https://github.com/MauroCerrato/sovd-lab).*


