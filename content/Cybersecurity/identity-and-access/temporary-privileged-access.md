---
title: Temporary Privileged Access
description: Combine narrow permissions, approval, automatic expiry, and activity auditing for occasional production access.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, identity-and-access]
---

Production databases sometimes require direct attention from engineers. Just-in-time access, or JIT, grants the permissions needed for a specific task during an approved period. It applies least privilege to the duration of access as well as its scope.

Privileged access management, or PAM, can support this process through a broker that checks the request and issues short-lived credentials. The broker gives each person accountable access rather than requiring everyone to share a database account.

## Requesting Access for a Task

A useful request identifies the person, the database, the required actions, and the access window. Policy checks or an approver authorize the request. Multifactor authentication helps establish that the requester controls the expected identity.

For example, an engineer investigating an incident might receive read-only database access for thirty minutes. The grant permits investigation without adding unnecessary write or administrative permissions. The access expires after the approved window.

Named accounts preserve the connection between an individual and their actions. Shared VPN access to a jump host provides connectivity, but that arrangement alone does not establish temporary database permissions or individual accountability.

## Auditing the Work

Access activation and database activity describe different events. An activation record shows that someone received permission. Database or access-gateway audit records show relevant activity performed during the session.

Configure both where the task requires an auditable history. Protected logs should support an account of who accessed the database, when access occurred, and what relevant actions took place.

Credential expiry also needs an implementation check. A credential can expire while an existing connection continues. Verify whether the database or gateway terminates established sessions when the approved window ends, and enforce that behavior where required.

## Limits and Tradeoffs

Routine occasional access belongs in an approved JIT process. Break-glass access usually serves emergencies and needs separate treatment as an emergency-access capability. Calling all temporary access “break-glass” can obscure that distinction.

The available approval, expiry, and audit features depend on the access platform and database. A temporary grant helps reduce exposure only when its scope, lifetime, and session behavior match the intended policy. Logging the grant alone leaves a gap in understanding database activity.

## References

- [Microsoft: Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-getting-started) introduces temporary privileged access and audit history.
- [Teleport: Access requests](https://goteleport.com/docs/identity-governance/access-requests/) describes request-based access.
- [Teleport: Session recording](https://goteleport.com/docs/reference/architecture/session-recording/) covers session and database auditing.
- [Microsoft: PIM deployment planning](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-deployment-plan) discusses planning privileged access.
- [Microsoft: Emergency access accounts](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access) addresses emergency access separately.

## Related Concepts

- [[Cybersecurity/identity-and-access/index|Identity and Access]]
- [[Cybersecurity/identity-and-access/least-privilege|Least Privilege]]
- [[Cybersecurity/detection-and-response/investigation-ready-logs|Investigation-Ready Logs]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
