---
title: Security During Design
description: Identify threats and systemic weaknesses while design choices can still guide implementation.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, application-and-delivery-security]
---

Security work during design helps a team identify threats and weaknesses before implementation. The team can then prioritize risks and choose protections as part of the system's design.

Threat modeling considers how someone could attack or misuse a system. A secure architecture review examines the broader design for systemic weaknesses and recommends controls. Both activities give developers security requirements to carry into implementation and testing.

## Anticipating Misuse

Threat modeling starts with the system the team intends to build and the ways an attacker could misuse it. The aim is to identify and prioritize threats, then decide which mitigations should reduce their likelihood or impact.

A mitigation is a protective measure. It can affect the design of access checks, isolation, or other safeguards before developers commit to implementation choices.

For example, a team designing a records application recognizes that a user might request another user's record. The team requires an authorization check for each record request before coding begins. The requirement makes object-level access control part of the design rather than leaving developers to infer it later.

## Reviewing the Architecture

An architecture review considers weaknesses that can affect the system as a whole. The review identifies design risks and prescribes controls such as isolation and access restrictions.

The connection between a risk and its proposed control should remain clear. A finding about access to other users' data needs a design requirement for authorization. A finding about insufficient isolation needs a corresponding boundary in the architecture.

This early review helps the team act while it can still change the design. Threat assessment and architectural controls can also reduce later redesign work when developers discover security requirements during implementation.

## Limits and Tradeoffs

Threat modeling cannot guarantee discovery of every threat. Its value depends on the assumptions and system design the team examines. Revisit the analysis when requirements or architecture change, including earlier decisions about threats and mitigations.

Architecture reviews complement secure coding and testing. A sound access-control design still requires developers to implement the checks, and testing must assess whether the implementation enforces them. Design work defines the intended protection; later verification provides evidence about the working application.

## References

- [OWASP: Threat Modeling Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html) covers threat identification, prioritization, mitigation, and validation.
- [OWASP Developer Guide: Threat modeling](https://devguide.owasp.org/en/04-design/01-threat-modeling/) discusses early assessment and design decisions.
- [OWASP: Secure by Design Framework](https://owasp.org/projects/secure-by-design-framework?tab=main) addresses security in design and architecture.

## Related Concepts

- [[Cybersecurity/application-and-delivery-security/index|Application and Delivery Security]]
- [[Cybersecurity/application-and-delivery-security/web-vulnerabilities|Web Vulnerabilities]]
- [[Cybersecurity/application-and-delivery-security/dependencies-builds-and-containers|Dependencies, Builds and Containers]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
