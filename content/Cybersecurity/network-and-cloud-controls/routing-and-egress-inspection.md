---
title: Routing and Egress Inspection
description: Protect routing sessions and inspect outbound web and DNS activity with attention to encryption and visibility limits.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, network-and-cloud-controls]
---

Network defenses need to address both routing integrity and the destinations reached through the network. A router can authenticate routing-session traffic, while egress controls inspect or restrict outbound requests. Each control relies on different information and supplies a different kind of assurance.

## Authenticating Routing Sessions

Border Gateway Protocol, or BGP, exchanges routing information over TCP. Keyed authentication helps protect this transport session against forged or altered segments.

The TCP MD5 Signature Option uses a shared secret to compute and verify a digest on each TCP segment. For example, a router can discard a forged TCP reset that lacks the valid keyed digest, helping protect the connection. TCP Authentication Option, or TCP-AO, supersedes this older mechanism.

Integrity checks detect unauthorized changes to protected data. Data-origin authentication indicates that a party holding the shared key generated the segment. A plain, unkeyed hash does not authenticate a sender.

These protections do not encrypt the session or establish that the sender owns the advertised routes. Data-origin authentication is also distinct from proving a peer's identity.

## Inspecting Web Destinations

Domain fronting can hide a destination behind an allowed domain. Managed TLS inspection can support policy checks on the TLS server name and the HTTP Host destination.

The distinction between those fields matters. HTTP headers travel inside encrypted HTTPS traffic. Passive filtering of Server Name Indication, or SNI, cannot compare that field with encrypted HTTP headers. Encrypted Client Hello can further reduce visibility into the TLS server name.

Use compatible managed inspection and destination controls where those checks are required. The policy must reflect the information the inspection point can actually observe.

## Examining DNS for Hidden Transfers

DNS tunneling embeds data in DNS requests. A DNS firewall can combine query-length and entropy analytics to identify suspicious requests. Entropy describes how random the content appears; long, random-looking domain names can indicate encoded data.

Combine those indicators with behavior analysis and enforced use of approved DNS resolvers. Otherwise, the organization may lack the intended visibility or control over outgoing DNS requests.

## Limits and Tradeoffs

Long or random-looking queries do not prove DNS tunneling. Treat them as indicators that need behavioral context. TLS inspection likewise depends on compatibility and accessible fields; SNI-only filtering cannot supply an HTTP-header comparison.

Routing-session authentication, web-destination inspection, and DNS analysis address separate failure modes. A valid routing-session digest gives no assurance about the safety of the outbound application traffic that follows the route.

## References

- [RFC 2385: TCP MD5 Signature Option](https://www.rfc-editor.org/rfc/rfc2385.html) describes the older keyed transport protection.
- [RFC 4271: BGP](https://www.rfc-editor.org/rfc/rfc4271.html) discusses BGP and its security considerations.
- [RFC 5925: TCP Authentication Option](https://www.rfc-editor.org/rfc/rfc5925.html) defines the successor mechanism.
- [MITRE ATT&CK: Domain fronting detection](https://attack.mitre.org/detectionstrategies/DET0196/) describes detection approaches.
- [Palo Alto Networks: DNS security signatures](https://docs.paloaltonetworks.com/dns-security/getting-started/cloud-delivered-dns-signatures) discusses DNS threat analysis.

## Related Concepts

- [[Cybersecurity/network-and-cloud-controls/index|Network and Cloud Controls]]
- [[Cybersecurity/network-and-cloud-controls/source-addresses-and-name-resolution|Source Addresses and Name Resolution]]
- [[Cybersecurity/detection-and-response/data-loss-detection-and-response|Data Loss Detection and Response]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
