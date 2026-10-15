---
title: Least Privilege
description: Grant only the permissions a task requires and use carefully scoped roles to keep access limited.
created: 2026-10-15
updated: 2026-10-15
tags: [cybersecurity, identity-and-access]
---

Least privilege means granting only the permissions someone needs to perform an assigned task. The principle applies to administrators as well as ordinary users. An administrator who manages accounts may need substantial access to user records while having no reason to change billing settings or grant unrestricted administrator privileges.

The starting point is the work itself. Identify the task, identify the actions and resources it requires, then grant access that matches those requirements.

## Turning Duties into Permissions

Consider a new administrator for a software-as-a-service application, often called SaaS. The service runs online, and the organization assigns someone to maintain its user accounts. That person needs permission to add accounts and disable access when people leave.

A role for those duties can exclude billing access and the authority to create full administrators. This example shows how a narrow permission set can support useful administrative work without giving its holder control over the entire service.

The same reasoning applies when considering a new permission. Ask which assigned duty requires it and whether a narrower permission would support that duty.

## Using Roles with Care

Role-based access control, or RBAC, groups permissions into roles that administrators assign to people. A user-management role can make access easier to apply consistently across a team.

RBAC provides a mechanism for organizing permissions. Least privilege supplies the principle for deciding what those permissions should include. A broadly defined administrator role can grant excessive access even when the organization uses RBAC throughout its systems.

Review the role's actual permissions before assigning it. A useful name alone does not establish an appropriate scope.

## Limits and Tradeoffs

The required permission set depends on the duties and controls available in the application. A service with coarse administrative roles may offer fewer ways to separate responsibilities. Document the gap between the required tasks and the access the service grants.

Least privilege also needs attention when responsibilities change. An access decision that fit an earlier job may exceed the needs of a later one. For occasional sensitive work, combine narrow permissions with a limited access period, as described in [[Cybersecurity/identity-and-access/temporary-privileged-access|Temporary Privileged Access]].

## References

- [NIST: Least privilege](https://csrc.nist.gov/glossary/term/least_privilege) defines the principle of limiting privileges to assigned work.
- [NIST: Role-based access control](https://csrc.nist.gov/glossary/term/role_based_access_control) describes organizing access through roles.

## Related Concepts

- [[Cybersecurity/identity-and-access/index|Identity and Access]]
- [[Cybersecurity/identity-and-access/context-and-zero-trust|Context and Zero Trust]]
- [[Cybersecurity/application-and-delivery-security/dependencies-builds-and-containers|Dependencies, Builds and Containers]]
- [[Cybersecurity/topics|All Topics]]
- [[Cybersecurity/references|References and Editorial Method]]
