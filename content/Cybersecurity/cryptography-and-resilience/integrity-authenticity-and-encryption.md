---
title: Integrity, Authenticity and Encryption
description: Distinguishing data integrity, confidentiality, message accountability, forward secrecy, and certificate information.
created: 2026-10-15
updated: 2026-10-15
tags:
  - cybersecurity
  - cryptography-and-resilience
---

Cryptographic controls protect different properties. Integrity concerns unauthorized changes to data. Encryption protects confidentiality by transforming readable plaintext into ciphertext using an algorithm and a key. Authenticity and non-repudiation concern evidence about origin and responsibility.

Understanding the property first helps explain why a particular mechanism is needed and what it can establish.

## Integrity and Authenticated Records

In the confidentiality, integrity, and availability (CIA) triad, integrity protects information against unauthorized alteration and supports checking its accuracy. Consider a bank transaction whose amount changes from one hundred to one thousand. Comparison with an authenticated record can reveal the modification.

A plain hash stored beside editable data is insufficient against an attacker who can replace both. Protected authentication codes, digital signatures, or tamper-evident records can support meaningful verification. The verification mechanism must preserve something the attacker cannot simply replace along with the data.

## Origin and Accountability

A digital signature can link a message to a signing identity and support non-repudiation: verifiable evidence that helps establish message origin. This depends on reliable identity binding and protection of signing keys.

Encryption alone does not necessarily authenticate data. When confidentiality, integrity, and authenticity are needed together, authenticated encryption addresses those combined requirements. Hiding a message's content and establishing its origin are distinct security goals.

## Forward Secrecy

Elliptic Curve Diffie-Hellman Ephemeral (ECDHE) uses fresh temporary key-exchange secrets. With forward secrecy, later compromise of a long-term private key does not reveal past session keys.

This property depends on secure generation of fresh ephemeral secrets and their deletion. Static RSA key exchange lacks it. The distinction concerns key exchange, so an RSA signature label should not be confused with evidence of static RSA key exchange.

## Reading Certificate Information

A certificate has a validity period. If its expiration date has passed, it is outside that period. This is a general interpretation of certificate validity, rather than a diagnosis of a particular website.

The label `sha256RSA` indicates SHA-256 hashing with an RSA digital signature. It describes a signature algorithm; it does not by itself establish that a certificate is within its validity dates or that all aspects of a connection are secure.

## Limits and Tradeoffs

Cryptographic evidence depends on protected keys, trustworthy identity binding, and appropriate verification. Digital signatures support accountability without guaranteeing that disputes are impossible. A certificate's signature algorithm and its validity period address different parts of certificate validation.

## References

- [NIST: Integrity](https://csrc.nist.gov/glossary/term/integrity)
- [NIST: Non-Repudiation](https://csrc.nist.gov/glossary/term/non_repudiation)
- [NIST: Encryption](https://csrc.nist.gov/glossary/term/encryption)
- [IETF: Elliptic Curve Cryptography for TLS](https://www.rfc-editor.org/rfc/rfc8422.html#section-2)
- [IETF: Certificate Validity](https://www.rfc-editor.org/rfc/rfc5280#section-4.1.2.5)
- [IETF: RSA Algorithm Identifiers for Certificates](https://www.rfc-editor.org/rfc/rfc4055)

## Related Concepts

- [[Cybersecurity/detection-and-response/investigation-ready-logs|Investigation-Ready Logs]]
- [[Cybersecurity/cryptography-and-resilience/availability-recovery-and-ransomware|Availability, Recovery and Ransomware]]
- [[Cybersecurity/cryptography-and-resilience/index|Cryptography and Resilience]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
