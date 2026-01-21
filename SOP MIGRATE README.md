# Standard Operating Procedure (SOP's) for **Migrate**

## Step-by-step Installation Guide for **Migrate** on Ubuntu

---

## Authors

| Author           | Created    | Version | Last updated by  | Last Edited On |  L0 Reviewer | L1 Reviewer | L2 Reviewer |
| ---------------- | ---------- | ------- | ---------------- | -------------- | ------------ | ----------- | ----------- | 
| Abhinav Sikarwar | 2026-01-17 | 1.0     | Abhinav Sikarwar | 2026-01-17     |              |             |             |             

---

## Table of Contents

1. [Pre-requisites](#pre-requisites)
2. [Software Overview](#software-overview)
3. [System Requirement](#system-requirement)
4. [Dependencies](#dependencies)
5. [Installation – Ubuntu](#installation--ubuntu)
6. [Quick Usage Test](#quick-usage-test)
7. [Troubleshooting](#troubleshooting-ubuntu)
8. [Uninstall migrate](#uninstall-migrate)
9. [Examples](#examples)
10. [Summary](#summary)

---

<a id="pre-requisites"></a>

## Pre-requisites

| License Type | Description                                          | Commercial Use | Open Source |
| ------------ | ---------------------------------------------------- | -------------- | ----------- |
| MIT License  | Free for public use, modification and redistribution | Yes            | Yes         |

---

<a id="software-overview"></a>

## Software Overview

| Software | Version |
| -------- | ------- |
| migrate  | 4.16.2  |

---

<a id="system-requirement"></a>

## System Requirement

| Requirement             | Minimum Recommendation         |
| ----------------------- | ------------------------------ |
| Processor/Instance Type | Dual-Core / t2.micro or higher |
| RAM                     | 1 GB or Higher                 |
| ROM (Disk Space)        | 5 GB or Higher                 |
| OS Required             | Linux (Ubuntu Recommended)     |

---

<a id="dependencies"></a>

## Dependencies

### Run-time Dependency

| Run-time Dependency | Version            | Description                                                       |
| ------------------- | ------------------ | ----------------------------------------------------------------- |
| **glibc / libc6**   | Default OS version | Standard C library used by compiled migrate binaries              |
| **Database Client** | DB-specific        | Required for connecting Postgres/MySQL/SQLite to apply migrations |

➡️ **Explanation:**
Migrate binaries depend on the Linux C runtime.
If you plan to migrate PostgreSQL or MySQL, ensure the respective database client is installed.

---

### Other Dependency

| Other Dependency | Version                  | Description                                    |
| ---------------- | ------------------------ | ---------------------------------------------- |
| **curl / wget**  | Latest package available | Used to download migrate binary releases       |
| **bash / shell** | Default OS shell         | Needed to run migration commands and pipelines |

➡️ **Explanation:**
Database migration tools fit naturally into CLI pipelines.
`curl` downloads the binary, and the shell executes migration commands.

---

<a id="installation--ubuntu"></a>

## 🚀 Installation — Ubuntu (Binary Release)

> This is the **recommended method** from the official repository.

### 1️⃣ Install wget if missing

```bash
sudo apt-get update -y
sudo apt-get install wget -y
```

<img width="954" height="383" alt="image" src="https://github.com/user-attachments/assets/53751a2a-b566-45be-b4ad-5ea322be7857" />

---

### 2️⃣ Download migrate binary

```bash
wget https://github.com/golang-migrate/migrate/releases/download/v4.16.2/migrate.linux-amd64.tar.gz
```

<img width="1919" height="604" alt="image" src="https://github.com/user-attachments/assets/80cdfb38-fef7-40e1-a32e-e334295de473" />

---

### 3️⃣ Extract the archive

```bash
tar -xvf migrate.linux-amd64.tar.gz
```

<img width="621" height="107" alt="image" src="https://github.com/user-attachments/assets/6b03ce21-4f30-4464-8038-3089aec6b5d0" />

---

### 4️⃣ Move binary to PATH

```bash
sudo mv migrate /usr/local/bin/
```

<img width="628" height="23" alt="image" src="https://github.com/user-attachments/assets/d1047aae-7e8a-4a42-b22d-4f9b902b8106" />

---

### 5️⃣ Add executable permissions

```bash
sudo chmod +x /usr/local/bin/migrate
```

<img width="610" height="20" alt="image" src="https://github.com/user-attachments/assets/16098a48-8306-4d32-94f7-1c8193c1b5c1" />

---

### 6️⃣ Verify installation

```bash
migrate -version
```

Expected output:

```
4.16.2
```

<img width="368" height="69" alt="image" src="https://github.com/user-attachments/assets/b25c8aac-ccfb-4479-a660-0fa55ec3537d" />

---

<a id="quick-usage-test"></a>

## 🧪 Quick Usage Test

### 1️⃣ Create a migration file

```bash
migrate create -ext sql -dir migrations create_users_table
```

<img width="890" height="86" alt="image" src="https://github.com/user-attachments/assets/c90b16c9-9c40-4977-bc1e-312294afc559" />

---

### 2️⃣ Verify files

```bash
ls migrations/
```

<img width="960" height="72" alt="image" src="https://github.com/user-attachments/assets/47f140a1-35bb-4bbd-bd5e-381ca973c8b4" />

---

<a id="troubleshooting-ubuntu"></a>

## 🛠 Troubleshooting (Ubuntu)

| Issue                        | Fix                                              |
| ---------------------------- | ------------------------------------------------ |
| `migrate: command not found` | Ensure binary exists in `/usr/local/bin`         |
| Cannot connect to database   | Verify DB is running and credentials are correct |
| `down` command not available | Ensure `.down.sql` files exist                   |
| Permission denied            | Run `sudo chmod +x /usr/local/bin/migrate`       |

---

<a id="uninstall-migrate"></a>

## 🧹 Uninstall migrate

```bash
sudo rm /usr/local/bin/migrate
rm -rf migrations/
```

<img width="954" height="46" alt="image" src="https://github.com/user-attachments/assets/4a9475b4-d3f3-4c5c-80c1-1870b9333b51" />

---

<a id="summary"></a>

## 📌 Summary

`migrate` is a powerful CLI tool for **managing database schema evolution**.
By tracking changes using versioned migration scripts, it ensures consistency across **development, staging, and production** environments.

Migrate enables **safe, repeatable, and reversible** database changes and integrates seamlessly with CI/CD pipelines.

---


