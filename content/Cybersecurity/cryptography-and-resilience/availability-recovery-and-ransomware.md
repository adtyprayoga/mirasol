---
title: Availability, Recovery and Ransomware
description: Connecting availability goals to recovery objectives, protected backups, and evidence that restoration works.
created: 2026-10-15
updated: 2026-10-15
tags:
  - cybersecurity
  - cryptography-and-resilience
---

Availability means keeping systems and data accessible when they are needed. It is part of the confidentiality, integrity, and availability (CIA) triad. Redundancy, backups, and recovery support this goal, but each recovery arrangement needs clear objectives and evidence that it works.

Ransomware makes the need concrete. It locks or encrypts data and demands payment, often in exchange for a promised recovery key. Some campaigns also steal data. Paying does not guarantee recovery.

## Defining Acceptable Loss and Downtime

The Recovery Point Objective (RPO) expresses acceptable data loss as a time window. A fifteen-minute RPO means that losing up to fifteen minutes of recent data is acceptable to the business.

The Recovery Time Objective (RTO) concerns acceptable recovery time or downtime. The distinction matters: recovering an older copy quickly and recovering a recent copy slowly have different consequences. A recovery arrangement needs to be evaluated against the objective it is intended to meet.

## Protecting Backup Copies

Immutable storage prevents modification during enforced retention. Write Once, Read Many (WORM) storage can provide this protection when configured and enforced appropriately. Air-gapped backups protect through isolation from reachable production systems.

These are different mechanisms for reducing exposure to backup tampering. A product's WORM capability alone does not demonstrate protection if the necessary settings are absent or ineffective.

## Verifying Recovery and Protection Separately

An illustrative backup check has two parts. A retention-locked copy rejects overwrite and deletion attempts. An isolated restore test then recovers the expected records.

The rejected modification attempts provide evidence about enforced protection. The restore test demonstrates recoverability. A successful restore does not prove immutability, just as a protected copy does not by itself demonstrate that recovery will produce usable data.

## Limits and Tradeoffs

No backup approach guarantees safety under every compromise. Verify enforced retention and denied modification attempts, while testing restoration separately. Isolation and immutability should be understood in terms of their actual configuration.

RPO defines acceptable data loss; it does not prove that backups meet that target. Restore tests provide evidence of recovery, and backup protection checks provide evidence of resistance to tampering. Keep those claims distinct.

## References

- [NIST: Availability](https://csrc.nist.gov/glossary/term/availability)
- [AWS: Disaster Recovery Objectives](https://aws.amazon.com/disaster-recovery/faqs/)
- [CISA: Ransomware Guide](https://www.cisa.gov/stopransomware/ransomware-guide)
- [AWS: Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html)

## Related Concepts

- [[Cybersecurity/cryptography-and-resilience/integrity-authenticity-and-encryption|Integrity, Authenticity and Encryption]]
- [[Cybersecurity/detection-and-response/incident-response-readiness-and-containment|Incident Response Readiness and Containment]]
- [[Cybersecurity/cryptography-and-resilience/index|Cryptography and Resilience]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
