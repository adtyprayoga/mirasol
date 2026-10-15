---
title: Data Loss Detection and Response
description: Combining content and behavior signals with a fair investigation of potentially sensitive uploads.
created: 2026-10-15
updated: 2026-10-15
tags:
  - cybersecurity
  - detection-and-response
---

Data Loss Prevention (DLP) helps identify sensitive information leaving an organization's environment. An alert about an upload to personal cloud storage calls for a controlled response and an investigation of context. The alert signals a potential policy problem; it does not establish misconduct.

Effective detection combines visibility into data with an understanding of the activity around it. Effective response then uses that evidence to decide what happened and how to handle the transfer.

## Responding to a Suspicious Upload

Where policy and product capabilities support it, hold or block the upload. Preserve the alert and related activity records so investigators can examine what triggered the detection.

The investigation should consider the sensitivity of the data, the destination, and the business purpose. An upload to personal cloud storage may raise concern, but those details are needed to interpret the event fairly.

The word quarantine can mean holding or stopping a transfer. Some products implement a block rather than a quarantine queue. Response instructions need to match what the deployed product actually supports.

## Seeing HTTPS Exfiltration

HTTPS encrypts traffic, which affects content visibility. TLS inspection can reveal the content of traffic that the inspection system can decrypt. DLP can then inspect for sensitive information leaving the environment.

User and Entity Behavior Analytics (UEBA) adds another perspective by highlighting unusual activity, such as bulk uploads. Content signals indicate what information may be involved, while behavior signals help identify activity that deserves closer examination.

These sources complement each other. Unusual behavior alone does not establish that sensitive data was lost. Content visibility alone also leaves gaps when traffic cannot be inspected.

## Limits and Tradeoffs

Some traffic cannot be decrypted by inspection, and combining TLS inspection, DLP, and behavior analytics does not guarantee detection. Interpret alerts alongside the available visibility and the circumstances of the transfer.

Containment and judgment serve different purposes. Holding a transfer can limit potential loss while the investigation proceeds; a decision about misconduct requires evidence beyond the alert itself. Preserve that distinction in response procedures and communications.

## References

- [Microsoft: Endpoint DLP](https://learn.microsoft.com/en-us/purview/endpoint-dlp-learn-about)
- [Palo Alto Networks: SSL Forward Proxy](https://docs.paloaltonetworks.com/network-security/decryption/administration/decryption-overview/ssl-forward-proxy)
- [Microsoft: Content Inspection](https://learn.microsoft.com/en-gb/defender-cloud-apps/content-inspection)
- [Microsoft: Defender for Cloud Apps and Zero Trust](https://learn.microsoft.com/en-us/defender-cloud-apps/zero-trust)

## Related Concepts

- [[Cybersecurity/risk-and-governance/classification-and-privacy|Classification and Privacy]]
- [[Cybersecurity/detection-and-response/investigation-ready-logs|Investigation-Ready Logs]]
- [[Cybersecurity/detection-and-response/index|Detection and Response]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
