# ArcaneDoor & FIRESTARTER Research Project

## Overview

This project focuses on the analysis of the intrusion activity publicly associated with ArcaneDoor-related reporting and the malware referred to as **FIRESTARTER**, with particular attention given to the Cisco Secure Firewall ASA and FTD WebVPN attack surface.

The primary goal of this research is to examine the technical conditions that may have enabled:

- initial access,
- post-compromise persistence,
- and long-term operational stealth

inside affected network appliances.

Public reporting from Cisco, CISA, and other security organizations provides high-level descriptions of the vulnerabilities and malware behavior involved in these campaigns. However, many low-level implementation details, internal processing behaviors, and architectural implications remain either partially documented or entirely undisclosed publicly.

This project attempts to bridge that gap through technical reconstruction and analytical research.

---

# Research Scope

Several chapters focus specifically on vulnerabilities such as:

- `CVE-2025-20362`
- `CVE-2025-20333`

where the research expands beyond the limited information available in official advisories by examining:

- plausible request-processing behavior,
- authorization-boundary inconsistencies,
- parser logic failures,
- memory corruption mechanics,
- heap corruption survivability,
- and potential control-flow redirection paths inside the `lina` WebVPN subsystem.

Where exact implementation details are unavailable publicly, the project uses hypothetical reconstructions derived from:

- public advisories,
- observed appliance behavior,
- reverse engineering methodology,
- enterprise VPN architecture patterns,
- and historical exploitation techniques targeting network edge devices.

The purpose of these reconstructions is **not** to claim access to proprietary Cisco source code or private exploit material, but rather to model technically coherent explanations for how vulnerabilities of this class may realistically behave internally.

---

# FIRESTARTER Operational Analysis

Beyond the initial access phase, the project also examines the persistence and operational behavior associated with FIRESTARTER itself.

Public reporting from CISA describes FIRESTARTER as a Linux-based persistence mechanism capable of:

- surviving remediation attempts,
- restoring execution during shutdown events,
- interacting directly with the `lina` process,
- and maintaining long-term access to compromised devices even after firmware updates were applied.

Rather than focusing on payload development or undocumented malware internals, the analysis concentrates on the observable operational behavior described publicly, including:

- runtime persistence behavior,
- signal-based relaunch mechanisms,
- memory-resident execution,
- interaction with `lina` process memory,
- hook installation concepts,
- reboot persistence behavior,
- anti-forensic cleanup activity,
- and stealth considerations inside long-lived appliance processes.

---

# Architectural Perspective

Particular attention is given to how these behaviors differ from traditional endpoint malware operations.

In appliance-focused intrusion scenarios, attackers often prioritize:

- operational stability,
- persistent runtime access,
- authentication manipulation,
- and long-term stealth

over noisy payload execution or conventional malware deployment techniques.

This project therefore approaches FIRESTARTER primarily as an **operational persistence and appliance-residency problem** rather than as a traditional userland malware sample.

---

# Disclaimer

All technical reconstructions presented throughout this project are intended strictly for educational, analytical, and defensive research purposes.

Any hypothetical code paths, memory layouts, parser behaviors, or exploitation models discussed are derived from public reporting, reverse engineering methodology, and behavioral inference — not from proprietary Cisco source code or undisclosed exploit material.

The goal of this research is to improve understanding of appliance-focused intrusion tradecraft, persistence behavior, and defensive visibility challenges in modern network infrastructure environments.