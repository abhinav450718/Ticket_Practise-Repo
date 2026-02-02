# Project VCS Policies – Naming Conventions

---

## Authors

| Author           | Created    | Version | Last Edited On | L0 Reviewer | L1 Reviewer | L2 Reviewer |
| ---------------- | ---------- | ------- | -------------- | ----------- | ----------- | ----------- |
| Abhinav Sikarwar | 2026-02-02 | 1.0     | 2026-02-02     | Aayush Verma| Shreya Jaiswal| Ashwin    |

---

## Version History

| Version | Date       | Description                          | Author           |
| ------- | ---------- | ------------------------------------ | ---------------- |
| 1.0     | 2026-02-02 | Project VCS Naming Convention Policy | Abhinav Sikarwar |

---

## Table of Contents

1. [Introduction](#introduction)
2. [Branch Name Template](#branch-name-template)
3. [Tag Template](#tag-template)
4. [Commit Message Template](#commit-message-template)
5. [Detailed Documentation](#detailed-documentation)
6. [Governance & Enforcement](#governance--enforcement)
7. [Acceptance Criteria Coverage](#acceptance-criteria-coverage)
8. [Contact Information](#contact-information)
9. [References](#references)

---

## Introduction

This document defines the Project Version Control System (VCS) Policies with a specific focus on naming conventions for branches, tags, and commit messages across all repositories. 

The purpose of this policy is to establish standardized version control practices that ensure consistency, traceability to Jira tickets, structured release management, and improved collaboration among development teams. By enforcing uniform naming conventions and commit standards, the project maintains clear change history, enhances audit readiness, and supports disciplined release governance. These conventions are mandatory for all contributors and apply to feature development, defect resolution, hotfixes, release preparation, and maintenance activities.

---

## Branch Name Template

### Standard Format

```
<branch-type>/<JIRA-ID>-<short-description>
```

### Allowed Branch Types

| Type    | Purpose                          |
| ------- | -------------------------------- |
| feature | New feature implementation       |
| bugfix  | Non-production defect resolution |
| hotfix  | Production critical fix          |
| release | Release preparation branch       |
| chore   | Refactoring / maintenance        |

### Rules

* All branch names must be lowercase
* Words must be separated using hyphen (-)
* Jira ID is mandatory (except release branches)
* No special characters allowed
* Branch names should not exceed 100 characters
* Description must clearly represent the change

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

Tags represent stable and production-ready releases.

### Standard Format (Semantic Versioning)

```
v<major>.<minor>.<patch>
```

### Versioning Guidelines

* Major → Breaking changes
* Minor → Backward-compatible feature additions
* Patch → Bug fixes

### Examples

```
v1.0.0
v1.2.3
v2.0.0
```

### Tag Rules

* Tags must be created only from the `main` branch
* Tags must represent approved and tested releases
* Tags are immutable once created

---

## Commit Message Template

All commits must follow the Conventional Commit format.

### Standard Format

```
<type>(<scope>): <short-summary>

[optional body]

Refs: <JIRA-ID>
```

### Allowed Types

| Type     | Description           |
| -------- | --------------------- |
| feat     | New feature           |
| fix      | Bug fix               |
| docs     | Documentation changes |
| refactor | Code restructuring    |
| test     | Test updates          |
| chore    | Maintenance tasks     |

### Example Commit

```
feat(auth): implement JWT validation

Added middleware for token validation.
Improved error handling mechanism.

Refs: PROJ-101
```

### Commit Rules

* Subject must not exceed 50 characters
* Use imperative tone (add, fix, update)
* Every commit must reference a Jira ID
* Avoid generic messages (e.g., "code update")

---

## Detailed Documentation

The project follows a controlled branching strategy to maintain code stability, release discipline, and clear traceability of changes.

### Branching Workflow

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
main → hotfix/PROJ-ID-description → fix & validate → main → tag patch version → back-merge to develop
```

---

## Governance & Enforcement

To ensure compliance with this policy:

* `main` branch is protected
* Direct commits to `main` are prohibited
* CI pipelines validate commit message format
* Pull Requests require reviewer approval
* Only authorized maintainers can create release tags
* Merged branches must be deleted after integration

Non-compliance with these policies may result in pull request rejection.

---

## Acceptance Criteria Coverage

| Acceptance Requirement          | Status      |
| ------------------------------- | ----------- |
| Branch Name Template Defined    | ✔ Completed |
| Tag Template Defined            | ✔ Completed |
| Commit Message Template Defined | ✔ Completed |
| Detailed Documentation Provided | ✔ Completed |

---

## Contact Information

| Name             | Email                                                                     |
| ---------------- | ------------------------------------------------------------------------- |
| Abhinav Sikarwar | [abhinav.sikarwar@mygurukulam.co](mailto:abhinav.sikarwar@mygurukulam.co) |

For clarifications regarding these VCS policies, contributors may contact the repository maintainers or DevOps team.

---

## References

| Reference                          | Description                                            |
| ---------------------------------- | ------------------------------------------------------ |
| Git Official Documentation         | Version control standards and branching best practices |
| Conventional Commits Specification | Standard for commit message structure                  |
| Semantic Versioning (SemVer)       | Version numbering guidelines                           |

---


