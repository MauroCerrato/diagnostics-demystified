---
layout: default
title: 005 - Inside OBD-II protocol implementation alternatives and OBD-II quirks real-life feedbacks
description: "Part of the Diagnostics Demystified series by Mauro Cerrato"
---

# 🚀 My experiences in OBD-II protocol implementations

How can I describe my experiences on OBD-II protocol alternatives?  
Let´s use a mix of **technical details** and the real-life **“incidents”** that I had the “unluck” to survive over many years of owning, driving and repairing cars.

---

## 🚗 Car systems alternatives

Here’s the list of OBD system variants I have been in contact with:

- **Euro 1** — 0.700L, 2 cylinders petrol engine  
  Single ECU, responsible for a 3-way catalytic system.  
  “Custom” Packard-style connector visible in the engine bay.  
  IPC with non-standard lamps.

- **Euro 3** — 1.4L, 4 cylinders petrol engine  
  ECU in the engine bay, **standard OBD-II plug** (below steering wheel).  
  MIL + additional lamps and indicators.

- **Euro 4** — 1.2L dual fuel (petrol + CNG)  
  Two ECUs:  
  - 1x resin-sealed plastic ECU for CNG  
  - 1x metal ECU for petrol  
  OBD-II plug under steering wheel, MIL and additional lamps.

- **Euro 5** — 1.4L dual fuel (petrol + LPG)  
  Two ECUs:  
  - 1x LPG ECU on tank  
  - 1x metal ECU in engine bay for petrol  
  Standard OBD-II plug and MIL.

- **Euro 6** — 1.0L petrol, 3 cylinders  
  Single ECU, standard OBD-II plug.  
  Tablet-style HMI, MIL as a software-controlled icon.

---

## ⚠️ Quirks & pitfalls of OBD-II

**Spoiler:** OBD-II often did **not** help me understand the real issues.

### Euro 1
- **Quirk:** No warning lamp for engine failure.  
- **Incident:** Starting issues. Diagnostic tool: *“no errors”*. Case closed.  
- **Reality:** After days, engine stopped completely.  
> I saw the engine open: one cylinder shiny clean from coolant leak.  
👉 No lamp ever warned me.  
💡 **Lesson learned:** Early OBD systems were blind. Only mechanical expertise found the root cause.

---

### Euro 3
- **Quirk:** Harsh winter morning, engine refused to crank.  
- **HMI:** MIL on + red STOP flashing.  
- **Workshop:** Manufacturer’s diagnostic tool showed *“unknown DTC”*.  
  After a week, HQ had to update the tool to reveal the root cause.  
👉 HMI helped, but **data was incomplete**.  
💡 **Lesson learned:** Diagnostics tools are only as good as their last update.

---

### Euro 4
- **Incident:** Car started on petrol but failed to switch to CNG. MIL blinked shortly then went off.  
- **Workshop:** No stored data. No permanent DTC.  
  → They replaced CNG system **piece by piece** until finding the real fault.  
> The CNG ECU itself had “cooked” outputs — resin + heat = failure.  
💡 **Lesson learned:** Sometimes the ECU is the problem, not the sensor.

---

### Euro 5
- **Incident:** After LPG refueling, engine stopped after a few meters.  
- **Symptoms:** No MIL, no warning. Car dead.  
- **Workshop:** Generic scantool showed multiple DTCs, none relevant.  
> A strange humming was heard in the engine bay just before the shutdown.  
👉 Conclusion: “Sudden death” of the LPG ECU.  
💡 **Lesson learned:** No predictive diagnostics = no chance to anticipate catastrophic ECU failures.

---

### Euro 6
- **Owned for 12 months.**  
- **Result:** No major issues from engine/after-treatment yet.  
Other “annoying issues” … story for another article. 😉

---

## 🔧 OBD-II quirks (protocol, DTCs, voltage)

From my own work on ECUs and diagnostics tooling, here’s what I observed:

### Protocol recognition
- Euro 1: “special” connectors, single-wire K-Line, power and ground.  
  → Many technicians didn’t trust the tools, relying only on mechanics.  
- Euro 3+: standardized CAN, power, ground, DoIP (Ethernet).  
  → Easier, but still dependent on the tool’s implementation.

💡 **Lesson learned:** Standardization helped, but interpretation still varied per workshop.

---

### DTC status byte
- ISO 15031 does **not** mandate info like *“active/inactive”*.  
- Euro 3 + 4 cars gave **no useful data at readout time**.  
→ Repair required OEM expertise, not just generic tools.  

💡 **Lesson learned:** Same DTC ≠ same meaning. Context is king.

---

### Voltage level issues
- Old ECUs required **>11V stable voltage** to store or process data.  
- Weak batteries → incomplete DTCs, missing memory writes.  
- Possible cause for Euro 5 ECU’s sudden blackout.  

💡 **Lesson learned:** Diagnostics are only as reliable as the power supply.

---

## 🔮 What’s next

In the coming weeks, I’ll expand **SOVD-Lab** with more software-oriented approaches:  

- 🧩 New `obd2-sovd-sim` scenarios  
- 🔍 Modern REST-ful debugging tools  
- 📊 Practical “trial & error” experiments  

> Stay tuned: the old quirks of OBD-II may still have something to teach us in the era of SOVD.

---

💡 BONUS: Just to wrap it up, here’s my summary table of OBD-II quirks & pitfalls so far:

### 🔎 Summary of my OBD-II stories

| Euro | Engine / Fuel system      | Incident / Quirk                                | Lesson learned                                  |
|------|---------------------------|-------------------------------------------------|-------------------------------------------------|
| 1    | 0.7L, 2 cyl, petrol       | No warning lamp, head gasket failure undetected | no diagnostics, only mechanical skills saved it |
| 3    | 1.4L, 4 cyl, petrol       | MIL + STOP lamp, “unknown DTC” until OEM update | Tools only work if updated                      |
| 4    | 1.2L, dual fuel (CNG)     | Failed switch to CNG, no data stored            | Sometimes ECU itself is the problem             |
| 5    | 1.4L, dual fuel (LPG)     | Engine stopped after refuel, many useless DTCs  | No predictive diag = sudden ECU death           |
| 6    | 1.0L, 3 cyl, petrol       | No major faults in 12 months                    | TBD, more stories to come…                      |

👉 Now it’s your turn: what’s your worst OBD-II horror story?
Wrong DTCs, cryptic logs, “no trouble found” but the car still dead… I’m curious to hear them all.

⚠️ Spoiler alert: this is just the beginning. I’m preparing the series
“My granny could understand that too…” — real-life diagnostics stories told in plain words. Stay tuned! 🚀

---

# 🚀 From Zero to Go (in a container): lessons from SOVD-Lab on PWD Play-with-Docker (Wed tech)

This week, SOVD-Lab gained a new service: a tiny **Go microservice** that serves `/healthz` and `/data/ident/vin`.  
Sounds simple? The real learning started once I moved from “hello world” to a **four-node simulation** on [Play with Docker](https://labs.play-with-docker.com/).

### Why I did this
My goal was pragmatic:  
- add a Go service without installing runtimes locally,  
- strengthen observability and health,  
- keep the workflow copy-paste simple.

### What broke (and how I fixed it)
- **Healthchecks**: distroless images lack `curl` → healthchecks fail. Fixed with Alpine + `apk add curl`.  
- **YAML gotchas**: unquoted URLs, CRLF line endings → “mapping values not allowed” errors. Fixed by quoting and normalizing line endings.  
- **Go toolchain**: no local install; solved with two containerized paths (`golang:1.22-alpine` bind mount or `apk add go`).  
- **Gateway mystery**: “container up but unreachable” until I forced bind to `0.0.0.0:8081`.

Each fix took minutes instead of days once I understood the pattern.

### What I shipped
✅ [A working Go service in SOVD-Lab](https://github.com/MauroCerrato/sovd-lab/tree/main/services/go-capabilities)  
✅ [Multi-host](https://github.com/MauroCerrato/sovd-lab/blob/main/compose.yaml) `compose.yaml`  
✅ [Copy-paste commands for Play-with-Docker](https://github.com/MauroCerrato/diagnostics-demystified/blob/main/articles/resources/005-annexes/commands.md)

### What’s next
- CI with OpenAPI validation  
- OpenTelemetry traces + metrics  
- Updated OBD-II scenarios: quirks, pitfalls and user stories

> Every bug became a lesson. Debugging on PWD turned out to be my fastest way to learn Go *and* sharpen my container troubleshooting skills.
