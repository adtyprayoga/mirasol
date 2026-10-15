---
title: Source Addresses and Name Resolution
description: Validate packet source addresses and remove unnecessary local name-resolution paths that attackers can poison.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, network-and-cloud-controls]
---

A network packet includes a source address, but that address can be forged. A computer also relies on name resolution to find another system, and an attacker can exploit insecure resolution mechanisms with false replies. Source validation and managed DNS address these separate opportunities for deception.

## Filtering Forged Source Addresses

IP spoofing means forging a packet's source IP address. Egress source filtering uses an access control list, or ACL, to permit traffic leaving an internal network only when its source belongs to an authorized internal subnet.

For example, a router can accept sources in `192.168.1.0/24` on the LAN side and block an internal packet claiming source `8.8.8.8`. The `/24` identifies a subnet whose addresses share the first twenty-four bits.

Traffic leaving the organization enters the router through its LAN interface. Applying validation there, before network address translation changes addresses, can make the source check match the internal subnet. A WAN-side rule must account for the translated source addresses it will see.

Unicast Reverse Path Forwarding, or uRPF, uses routing information for another form of source validation. Strict mode checks that the return route uses the arriving interface. Loose mode checks source-route reachability and provides weaker validation.

## Removing Poisonable Name Resolution

Link-Local Multicast Name Resolution, or LLMNR, and NetBIOS Name Service, or NBT-NS, can resolve local names when DNS fails. An attacker can answer with false information, redirecting a computer to an attacker-controlled system and potentially exposing authentication material.

Disable unnecessary LLMNR and NetBIOS name resolution on endpoints and use properly configured DNS. On Windows, enable **Turn off multicast name resolution** for LLMNR. Disable **NetBIOS over TCP/IP** separately on the relevant adapters or through managed configuration.

After both mechanisms have been disabled, a mistyped file-server name cannot trigger requests through those mechanisms for an attacker to answer.

## Limits and Tradeoffs

Subnet filtering cannot distinguish legitimate use from impersonation of another address within the permitted subnet. Strict uRPF can also reject legitimate traffic when return paths differ, so topology matters when choosing its mode.

Before disabling local resolution, check DNS operation and legacy dependencies. Other name-resolution protocols require separate consideration. SMB signing helps mitigate SMB relay, but it does not disable name-resolution poisoning. Match each control to the mechanism it addresses.

## References

- [RFC 2827: Network ingress filtering](https://datatracker.ietf.org/doc/html/rfc2827) describes source-prefix filtering and its limits.
- [RFC 3704: Multihomed network filtering](https://www.rfc-editor.org/rfc/rfc3704.html) discusses reverse-path validation and asymmetric routing.
- [MITRE ATT&CK: LLMNR/NBT-NS poisoning and SMB relay](https://attack.mitre.org/techniques/T1557/001/) describes the attack and mitigations.
- [Microsoft: DNS Client policy](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-admx-dnsclient) documents the multicast name-resolution setting.

## Related Concepts

- [[Cybersecurity/network-and-cloud-controls/index|Network and Cloud Controls]]
- [[Cybersecurity/network-and-cloud-controls/segmentation-and-lateral-movement|Segmentation and Lateral Movement]]
- [[Cybersecurity/network-and-cloud-controls/routing-and-egress-inspection|Routing and Egress Inspection]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
