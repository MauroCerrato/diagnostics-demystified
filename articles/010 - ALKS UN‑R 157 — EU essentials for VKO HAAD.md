---
title: "ALKS (UN-R 157) — EU essentials for VKO HAAD"
date: 2025-12-06
tags: [ALKS, UN-R157, EU, Type-Approval, DSSAD, SMS]
summary: Paraphrased, IP-safe notes mapping ALKS obligations to approval and in-service evidence, plus synthetic JSON examples (ToC/MRM).
---


#*Why ALKS matters for VKO HAAD (EU focus)*

In the past weeks I started my new VKO role at CARIAD by reading and summarizing a lot of UNECE Regulation texts, I am writing this article primarly to keep track of the learning and to try out how would it be possible to conenct Highly Automated Autonomous Driving Vehicle regulations to some (IP friendly) examples of generated synthetic evidence.

I’m starting a weekly series to turn regulatory reading into small, verifiable artifacts: master-table entries, an “ALKS essentials” action pack, and synthetic evidence. All content is paraphrased and Apache‑2.0 friendly.


##*Essentials acronyms needed(paraphrased)*
- HAAD
- ODD,
- ToC, 
- MRM, 
- extensions (speed, lane change where applicable), 
- documentation/evidence

##*Compliance mapping table (Homologation/Type Approval/SMS/DSSAD/In-Service)*

Topic	Homologation	Type Approval	SMS	DSSAD	In-Service
ODD declaration	Context doc	ODD boundaries evidence	Governance	ODD flag	Operational checks
ToC timing/HMI	—	Timing + escalation behavior	Ops procedure	ToC record	Event review
MRM behavior	—	Triggers + safe stop	Safety mgmt	MRM record	Incident review
Speed/lane-change	—	Conditions + limits	Change mgmt	Mode flags	Field observation
Logging/records	—	Sufficiency of records	Retention policy	Record types	Reporting cadence



##*Synthetic evidence (JSON outlines; links to sovd-lab docs/haad/compliance-mapping)*

- ToC example: docs/haad/compliance-mapping/evidence/2025-12-06_toc_demo.json
- MRM example: docs/haad/compliance-mapping/evidence/2025-12-06_mrm_demo.json
- Schemas: docs/haad/compliance-mapping/event-schemas/


##PlayWithDocker quick run idea (still to be completed)

I am planning to add to sovd-lab a new kotlin powered event generator service, this shall emit a ToC event and, if ignored, an MRM event.

Both are exported as JSON and validated against schemas with ajv. 

All of the data will always be synthetic and does (and will) not use proprietary data.

##*What’s next: UN-R 155/156 touchpoints*

- Crosswalk with EU GSR and confirm implementing checkpoints from my internal tracker.
- Add a minimal DSSAD checklist and improve the evidence mapping tables.



“Content licensed under Apache-2.0; paraphrase-only; no quotations from paywalled standards.”
