---
layout: default
title: 002 — Overview of Key Diagnostics Standards
---

# Overview of Key Diagnostics Standards  
*Brief descriptions and why they matter.*

**UDS — ISO 14229**  
Today’s workhorse for off‑board and in‑vehicle diagnostics. It standardizes service families (sessions, data read/write, security, routines), so tools and ECUs interoperate across brands. (Transports below move these messages.)

**CAN & CAN‑TP — ISO 11898 / ISO 15765‑2**  
CAN is the real‑time vehicle bus; CAN‑TP segments large diagnostic payloads into frames. Still critical for in‑vehicle UDS traffic.

**DoIP — ISO 13400**  
Diagnostics over IP/Ethernet for higher bandwidth and remote scenarios. A good fit for HPC‑centric vehicles and large data transfers. (Recent updates emphasize secure transport and network services.) [4](https://genorma.com/en/standards/iso-awi-17978-1)

**UDS on IP — ISO 14229‑5**  
Runs UDS over IP/Ethernet—useful for fast shop networks or controlled remote diagnostics.

**KWP2000 — ISO 14230 & UDS on K‑Line — ISO 14229‑6**  
Legacy but still relevant for older ECUs/vehicles and specific single‑wire setups.

**WWH‑OBD — ISO 27145**  
Harmonizes emissions diagnostics globally; aligns data and DTCs with SAE definitions so generic tools can read consistent emissions information. [5](https://github.com/eclipse-opensovd/website)
**OBD data & DTCs — ISO 15031, SAE J1979, SAE J2012**  
Defines emissions‑related PIDs/test modes (J1979) and trouble code definitions (J2012), with ISO 15031 providing vehicle↔tool comms alignment.

**Where SOVD comes in (HTTP/REST + JSON + OAuth)**  
SOVD provides a web‑style API across proximity, remote, and in‑vehicle scenarios; the ISO series is **17978**. Many platforms will bridge UDS ↔ SOVD during transition. [1](https://www.roboticlab.eu/homelab/_media/en/av/autonomy_and_autonomous_systems/autonomy/sae_j3016_levels_of_automation_graphic.pdf)[2](https://github.com/eclipse-opensovd/.eclipsefdn)

> Want to try it? See **SOVD‑Lab** for a mock gateway + minimal SOVD‑like endpoints.

**References**  
ISO 17978 (SOVD) draft; ASAM SOVD overview; DoIP update references. [2](https://github.com/eclipse-opensovd/.eclipsefdn)[1](https://www.roboticlab.eu/homelab/_media/en/av/autonomy_and_autonomous_systems/autonomy/sae_j3016_levels_of_automation_graphic.pdf)[4](https://genorma.com/en/standards/iso-awi-17978-1)
