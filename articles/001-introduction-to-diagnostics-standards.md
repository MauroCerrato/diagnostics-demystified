---
layout: default
title: 001 — Introduction to Automotive Diagnostics Standards
---

# Introduction to Automotive Diagnostics Standards  
*What they are, and why they matter.*

**Why standards exist**  
Standards are shared agreements on “how we do things,” so teams can interoperate safely and repeatably. In diagnostics, they make sure tools and ECUs can discover capabilities, read/write data, manage faults, and execute routines in predictable ways.

**A quick map of today’s landscape**  
- **UDS (ISO 14229)** defines a common set of diagnostic services many ECUs speak today.  
- **Transport & networks** like **CAN (ISO 11898)** and **CAN‑TP (ISO 15765‑2)** move UDS messages; **DoIP (ISO 13400)** brings IP/Ethernet speed.  
- **OBD/Emissions** families (e.g., **ISO 15031**, **SAE J1979**, **SAE J2012**) ensure inspection tools can read standardized data and trouble codes.  
- **WWH‑OBD (ISO 27145)** harmonizes emissions diagnostics globally.  
- **SOVD** (service‑oriented diagnostics) uses **HTTP/REST + JSON + OAuth** to work natively with modern HPCs, on‑board/off‑board, and in the cloud; its ISO track is **ISO 17978**. [1](https://www.roboticlab.eu/homelab/_media/en/av/autonomy_and_autonomous_systems/autonomy/sae_j3016_levels_of_automation_graphic.pdf)[2](https://github.com/eclipse-opensovd/.eclipsefdn)

**Where SOVD fits**  
SOVD doesn’t delete UDS; it complements it. You can keep UDS for legacy flows and use SOVD for web‑style discovery, data access, logging, and routine execution—bridging via gateway/adapters when needed. [3](https://www.asam.net/standards/detail/sovd/)

**How to learn this quickly**  
Each Saturday I post a short explainer here and a runnable example in **SOVD‑Lab**—so you can try it in minutes:
- Run the compose stack  
- Call a few endpoints  
- See faults/data/routines in action

> **Rate this article** or **propose a scenario**: open an issue using the templates in this repo.

**References**  
ASAM SOVD overview; ISO 17978 draft page; AUTOSAR SOVD explainer. [1](https://www.roboticlab.eu/homelab/_media/en/av/autonomy_and_autonomous_systems/autonomy/sae_j3016_levels_of_automation_graphic.pdf)[2](https://github.com/eclipse-opensovd/.eclipsefdn)[3](https://www.asam.net/standards/detail/sovd/)
