---
title: Application Secrets
description: Keep privileged credentials outside code and browsers, detect accidental exposure, and invalidate leaked copies.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, application-and-delivery-security]
---

Application secrets include credentials and privileged API keys that grant access to services. Keep them outside source code, retrieve them securely when the application needs them, and limit their permissions and lifetime.

Secret handling spans storage, exposure prevention, and response. Moving a key out of code improves future handling, but a leaked copy continues to work until its authority ends.

## Keeping Secrets Outside the Repository

A secrets manager provides a place for credentials that applications can retrieve at runtime. Short time-to-live values, or TTLs, limit how long credentials remain valid where the service supports that model.

Revoke or rotate secrets that have already been exposed. Removing a value from the current source file or moving it into a secrets manager does not invalidate copies an attacker may hold.

The sequence matters: improve storage and end the exposed credential's usefulness. Neither action supplies the other.

## Detecting Accidental Exposure

Secret scanning can find API keys and other credentials committed to a repository. Integrating scanning into continuous integration helps identify mistakes as changes pass through the delivery process.

CI checks can run after publication. Pre-commit scanning or push protection adds an earlier opportunity to block a secret from reaching the repository. Combine those checks with storing secrets outside it.

Encoding a credential with Base64 does not protect it. The application still contains a recoverable representation of the same secret.

## Protecting Browser Applications

A single-page application, or SPA, runs in a browser that users can inspect. It cannot keep an embedded privileged API key confidential.

Keep that key on a backend proxy and give users access scoped to their own needs. The backend must authenticate callers and authorize their requests so it does not offer unrestricted use of the upstream API.

Use short-lived, scoped tokens for delegated access. A backend-for-frontend can retain tokens on the server. Public client identifiers have a different purpose and do not need treatment as confidential secrets.

## Limits and Tradeoffs

Scanning detects exposure, while revocation or rotation ends the leaked credential's validity. A successful scan result does not remove the need to store credentials appropriately, and a storage change does not repair earlier exposure.

A proxy also needs its own access controls. Moving a privileged key to a server helps only when the server restricts what each caller can do with it. Scope and lifetime should match the access the application and its users require.

## References

- [OWASP: Secrets management](https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html) covers storage, runtime use, and credential lifecycle.
- [GitHub: Secret scanning](https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning) describes repository exposure detection.
- [GitHub: Push protection](https://docs.github.com/en/code-security/concepts/secret-security/push-protection) describes blocking secrets during a push.
- [RFC 6749: Client types](https://www.rfc-editor.org/rfc/rfc6749.html#section-2.1) distinguishes public and confidential clients.

## Related Concepts

- [[Cybersecurity/application-and-delivery-security/index|Application and Delivery Security]]
- [[Cybersecurity/network-and-cloud-controls/cloud-permissions-and-change-visibility|Cloud Permissions and Change Visibility]]
- [[Cybersecurity/application-and-delivery-security/dependencies-builds-and-containers|Dependencies, Builds and Containers]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
