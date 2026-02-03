# Naming Conventions

---

## Document Details

| Author           | Created    | Version | Last Edited On | L0 Reviewer  | L1 Reviewer    | L2 Reviewer |
| ---------------- | ---------- | ------- | -------------- | ------------ | -------------- | ----------- |
| Abhinav Sikarwar | 2026-02-02 | 1.0     | 2026-02-03     | Aayush Verma | Shreya Jaiswal | Ashwani     |

---

## Index

1. [Introduction](#1-introduction)
2. [Branch Naming Convention](#2-branch-naming-convention)
3. [Tag Naming Convention](#3-tag-naming-convention)
4. [Commit Message Convention](#4-commit-message-convention)
5. [Versioning Guidelines](#5-versioning-guidelines)
6. [General Standards](#6-general-standards)
7. [Compliance](#7-compliance)
8. [Contact Information](#8-contact-information)
9. [References](#9-references)

---

## 1. Introduction

This document defines the Version Control System (VCS) naming conventions and governance standards applicable across all project repositories.

In VCS, a **naming convention** refers to a predefined and structured format used for naming branches, creating release tags, and composing commit messages. These conventions ensure consistency, traceability, maintainability, and audit readiness throughout the development lifecycle.

By enforcing standardized naming practices, teams can:

* Maintain a structured and readable version history
* Improve collaboration and transparency
* Enable controlled and predictable release management
* Support governance and compliance requirements

These standards are generic and independent of any specific branching strategy.

---

## 2. Branch Naming Convention

Branch names must follow a structured and descriptive format.

### 2.1 Branch Naming Template

```
<branch-type>/<reference-id>-<short-description>
```

### 2.2 Naming Rules

* Use lowercase letters only
* Use hyphens (-) to separate words
* Do not use spaces or special characters
* Include a reference ID (ticket/issue ID) when applicable
* Keep the description concise and meaningful
* Recommended maximum length: 100 characters

### 2.3 Example

```
feature/1234-user-authentication
bugfix/5678-login-error
task/8901-config-update
```

---

## 3. Tag Naming Convention

Tags represent stable, validated, and releasable versions of the codebase.

### 3.1 Tag Template

```
v<major>.<minor>.<patch>
```

### 3.2 Versioning Rules (Semantic Versioning)

| Component | Definition                       |
| --------- | -------------------------------- |
| MAJOR     | Breaking or incompatible changes |
| MINOR     | Backward-compatible enhancements |
| PATCH     | Backward-compatible bug fixes    |

### 3.3 Tag Governance Rules

* Tags must follow Semantic Versioning format
* Tags must reference approved and tested code
* Tags are immutable once created
* Tag creation should be restricted to authorized contributors

### 3.4 Example

```
v1.0.0
v2.1.3
```

---

## 4. Commit Message Convention

Commit messages must be clear, structured, and traceable.

### 4.1 Commit Format

```
<type>: <short summary>

[optional detailed description]

Reference: <reference-id>
```

### 4.2 Approved Commit Types

| Type     | Description                                |
| -------- | ------------------------------------------ |
| feat     | New functionality                          |
| fix      | Bug resolution                             |
| docs     | Documentation updates                      |
| refactor | Code restructuring without behavior change |
| test     | Test-related updates                       |
| chore    | Maintenance tasks                          |

### 4.3 Commit Rules

* Summary must be concise (recommended 50–72 characters)
* Use imperative tone (e.g., add, fix, update)
* Avoid vague messages (e.g., “update code”)
* Include reference ID where applicable
* Each commit must represent a single logical change

### 4.4 Example Commit

```
feat: add JWT validation middleware

Implemented token validation logic.
Improved authentication error handling.

Reference: 1234
```

---

## 5. Versioning Guidelines

All releases must follow Semantic Versioning:

```
MAJOR.MINOR.PATCH
```

* MAJOR → Breaking changes
* MINOR → Backward-compatible feature additions
* PATCH → Backward-compatible bug fixes

---

## 6. General Standards

* Direct commits to protected branches must be avoided
* All changes must undergo peer review prior to merge
* Maintain a clean and readable commit history
* Delete stale or obsolete branches after merge
* Ensure naming compliance before creating branches or tags

---

## 7. Compliance

Adherence to this policy is mandatory for all contributors.

Non-compliance with naming conventions, commit formatting, or tagging standards may result in pull request rejection or governance review.

---

## 8. Contact Information

|  Author's  Name  | Email                                                                     |
| ---------------- | ------------------------------------------------------------------------- |
| Abhinav Sikarwar | [abhinav.sikarwar@mygurukulam.co](mailto:abhinav.sikarwar@mygurukulam.co) |

---

## 9. References

| Reference                            | Link                                                                                                                                                                                                                               |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Git Branch Naming Conventions (2025) | [https://medium.com/@jaychu259/git-branch-naming-conventions-2025-the-ultimate-guide-for-developers-5f8e0b3bb9f7](https://medium.com/@jaychu259/git-branch-naming-conventions-2025-the-ultimate-guide-for-developers-5f8e0b3bb9f7) |

---

