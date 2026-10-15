---
title: Context and Zero Trust
description: Use identity, device condition, and access context to grant scoped access and reassess it as conditions change.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, identity-and-access]
---

An identity can have permission to use an application while the current access attempt presents unacceptable risk. Context-aware access adds conditions such as device security, location, and sign-in risk to the decision.

Zero trust follows the same central idea: being inside a network does not establish trust by itself. Access depends on verified identity and relevant context, with reassessment when conditions change.

## Considering Device Posture

Device posture describes a device's security condition, including its compliance and protection status. A context-aware policy might allow an application only from a compliant company laptop during a low-risk sign-in.

That condition complements the user's permissions. A role can describe the work a person may perform, while the contextual policy determines whether the present request meets the required conditions. Administrators must configure and enforce both parts.

## Combining Roles and Attributes

Role-based access control, or RBAC, assigns permissions through roles. Attribute-based access control, or ABAC, evaluates attributes of the user, resource, action, and environment.

ABAC fits decisions that depend on details such as device condition, location, or data sensitivity. It can express a policy that needs more information than a fixed role assignment provides.

Organizations can combine these approaches. Role membership can serve as one attribute in a broader policy. The choice depends on the conditions an organization needs to express rather than a requirement to replace all roles.

## Reassessing Access and Limiting Reach

Continuous verification means ongoing policy and risk evaluation. A system can reassess or revoke access when identity, device condition, or other relevant signals change. It does not require constant password prompts.

Zero Trust Network Access, or ZTNA, applies identity, posture, and policy checks before granting access to approved applications. Application-level access can limit the network reach available through a connection.

This scope matters because connectivity and authorization are different. Reaching a network should not by itself establish permission to use all applications or resources on it.

## Limits and Tradeoffs

Contextual policies provide protection only when the system evaluates and enforces them. A policy description or role assignment alone does not establish those checks.

The comparison between ZTNA and a VPN also requires care. Broad network access is a common VPN deployment pattern, but VPNs can restrict access. Assess the actual permissions and reachable resources in either deployment instead of inferring them from the product label.

## References

- [Microsoft: Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview) describes contextual access policies.
- [NIST SP 800-162: ABAC](https://csrc.nist.gov/pubs/sp/800/162/upd2/final) explains attribute-based access control.
- [NIST SP 800-207: Zero trust architecture](https://csrc.nist.gov/pubs/sp/800/207/final) provides the architectural basis for identity- and context-based access.
- [Microsoft: ZTNA overview](https://www.microsoft.com/en-us/security/business/security-101/what-is-zero-trust-network-access-ztna) introduces application-level access.

## Related Concepts

- [[Cybersecurity/identity-and-access/index|Identity and Access]]
- [[Cybersecurity/identity-and-access/least-privilege|Least Privilege]]
- [[Cybersecurity/network-and-cloud-controls/segmentation-and-lateral-movement|Segmentation and Lateral Movement]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
