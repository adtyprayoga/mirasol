---
title: Windows Credential and Privilege Defenses
description: Understanding credential dumping, Pass-the-Hash, vulnerable drivers, and the distinct telemetry needed for Kerberoasting.
created: 2026-10-15
updated: 2026-10-15
tags:
  - cybersecurity
  - detection-and-response
---

Windows defenses need to address both stolen credentials and elevated privileges. These threats can reinforce each other, but the underlying techniques differ. Protecting authentication material, limiting privileged logons, and controlling vulnerable drivers address different parts of the problem.

## Protecting Credential Material

The Local Security Authority Subsystem Service, or LSASS, handles Windows authentication. Its process, `lsass.exe`, can hold credential material in memory and is a common credential-dumping target. The material available depends on system configuration and protections; other dumping techniques target different stores.

Pass-the-Hash uses a stolen password hash to authenticate without knowing the password. Credential Guard isolates supported credential secrets, while LSA protection hardens the authentication process. Restricting administrator logons limits the systems where privileged credentials are exposed. Together, these controls reduce theft and reuse risk.

## Blocking Vulnerable Drivers

A signed driver can still contain a vulnerability that an attacker exploits to gain kernel privileges. Driver block rules and application control help prevent known vulnerable drivers from being used.

Windows Defender Application Control (WDAC), now called App Control for Business, supports this approach. Rules need enforcement and updates, alongside driver patching and compatibility testing. A signature establishes something about a driver's origin; it does not establish that the driver is free of security flaws.

## Recognizing Kerberoasting

Kerberoasting obtains Kerberos service tickets for offline attempts to recover service-account passwords. Hunting should prioritize unusual service-ticket requests, or TGS-REQ, including Windows Event ID 4769, bursts targeting service principal names (SPNs), and unexpected encryption patterns.

AS-REQ belongs to initial authentication. AS-REP roasting is a distinct technique involving authentication responses. Neither should be treated as interchangeable with the service-ticket activity central to Kerberoasting. Kerberoasting also does not require dumping LSASS.

## Limits and Tradeoffs

Credential protections reduce risk without covering every possible Pass-the-Hash scenario. Driver blocklists cannot cover every vulnerable driver, and deployment needs compatibility checks.

Kerberoasting telemetry needs interpretation. RC4 use can be a useful signal but is not proof of an attack; AES-encrypted tickets can also be roasted. Evaluate request patterns and context together.

## References

- [MITRE ATT&CK: LSASS Memory](https://attack.mitre.org/techniques/T1003/001/)
- [Microsoft: How Credential Guard Works](https://learn.microsoft.com/windows/security/identity-protection/credential-guard/how-it-works/)
- [Microsoft: Mitigating Pass-the-Hash and Credential Theft](https://download.microsoft.com/download/7/7/a/77abc5bd-8320-41af-863c-6ecfb10cb4b9/mitigating-pass-the-hash-attacks-and-other-credential-theft-version-2.pdf)
- [Microsoft: Recommended Driver Block Rules](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/design/microsoft-recommended-driver-block-rules)
- [MITRE ATT&CK: Kerberoasting](https://attack.mitre.org/techniques/T1558/003/)
- [MITRE ATT&CK: Kerberoasting Detection Strategy](https://attack.mitre.org/detectionstrategies/DET0157/)

## Related Concepts

- [[Cybersecurity/detection-and-response/adversary-behavior-and-detection-coverage|Adversary Behavior and Detection Coverage]]
- [[Cybersecurity/network-and-cloud-controls/segmentation-and-lateral-movement|Segmentation and Lateral Movement]]
- [[Cybersecurity/detection-and-response/index|Detection and Response]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
