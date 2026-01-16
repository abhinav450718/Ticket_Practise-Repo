#  Standard Operating Procedure (SOP's) for JQ

## Step by step installation guide for **JQ** on Ubuntu

---

## Pre-requisites

| License Type | Description                                          | Commercial Use | Open Source |
| ------------ | ---------------------------------------------------- | -------------- | ----------- |
| MIT License  | Free for public use, modification and redistribution | Yes            | Yes         |

---

## Software Overview

| Software | Version           |
| -------- | ----------------- |
| jq       | Fill version here |

---

## System Requirement

| Requirement             | Minimum Recommendation         |
| ----------------------- | ------------------------------ |
| Processor/Instance Type | Dual-Core / t2.micro or higher |
| RAM                     | 1 GB or Higher                 |
| ROM (Disk Space)        | 5 GB or Higher                 |
| OS Required             | Linux (Ubuntu Recommended)     |

---

## Dependencies

### Run-time Dependency

| Run-time Dependency | Version            | Description                                                   |
| ------------------- | ------------------ | ------------------------------------------------------------- |
| **glibc / libc6**   | Default OS version | Core Linux C library required to execute compiled jq binaries |

➡️ Explanation:
jq is written in C, so it needs the GNU C standard library (already available in Ubuntu).
No manual installation needed — it comes pre-installed with Linux.

### Other Dependency

| Other Dependency | Version                  | Description                                                            |
| ---------------- | ------------------------ | ---------------------------------------------------------------------- |
| **curl / wget**  | Latest package available | Used to fetch API responses or download JSON before processing with jq |
| **bash / shell** | Default OS shell         | jq is typically used inside bash scripts and CLI pipelines             |


➡️ Explanation:

jq itself does not require extra runtime packages

But in real DevOps workflows, we pair jq with curl to pull JSON from APIs:
```
curl https://api.github.com/users/octocat | jq '.id'
```
Bash or shell environments are required to pipe JSON → jq
---

##  Installation — Ubuntu (Debian-based Systems)

### 1️⃣ Update Package Index

```bash
sudo apt-get update -y
```
<img width="955" height="588" alt="image" src="https://github.com/user-attachments/assets/1d8b69af-bc4c-4043-930b-97a0e64a1086" />

### 2️⃣ Install jq

```bash
sudo apt-get install jq -y
```
<img width="952" height="363" alt="image" src="https://github.com/user-attachments/assets/0605c23e-ca5e-4ef7-ab28-aca5e870abe8" />

### 3️⃣ Verify Installation

```bash
jq --version
```

Expected output (example):

<img width="954" height="61" alt="image" src="https://github.com/user-attachments/assets/41e749e6-96ef-4d3c-9b7d-50288c3d0d62" />


---

##  Quick Usage Test

### Test JSON extraction

### Step 1 — Create sample.json

```
echo '{"name":"Abhinav","batch":32,"tool":"jq"}' > sample.json

```
### Step 2 — Run jq now
```
jq '.' sample.json

```
### Pretty-print a JSON file

```
{
  "name": "Abhinav",
  "batch": 32,
  "tool": "jq"
}

```
### Output
<img width="877" height="166" alt="image" src="https://github.com/user-attachments/assets/4e4a26cc-fa0d-4764-8311-9ac264f7ded5" />

---

##  Troubleshooting (Ubuntu)

| Issue                           | Fix                                       |                                  |
| ------------------------------- | ----------------------------------------- | -------------------------------- |
| `jq: command not found`         | Reinstall using `sudo apt-get install jq` |                                  |
| Output unreadable/no formatting | Use pipe `                                | jq` after command producing JSON |
| Permission denied errors        | Run commands with `sudo` if required      |                                  |

---

##  Uninstall jq

```bash
sudo apt-get remove jq -y
```
<img width="953" height="264" alt="image" src="https://github.com/user-attachments/assets/b9b4184a-22ae-4893-a1c5-3d15033618de" />

---

## Examples

| Command            | Purpose           |                       |
| ------------------ | ----------------- | --------------------- |
| `jq '.' file.json` | Pretty print JSON |                       |
| `curl ...          | jq '.id'`         | Extract key from API  |
| `.[]               | select(.active)`  | Filter matching items |

Bhai, **perfect polished summary** added — paste this at the end of your README 🚀
(Or I can merge it for you if you want.)

---

## 📌 Summary

`jq` is a lightweight yet powerful command-line utility designed for **processing JSON data efficiently**.
It fits naturally into Linux workflows by allowing users to **query, filter, format, and transform structured data** without writing additional code.

Because modern DevOps tooling, cloud services, and APIs rely heavily on JSON, jq becomes a **critical productivity tool** across:

* Debugging and log analysis
* CI/CD pipelines
* API interaction
* Cloud automation (AWS, Kubernetes, Terraform, Docker)

With **minimal system requirements**, **almost no dependencies**, and **easy installation**, jq delivers high value for:

* System administrators
* DevOps engineers
* Cloud practitioners
* Anyone working with structured JSON data

In short, jq makes JSON **simple, readable, and actionable**, enabling faster decision making and more reliable automation.

---

🎯 Bullet punchline:

> jq helps turn raw JSON data into meaningful information — quickly, cleanly, and directly from the terminal.

---

