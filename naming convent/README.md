# Project VCS Policies – Naming Conventions

---

## Document Details

| Author           | Created    | Version | Last Edited On | L0 Reviewer  | L1 Reviewer    | L2 Reviewer |
| ---------------- | ---------- | ------- | -------------- | ------------ | -------------- | ----------- |
| Abhinav Sikarwar | 2026-02-02 | 1.0     | 2026-02-02     | Aayush Verma | Shreya Jaiswal | Ashwin      |

---

## Table of Contents

1. Introduction
2. Scope
3. Branch Name Template
4. Tag Template
5. Commit Message Template
6. Branching & Release Workflow
7. Governance & Enforcement
8. Contact Information
9. References

---

## Introduction

This document defines the Version Control System (VCS) naming conventions and governance standards applicable across all repositories within the project ecosystem.

The objective of this policy is to establish:

* Standardized branch naming conventions
* Structured tag versioning
* Consistent commit message formatting
* Clear traceability to Jira tickets
* Controlled release management
* Audit-ready and compliant development practices

These conventions are mandatory for all contributors working on application, microservices, infrastructure, and DevOps repositories.

---

## Scope

This policy applies to:

* Application repositories
* Microservices repositories
* Infrastructure-as-Code repositories
* Automation and DevOps repositories

All contributors must comply with this policy.

---

## Branch Name Template

### Standard Format

```
<branch-type>/<JIRA-ID>-<short-description>
```

---

### Allowed Branch Types

| Type    | Purpose                                      |
| ------- | -------------------------------------------- |
| feature | New feature implementation                   |
| bugfix  | Non-production defect resolution             |
| hotfix  | Production-critical fixes                    |
| release | Release preparation                          |
| chore   | Refactoring, maintenance, dependency updates |

---

### Naming Rules

* Branch names must be lowercase
* Words must be separated using hyphens (-)
* Jira ID is mandatory (except release branches)
* No special characters allowed
* Maximum length: 100 characters
* Description must clearly reflect the change

---

### Examples

```
feature/PROJ-101-user-authentication
bugfix/PROJ-204-null-pointer-exception
hotfix/PROJ-310-payment-timeout
release/v1.3.0
chore/PROJ-450-dependency-update
```

---

## Tag Template

Tags represent stable, production-ready releases.

### Standard Format (Semantic Versioning)

```
v<major>.<minor>.<patch>
```

---

### Versioning Guidelines

| Component | Description                           |
| --------- | ------------------------------------- |
| Major     | Breaking changes                      |
| Minor     | Backward-compatible feature additions |
| Patch     | Bug fixes                             |

---

### Tag Rules

* Tags must be created only from the `main` branch
* Tags must represent approved and tested releases
* Tags are immutable once created
* Only authorized maintainers may create release tags

---

### Examples

```
v1.0.0
v1.2.3
v2.0.0
```

---

## Commit Message Template

All commits must follow the **Conventional Commits** format.

### Standard Format

```
<type>(<scope>): <short-summary>

[optional body]

Refs: <JIRA-ID>
```

---

### Allowed Types

| Type     | Description           |
| -------- | --------------------- |
| feat     | New feature           |
| fix      | Bug fix               |
| docs     | Documentation changes |
| refactor | Code restructuring    |
| test     | Test updates          |
| chore    | Maintenance tasks     |

---

### Commit Rules

* Subject must not exceed 50 characters
* Use imperative tone (add, fix, update)
* Every commit must reference a Jira ID
* Avoid generic messages (e.g., “update code”)
* One logical change per commit

---

### Example Commit

```
feat(auth): implement JWT validation

Added middleware for token validation.
Improved error handling mechanism.

Refs: PROJ-101
```

---

## Branching & Release Workflow

### Development Workflow

```
feature branch
      ↓
Pull Request
      ↓
Code Review
      ↓
Merge to develop
      ↓
Release branch
      ↓
Merge to main
      ↓
Tag creation
```

---

### Release Workflow

```
develop → release/vX.Y.Z → QA validation → main → tag vX.Y.Z
```

---

### Hotfix Workflow

```
main → hotfix/PROJ-ID-description
     → fix & validate
     → merge to main
     → tag patch version
     → back-merge to develop
```

---

## Governance & Enforcement

To ensure compliance with this policy:

* `main` branch is protected
* Direct commits to `main` are prohibited
* Pull Requests require reviewer approval
* CI pipelines validate commit message format
* Jira ID validation is mandatory
* Only maintainers may create release tags
* Merged branches must be deleted after integration

Non-compliance may result in pull request rejection.

---

## Contact Information

| Name             | Email                                                                     |
| ---------------- | ------------------------------------------------------------------------- |
| Abhinav Sikarwar | [abhinav.sikarwar@mygurukulam.co](mailto:abhinav.sikarwar@mygurukulam.co) |

---

## References

| Reference                          | Link                                                                                                                           |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Git Official Documentation         | [https://git-scm.com/docs](https://git-scm.com/docs)                                                                           |
| Conventional Commits Specification | [https://www.conventionalcommits.org/en/v1.0.0/](https://www.conventionalcommits.org/en/v1.0.0/)                               |
| Semantic Versioning (SemVer)       | [https://semver.org/](https://semver.org/)                                                                                     |
| Atlassian Git Branching Guide      | [https://www.atlassian.com/git/tutorials/comparing-workflows](https://www.atlassian.com/git/tutorials/comparing-workflows)     |
| GitHub Flow Documentation          | [https://docs.github.com/en/get-started/quickstart/github-flow](https://docs.github.com/en/get-started/quickstart/github-flow) |

---
