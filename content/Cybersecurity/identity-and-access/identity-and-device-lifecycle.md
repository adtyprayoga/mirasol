---
title: Identity and Device Lifecycle
description: Maintain appropriate access as people change roles and manage unique device identities throughout their use.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, identity-and-access]
---

An access decision needs continued maintenance after an account or device enters service. People join organizations, change jobs, and leave. Devices need protected identities and a way to renew or revoke their credentials. Lifecycle management keeps those changes connected to the access that systems enforce.

Human accounts and connected devices use different mechanisms, but both require attention to identity, current access needs, and the end of that access.

## Managing Joiners, Movers, and Leavers

Joiner, mover, leaver management, often shortened to JML, covers three recurring changes. Grant access when someone joins, adjust it when their responsibilities change, and remove it when they leave.

Without a working removal process, an organization can retain orphaned SaaS access: accounts or permissions that remain after their business need has ended. A role change also needs attention because earlier permissions may no longer fit the person's duties.

System for Cross-domain Identity Management, or SCIM, supports automated account provisioning and deprovisioning. Periodic access reviews provide another opportunity to check whether people still need their assigned access. Automation and review address different parts of the lifecycle.

## Giving Devices Individual Identities

Large Internet of Things deployments need a way to distinguish devices. A per-device X.509 certificate gives each device a unique identity. A private certificate authority can issue these certificates for the deployment.

Protect each device's private key and support certificate renewal and revocation. The identity mechanism needs continued maintenance as certificates approach the end of their lifetime or a device loses trust.

Secure boot addresses a different concern: checking that trusted software starts on the device. A certificate establishes device identity, while secure boot protects startup integrity. Using both addresses separate requirements.

## Limits and Tradeoffs

Application support determines how much a provisioning integration can enforce. Verify that each application supports the required deprovisioning behavior. Removing or disabling an account may also require separate action to revoke active sessions or tokens.

Device identity likewise depends on private-key protection and a usable renewal and revocation process. A unique certificate alone does not establish trustworthy startup software; secure boot supplies a separate control for that purpose.

Lifecycle controls should therefore cover the actual access mechanisms in use. The relevant check is whether unwanted access ends, including credentials or sessions that can outlive the account change.

## References

- [Microsoft: Identity governance overview](https://learn.microsoft.com/en-us/entra/id-governance/identity-governance-overview) introduces lifecycle management and access review capabilities.
- [AWS IoT: X.509 client certificates](https://docs.aws.amazon.com/iot/latest/developerguide/x509-client-certs.html) describes certificate-based device identities.

## Related Concepts

- [[Cybersecurity/identity-and-access/index|Identity and Access]]
- [[Cybersecurity/identity-and-access/least-privilege|Least Privilege]]
- [[Cybersecurity/identity-and-access/authentication-and-session-protection|Authentication and Session Protection]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
