# Make Intro Documentation

---

## Authors

| Author           | Created    | Version | Last updated by  | Last Edited On | Pre Reviewer | L0 Reviewer | L1 Reviewer | L2 Reviewer |
| ---------------- | ---------- | ------- | ---------------- | -------------- | ------------ | ----------- | ----------- | ----------- |
| Abhinav Sikarwar | 2026-01-20 | 1.0     | Abhinav Sikarwar | 2026-01-20     |              |             |             |             |

---

## Index

1. [Introduction](#introduction)
2. [Why Make?](#why-make)
3. [What Make Does](#what-make-does)
4. [Key Features](#key-features)
5. [Contact Information](#contact-information)
6. [References](#references)
7. [End Note](#end-note)

---

<a id="introduction"></a>

## Introduction

`make` is a powerful build automation utility commonly used in software development to **compile code, run workflows, manage dependencies, and automate repetitive tasks**.
Using rules defined in a simple configuration file (`Makefile`), Make determines what tasks need to be executed and in what order — ensuring only required steps are run.

Make originated in the UNIX ecosystem and continues to be one of the **most widely used automation tools** in DevOps, CI/CD, and open-source projects.

---

<a id="why-make"></a>

## Why Make?

Modern software projects often require:

* Compiling source code
* Running test suites
* Packaging artifacts
* Regenerating files when dependencies change
* Automating multi-step commands

Without automation, developers must execute many commands manually — which is **slow, error-prone, and inconsistent**.

`make` solves these problems by:

* Automating command execution
* Understanding what needs to be rebuilt based on file changes
* Enforcing repeatable builds across machines
* Reducing human mistakes
* Eliminating redundant tasks
* Serving as a simple build orchestrator (even outside C/C++)

Make continues to be a **foundation of build automation**, used directly or indirectly by:

* Linux kernel
* GNU projects
* Docker image builds
* CI tools (GitHub Actions, Jenkins, GitLab CI)
* Infrastructure automation workflows

---

<a id="what-make-does"></a>

## What Make Does

At its core, Make:

✔ Uses a **Makefile** to define tasks (targets)
✔ Tracks **dependencies** between files
✔ Executes rules **only when required**
✔ Allows **custom commands**, not just compilation
✔ Works with **any language or script**

---

<a id="key-features"></a>

## Key Features

| Feature                     | Description                                                         |
| --------------------------- | ------------------------------------------------------------------- |
| Declarative Task Rules      | Define what to build and how using simple syntax in a `Makefile`    |
| Incremental Build Execution | Only rebuilds files that changed, saving time                       |
| Dependency Handling         | Automatically runs prerequisite tasks before a target is executed   |
| Extensible Command Support  | Can run shell commands, scripts, tests, docker builds, etc          |
| Platform Agnostic           | Works on Linux, macOS, WSL, and inside containers                   |
| Silent / Verbose Modes      | Control logging and output as per debugging requirements            |
| Widely Adopted in DevOps    | Used in CI pipelines, automation scripts, and open-source workflows |

---

<a id="contact-information"></a>

## Contact Information

For questions, clarifications, or review feedback related to this documentation, please contact:

| Contact Type | Details                                                             |
| ------------ | ------------------------------------------------------------------- |
| Name         | Abhinav Sikarwar                                                    |
| Role         | DevOps Engineer                                                     |
| Email        | [abhinav.sikarwar@mygurukulam.co](mailto:abhinav.sikarwar@mygurukulam.co) |
| Team         | Saarthi                                                             |

---

<a id="references"></a>

## References

| Links                                                                                                          | Descriptions              |
| -------------------------------------------------------------------------------------------------------------- | ------------------------- |
| [https://makefiletutorial.com/](https://makefiletutorial.com/)                                                 | Beginner Friendly Guide   |


---

<a id="end-note"></a>

## End Note

This document provides an introductory understanding of `make` — what it is, why it is used, and the key features that make it a foundational tool in build automation and DevOps practices.

---

