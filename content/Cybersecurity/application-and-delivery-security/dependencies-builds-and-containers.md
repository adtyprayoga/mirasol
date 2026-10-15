---
title: Dependencies, Builds and Containers
description: Combine independent release controls, dependency maintenance, build provenance, image verification, and runtime restrictions.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, application-and-delivery-security]
---

Software delivery connects source code, third-party components, build systems, and production workloads. Protecting that path requires controls over who approves changes, what the build contains, and which artifacts may run.

## Keeping Release Decisions Independent

Continuous integration and continuous delivery or deployment, known as CI/CD, automate building, testing, and releasing software. Separate code creation, independent review and approval, and production deployment authority.

For example, Alice submits a change, Bob approves it, and a protected pipeline deploys it after required checks pass. Alice cannot self-approve or bypass the release controls. A developer can trigger the pipeline if those independent approvals remain enforced.

The separation concerns permissions and decision authority rather than separate departments. Restrict changes to pipeline definitions and protection rules so an author cannot use them to bypass review. Keep production credentials within the controlled release process.

## Maintaining Dependencies and Early Checks

Software composition analysis, or SCA, checks dependencies for known vulnerabilities. A software bill of materials, or SBOM, inventories components, including indirect dependencies. Monitor that inventory and patch vulnerable components after appropriate testing.

Bring security checks into development and CI. Static application security testing, or SAST, examines code. Dynamic application security testing, or DAST, tests a running application and therefore needs a test deployment. Combine automated findings with developer training and review.

## Protecting Builds and Verifying Images

Isolate build jobs and runners, limit token permissions, and keep privileged tokens and secrets away from untrusted pull requests. Verify trusted build provenance to understand the origin of the artifact.

SLSA, Supply-chain Levels for Software Artifacts, provides an integrity framework. Signing supports verification but does not by itself establish that a build process was trustworthy.

For container images, verify the image digest's signature against approved signer and issuer policies. Enforce rejection when verification fails. Image tags can change, so a tag alone does not establish image integrity.

## Restricting Runtime Impact

Seccomp limits system calls, while AppArmor restricts resource access. Narrow node permissions reduce what a compromised workload can reach. Apply these restrictions alongside kernel patching and reduced node privileges.

These controls reduce exploit opportunities and potential impact. They cannot guarantee containment after an attacker achieves full kernel compromise through a container escape.

## Limits and Tradeoffs

An SBOM supplies inventory; remediation addresses the vulnerabilities found in that inventory. A valid signature supports integrity and signer identity; it does not establish that an image is free of vulnerabilities. Keep those assurances separate when deciding whether to release an artifact.

Repository protection features depend on available platform support. Verify that the actual permissions, approval rules, and deployment process enforce the intended separation of duties.

## References

- [NIST: Separation of duty](https://csrc.nist.gov/glossary/term/Separation_of_Duty) defines independent responsibilities.
- [GitHub: Deployments and environments](https://docs.github.com/en/actions/reference/workflows-and-actions/deployments-and-environments) documents release protection controls.
- [CISA: Managing open-source software and SBOMs](https://www.cisa.gov/sites/default/files/2024-08/ESF_SECURING_THE_SOFTWARE_SUPPLY_CHAIN%20RECOMMENDED%20PRACTICES%20FOR%20MANAGING%20OPEN%20SOURCE%20SOFTWARE%20AND%20SOFTWARE%20BILL%20OF%20MATERIALS_508.pdf) covers dependency management.
- [OWASP: DevSecOps guideline](https://owasp.org/www-project-devsecops-guideline/) discusses security in development and delivery.
- [SLSA: Provenance](https://slsa.dev/spec/v1.2/provenance) describes build provenance.
- [GitHub: Secure use of Actions](https://docs.github.com/en/actions/reference/security/secure-use) discusses build-system risks.
- [Sigstore: Image verification](https://docs.sigstore.dev/cosign/verifying/verify/) and [policy enforcement](https://docs.sigstore.dev/policy-controller/overview/) describe signature checks and admission policy.
- [Kubernetes: Linux kernel security constraints](https://kubernetes.io/docs/concepts/security/linux-kernel-security-constraints/) describes runtime restrictions.

## Related Concepts

- [[Cybersecurity/application-and-delivery-security/index|Application and Delivery Security]]
- [[Cybersecurity/application-and-delivery-security/security-during-design|Security During Design]]
- [[Cybersecurity/application-and-delivery-security/application-secrets|Application Secrets]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
