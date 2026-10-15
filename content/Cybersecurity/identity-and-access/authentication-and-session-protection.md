---
title: Authentication and Session Protection
description: Distinguish identity verification from permissions and protect logins, sessions, and tokens against theft and replay.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, identity-and-access]
---

Authentication verifies the identity of a user or device. Authorization determines what that identity may access. A successful login establishes identity for an access decision; the application still needs to enforce the user's permissions.

After login, a browser or application often presents a session cookie or token to continue working. Protecting authentication therefore includes protecting the authenticated session and the credentials used with subsequent requests.

## Resisting Stolen Passwords and Phishing

Credential stuffing occurs when attackers test username and password pairs stolen from other breaches. Multifactor authentication, or MFA, requires another factor so a password alone cannot complete the sign-in. Rate limits and bot detection provide additional controls against automated attempts.

Phishing-resistant authentication strengthens this protection. FIDO2 and WebAuthn hardware security keys bind authentication to the legitimate website's domain. A lookalike site cannot obtain a login response that it can use for the legitimate site through the same phishing flow.

Recovery and fallback methods need comparable care. A strong primary method loses value when an attacker can use a weaker recovery route to obtain access.

## Protecting the Authenticated Session

Adversary-in-the-middle phishing relays a sign-in through an attacker-controlled site. The attacker proxies the interaction with the real service and captures an authenticated session cookie. That cookie may let the attacker impersonate the signed-in user.

Some MFA methods can be relayed through this process. FIDO2 and WebAuthn help prevent proxy-based credential phishing through their domain binding. Other ways of stealing an existing session remain possible, so phishing resistance does not remove the need for session protection.

## Restricting Token Replay

A JSON Web Token, or JWT, can carry signed information. Its signature protects against unauthorized alteration, but someone who steals a usable token may still replay it.

Sender-constrained tokens add a requirement beyond possession of the token. Demonstrating Proof of Possession, or DPoP, requires the client to prove control of the private key associated with that token. Channel binding offers another way to constrain token use.

The server must validate the binding or proofs and detect reused proofs. Short token lifetimes reduce the misuse window, while enforced revocation can end access. These controls need to work together.

## Limits and Tradeoffs

Short lifetimes and JWT signatures alone do not prevent replay. MFA also varies in resistance to phishing and session interception. Choose controls for the attack being addressed and verify their enforcement on the server.

Aggressive lockout rules create their own risk: locking an account after a single failure can let an attacker deny access to its legitimate user. Balance automated-attack controls with continued access for legitimate users.

## References

- [NIST: Authentication](https://csrc.nist.gov/glossary/term/authentication) defines identity verification.
- [NIST: Authenticators](https://pages.nist.gov/800-63-4/sp800-63b/authenticators/) covers authentication methods and phishing resistance.
- [OWASP: Credential stuffing prevention](https://cheatsheetseries.owasp.org/cheatsheets/Credential_Stuffing_Prevention_Cheat_Sheet.html) describes layered defenses.
- [RFC 9449: DPoP security considerations](https://www.rfc-editor.org/rfc/rfc9449.html#section-11.1) discusses token and proof replay.
- [Microsoft: Session cookie theft](https://learn.microsoft.com/en-us/defender-xdr/session-cookie-theft-alert) explains session theft alerts and investigation.

## Related Concepts

- [[Cybersecurity/identity-and-access/index|Identity and Access]]
- [[Cybersecurity/identity-and-access/least-privilege|Least Privilege]]
- [[Cybersecurity/detection-and-response/phishing-defense|Phishing Defense]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
