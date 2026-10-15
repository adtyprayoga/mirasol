---
title: Web Vulnerabilities
description: Recognize common failures in query handling, outbound requests, authorization, browser actions, and deserialization.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, application-and-delivery-security]
---

Web applications handle user input, database requests, remote destinations, and authenticated actions. Vulnerabilities arise when the application gives untrusted input authority it should not have or omits a required access check. Each failure needs a control at the point where the application makes that decision.

## Keeping Data Separate from Commands

SQL injection occurs when untrusted input changes the meaning of a database query. Concatenating user input into SQL can let the input affect the command itself.

Parameterized queries, also called prepared statements, keep input separate from SQL commands. Developers should use them for the query construction that accepts user-supplied data.

A web application firewall, or WAF, filters web traffic for common exploits such as SQL injection and cross-site scripting. It provides an additional layer alongside secure coding and patching.

## Restricting Server Requests

Server-Side Request Forgery, or SSRF, occurs when an attacker tricks a server into making unintended requests. In cloud services, access to metadata endpoints can expose credentials.

For example, an application can reject a user-supplied URL that points to an instance metadata endpoint. Blocking metadata and link-local destinations addresses that path. Broader protection also requires destination validation, redirect restrictions, and network egress controls, with equivalent treatment of IPv4 and IPv6.

## Enforcing Access to Each Object

Insecure Direct Object Reference, or IDOR, involves unauthorized access to another person's resource because the application lacks object-level authorization.

An application must check whether the current identity may access the particular requested object. Authentication establishes the identity; it does not establish permission to access every resource the application can retrieve.

SSRF concerns the server's outgoing requests, while IDOR concerns authorization to a requested resource. Diagnose the application's behavior and missing control when distinguishing these failures.

## Validating Browser-Initiated Actions

Cross-Site Request Forgery, or CSRF, tricks a signed-in browser into submitting an unwanted action. SameSite cookie settings limit cross-site cookie sending. Server-validated anti-CSRF tokens help reject forged state-changing requests.

GET requests should not change application state. SameSite supplies defense in depth; HTTPS and input validation alone do not prevent CSRF.

## Handling Serialized Objects Safely

Deserialization rebuilds objects from stored or transmitted data. Avoid unsafe object deserialization and use safe formats with explicitly approved types.

If object signatures form part of the design, verify them before deserializing. A signature does not make a dangerous object type safe, so approved types and safe handling remain the foundation.

## Limits and Tradeoffs

A WAF cannot guarantee complete prevention or repair missing authorization checks in the application. Similarly, blocking a metadata endpoint addresses one SSRF path rather than the entire vulnerability class. Match each safeguard to its purpose and combine preventive application controls with supporting network and traffic controls.

## References

- [OWASP: SQL injection prevention](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html) explains parameterized queries.
- [OWASP: Web application firewall](https://community.owasp.org/Web_Application_Firewall) describes WAF capabilities.
- [OWASP: SSRF prevention](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html) covers destination restrictions.
- [OWASP: IDOR prevention](https://cheatsheetseries.owasp.org/cheatsheets/Insecure_Direct_Object_Reference_Prevention_Cheat_Sheet.html) addresses object-level authorization.
- [OWASP: CSRF prevention](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html) describes request defenses.
- [OWASP: Deserialization](https://cheatsheetseries.owasp.org/cheatsheets/Deserialization_Cheat_Sheet.html) explains safer object handling.

## Related Concepts

- [[Cybersecurity/application-and-delivery-security/index|Application and Delivery Security]]
- [[Cybersecurity/application-and-delivery-security/security-during-design|Security During Design]]
- [[Cybersecurity/identity-and-access/authentication-and-session-protection|Authentication and Session Protection]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
