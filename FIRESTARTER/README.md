# Firestarter

Technical research and reconstruction project focused on publicly reported intrusion activity and vulnerabilities affecting Cisco ASA/FTD appliances and WebVPN infrastructure.

This Dir contains technical research notes, inferred attack-flow analysis, and behavioral reconstructions based on publicly available information related to recent Cisco appliance intrusion activity.

The research is primarily based on:

- Cisco PSIRT advisories
- CISA publications
- public threat intelligence reporting
- reverse engineering methodology
- behavioral and operational inference

Some sections include hypothetical reconstructions and inferred execution paths intended to explain plausible exploitation mechanics and operational behavior.

These reconstructions should not be interpreted as confirmed representations of proprietary Cisco implementations or verified attacker workflows.

Current research areas include:

- Introduction
- CVE-2025-20362
- CVE-2025-20333

Internet Traffic (HTTPS / 443)
│
▼
┌──────────────────────────────────────────────┐
│ Stage 1: Initial Packet Processing           │
│ (Pre-Auth / Parsing Layer)                   │
└──────────────────────────────────────────────┘
│
│ Possible Exploit Path
│ CVE-2025-20362
▼
┌──────────────────────────────────────────────┐
│ Authentication Boundary / Login Transition   │
│ (Valid or Semi-Valid User Context)           │
└──────────────────────────────────────────────┘
│
▼
┌──────────────────────────────────────────────┐
│ Stage 2: Session Processing Layer            │
│ (Post-Auth / VPN Session Handling)          │
└──────────────────────────────────────────────┘
│
│ Secondary Exploitation Path
│ CVE-2025-20333
▼
┌──────────────────────────────────────────────┐
│ Internal LINA WebVPN Context Execution       │
│ (Request Handling / Session Logic Layer)     │
└──────────────────────────────────────────────┘
│
▼
┌──────────────────────────────────────────────┐
│ Stage 3: Memory Corruption Conditions        │
│ (Heap / Parser / Object Lifecycle Issues)    │
└──────────────────────────────────────────────┘
│
▼
┌──────────────────────────────────────────────┐
│ Control-Flow Disruption (Inferred)           │
│ (Indirect Execution Path Influence)          │
└──────────────────────────────────────────────┘
│
▼
┌──────────────────────────────────────────────┐
│ FIRESTARTER Deployment Phase (Observed)      │
│ Linux-based persistence component           │
└──────────────────────────────────────────────┘
│
▼
┌──────────────────────────────────────────────┐
│ Persistence & Operational Control            │
│ - Runtime persistence                       │
│ - Restart survival mechanisms               │
│ - Interaction with LINA process             │
│ - Stealth & anti-forensics                  │
└──────────────────────────────────────────────┘
│
▼
┌──────────────────────────────────────────────┐
│ Long-term Access / Stealth Operations       │
│ (Maintained Appliance Residency)            │
└──────────────────────────────────────────────┘
