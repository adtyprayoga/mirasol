---
title: Segmentation and Lateral Movement
description: Restrict communication between network zones and systems to limit the spread of a compromise.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, network-and-cloud-controls]
---

Lateral movement occurs when an attacker spreads from a compromised system to other systems. Network segmentation limits the connections available for that movement. Credential hygiene reduces the opportunities to reuse stolen credentials across the systems an attacker can reach.

These controls work together: restricting connectivity reduces reachable targets, while protecting credentials limits the authority an attacker can exercise.

## Separating Network Zones

A Virtual Local Area Network, or VLAN, creates a smaller broadcast domain. Dividing a network into VLANs can reduce the scope of broadcast traffic, but the organization also needs access control lists and firewalls between zones to restrict communication.

The enforcement point between zones determines which connections remain possible. Creating separate VLANs without meaningful restrictions between them leaves a gap between the intended separation and actual access.

Broadcast resilience also needs its own controls. Retain Spanning Tree Protocol, or STP, to prevent Layer 2 loops. Storm control can further limit broadcast floods. Segmentation does not replace these mechanisms.

## Restricting Connections Between Systems

Microsegmentation applies more specific restrictions to communication between systems. Its purpose is to reduce the paths an attacker can use after gaining an initial foothold.

Credential hygiene complements this restriction. Protected, unique credentials reduce reuse of stolen authentication material. A network rule and a credential policy address different parts of the same attempt to spread: reachability and authority.

For developer laptops, combine restrictive connectivity with device posture checks. Posture describes the laptop's security condition. Checking it before allowing access provides another condition for access to the systems the developer needs.

## Limits and Tradeoffs

VLAN membership alone does not supply sufficient access restrictions. Review the ACLs and firewalls that govern communication between zones, along with the more specific connections permitted between systems.

A device can pass a posture check while harboring an undetected compromise. Keep connectivity restrictive even for devices that meet the current posture policy. The posture signal adds information to the decision; it cannot establish that a system is free from compromise.

Segmentation and credential hygiene reduce the opportunities for lateral movement without guaranteeing its prevention. Their value depends on the access they restrict in the actual environment and the credentials that remain available to a compromised system.

## References

- [Cisco: Segmentation design guide](https://www.cisco.com/c/dam/en/us/td/docs/solutions/CVD/Campus/CVD-Software-Defined-Access-Segmentation-Design-Guide-2018MAY.pdf) describes network segmentation design.
- [CISA: Microsegmentation guidance](https://www.cisa.gov/news-events/alerts/2025/07/29/cisa-releases-part-one-zero-trust-microsegmentation-guidance) introduces microsegmentation in zero trust.
- [CISA: Common network misconfigurations](https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-278a) discusses weaknesses that support attacker movement.
- [NIST: Zero trust implementation architecture](https://pages.nist.gov/zero-trust-architecture/VolumeB/architecture.html) discusses access architecture and enforcement.

## Related Concepts

- [[Cybersecurity/network-and-cloud-controls/index|Network and Cloud Controls]]
- [[Cybersecurity/identity-and-access/context-and-zero-trust|Context and Zero Trust]]
- [[Cybersecurity/detection-and-response/windows-credential-and-privilege-defenses|Windows Credential and Privilege Defenses]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
