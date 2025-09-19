---
layout: default
title: 003 — The Evolution of Diagnostic Standards
---

# The Evolution of Diagnostic Standards  
*How they have changed over time.*

Automotive diagnostics has never stood still. Standards evolve alongside vehicles, making sure tools and ECUs can “speak the same language” — no matter the network, the use case, or the decade.  

This article gives a high-level view of how diagnostics standards have developed, from **UDS over multiple physical layers** to **connected vehicle architectures**, **software-oriented diagnostics**, and today’s shift toward **SOVD**. We’ll also look at how **CI/CD practices** and **open authentication** are shaping the future.

---

## Before diagnostics standards
What did diagnostics look like before 2006?  

I started working in 1998 and at that time there was practically no fully standardized hardware, no common communication interface, no reliable transport protocols, and no reusable application components.  

All I had was a supplier-specific spec, a laptop, a RS232 cable, a quirky vehicle interface, and a handful of banana plug wires.  

It was a very funny “trial and error” period, until one day I had both a German OEM ECU and a French OEM ECU on my desk — both claiming to implement the new ISO KWP2000 diagnostics standard.  

Looking at them side by side was amusing: the same outline in the spec, but two very different “dialects” of the so-called ISO standard.  

Then a colleague asked me if I wanted to join the ISO working group that was about to publish the first ISO version of the UDS protocol. It was 2007, and suddenly I was among a great group of experts discussing how to harmonize different custom implementations into one shared diagnostics protocol.

---

## UDS across multiple physical layers
UDS (Unified Diagnostic Services) has long been the backbone of diagnostics. Originally bound to CAN, it now works across Ethernet, FlexRay, LIN — and yes, even the legacy K-line.  

The idea is simple: keep the same application layer, but adapt the transport below. This makes gateways easier to configure and keeps diagnostics usable as network technologies evolve.  

High-speed versions like **UDS over IP** enable bandwidth-intensive tasks such as vehicle software updates, while CAN or LIN still serve well for lighter ECUs. The flexibility is what keeps UDS relevant.

---

## Connected vehicles
With vehicles online, diagnostics is no longer limited to a workshop tool and a cable. Remote diagnostics, OTA updates, and predictive monitoring are all possible.  

Standards such as DoIP make it feasible to move diagnostic data over IP backbones. Combined with telematics and V2X systems, this enables entirely new use cases — from safety monitoring to remote software rollout.

---

## On-board and off-board architectures
On-board diagnostics (OBD) handle real-time monitoring and emissions compliance. Off-board tools provide deeper inspection and software flashing.  

Modern standards bridge the two: a scan tool can talk to an ECU the same way a backend service can, provided both follow the same UDS or DoIP mappings. This blending of on-board and off-board is essential for today’s service flows.

---

## Software-oriented diagnostics
As vehicles become software-defined, diagnostics must cover more than hardware faults. Multiple OSs, third-party apps, and frequent updates demand a software-aware approach.  

Data analytics and machine learning are increasingly used to detect patterns, while new APIs are emerging to unify access across ECUs and HPCs.

---

## Service-Oriented Vehicle Diagnostics (SOVD)
SOVD takes this shift further. Instead of ECU-centric messages, it defines a **web-style API** (HTTP/REST, JSON, OAuth) for the entire vehicle diagnostics contents.  

It works on-board, off-board, or even in the cloud, and can expose the same diagnostics data via different deployment models. This makes it a strong candidate to bridge classic diagnostics with software-defined vehicles.

---

## Security and authentication
Security is critical when diagnostics moves online.  
- **Digital certificates** can be used to authenticate clients and authorize specific operations.  
- **Open authentication schemes** (like OAuth / OpenID Connect) provide interoperability across tools and organizations.  

The goal: only trusted clients should be able to trigger sensitive diagnostics functions.

---

## CI/CD and diagnostics
Modern development pipelines apply not only to software features, but also to diagnostics. CI/CD can be used to test diagnostic flows continuously, ensuring they evolve in step with the code they observe.  

This shortens feedback loops and increases confidence — a necessity when vehicle software is updated frequently.

---

## Conclusion
Diagnostics standards have evolved from fixed hardware protocols to flexible, software-oriented APIs. By embracing SOVD, UDS over multiple layers, secure authentication, and CI/CD methods, the industry is building a foundation for diagnostics that is **scalable, adaptable, and future-proof**.  

The journey isn’t over. Expect more research in **AI-driven diagnostics, data analytics, and new standardization efforts** — all aiming to keep pace with software-defined mobility.

---

*Feedback welcome: open an issue in the repo to share your thoughts or propose a scenario.*  
