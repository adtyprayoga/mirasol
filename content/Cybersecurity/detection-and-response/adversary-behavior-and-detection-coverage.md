---
title: Adversary Behavior and Detection Coverage
description: How MITRE ATT&CK helps teams describe attacker behavior and assess the reach of their detections.
created: 2026-10-15
updated: 2026-10-15
tags:
  - cybersecurity
  - detection-and-response
---

A security team needs a shared way to describe what attackers try to do and how they do it. MITRE ATT&CK provides that language. Its name stands for Adversarial Tactics, Techniques, and Common Knowledge, and its knowledge base organizes adversary behavior into goals and methods.

For a Security Operations Center (SOC), this makes individual alerts easier to relate to a wider defensive purpose. A detection becomes part of a view of the behaviors the organization can observe and investigate.

## Connecting Detections to Behavior

Mapping a detection means identifying which ATT&CK behavior its logic can recognize. The mapping should reflect what the rule actually observes. A familiar technique name attached to a rule is insufficient evidence of coverage.

This distinction matters because an attacker can carry out a technique in different ways. A rule may detect a particular implementation while missing another. Coverage therefore depends on both the rule and the events available to it.

## Finding Useful Gaps

Consider a SOC with tested detections for malicious scripts but none for credential theft. Mapping these detections makes the imbalance visible. The team can then assess whether credential theft is a significant risk and decide which visibility or detection improvements deserve attention.

The map supports prioritization by making gaps explicit. It also gives analysts a common vocabulary for discussing them. A missing detection and missing telemetry are related problems, but they require different work: writing a rule cannot compensate for events the organization never collects.

## Limits and Tradeoffs

An ATT&CK label does not demonstrate that every variation of a technique will be detected. Validate mappings against detection logic, available logs, and tests of relevant behavior. Review them when rules or telemetry change.

Mapping also does not replace a Security Information and Event Management platform or incident response playbooks. It describes coverage; it does not guarantee accurate alerts, eliminate false positives, or perform the response itself.

## References

- [MITRE ATT&CK knowledge base](https://attack.mitre.org/)
- [MITRE: Getting Started with ATT&CK](https://attack.mitre.org/resources/enterprise-introduction/)
- [MITRE Center for Threat-Informed Defense: Mapping Detections](https://center-for-threat-informed-defense.github.io/summiting-the-pyramid/analytic-design/mappingdetections/)

## Related Concepts

- [[Cybersecurity/detection-and-response/investigation-ready-logs|Investigation-Ready Logs]]
- [[Cybersecurity/detection-and-response/adversary-simulation|Adversary Simulation]]
- [[Cybersecurity/detection-and-response/index|Detection and Response]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
