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
Diagnostics over IP/Ethernet for higher bandwidth and remote scenarios. A good fit for HPC‑centric vehicles and large data transfers. (Recent updates emphasize secure transport and network services.) 

**UDS on IP — ISO 14229‑5**  
Runs UDS over IP/Ethernet—useful for fast shop networks or controlled remote diagnostics.

**KWP2000 — ISO 14230 & UDS on K‑Line — ISO 14229‑6**  
Legacy but still relevant for older ECUs/vehicles and specific single‑wire setups.

**WWH‑OBD — ISO 27145**  
Harmonizes emissions diagnostics globally; aligns data and DTCs with SAE definitions so generic tools can read consistent emissions information.
**OBD data & DTCs — ISO 15031, SAE J1979, SAE J2012**  
Defines emissions‑related PIDs/test modes (J1979) and trouble code definitions (J2012), with ISO 15031 providing vehicle↔tool comms alignment.

**Where SOVD comes in (HTTP/REST + JSON + OAuth)**  
SOVD provides a web‑style API across proximity, remote, and in‑vehicle scenarios; the ISO series is **17978**. Many platforms will bridge UDS ↔ SOVD during transition. 

> Want to try it? See **SOVD‑Lab** for a mock gateway + minimal SOVD‑like endpoints.

**References**  
ASAM SOVD overview; ISO 17978 (SOVD) draft; DoIP update references, ISO multiple project references. 
> [2](https://www.asam.net/standards/detail/sovd/)
> [3](https://www.iso.org/standard/85133.html)
> [4](https://www.iso.org/standard/86586.html)
> [5](https://www.iso.org/standard/86587.html)
> [7](https://www.iso.org/standard/13400-2)
> [8](https://www.iso.org/standard/72439.html)
> [9](https://www.iso.org/standard/86384.html)	
> [10](https://www.iso.org/standard/85120.html)
> [11](https://www.iso.org/standard/84211.html)
> [12](https://www.iso.org/standard/76882.html)
> [13](https://www.iso.org/standard/55288.html)
> [14](https://www.iso.org/standard/46273.html)


