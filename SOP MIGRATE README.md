# Standard Operating Procedure (SOP's) for **Migrate**

## Step-by-step Installation Guide for **Migrate** on Ubuntu

---

## Pre-requisites

| License Type | Description                                          | Commercial Use | Open Source |
| ------------ | ---------------------------------------------------- | -------------- | ----------- |
| MIT License  | Free for public use, modification and redistribution | Yes            | Yes         |

---

## Software Overview

| Software | Version           |
| -------- | ----------------- |
| migrate  |       4.16.2      |

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

| Run-time Dependency | Version            | Description                                                       |
| ------------------- | ------------------ | ----------------------------------------------------------------- |
| **glibc / libc6**   | Default OS version | Standard C library used by compiled migrate binaries              |
| **Database Client** | DB-specific        | Required for connecting Postgres/MySQL/SQLite to apply migrations |

➡️ Explanation:
Migrate binaries depend on the Linux C runtime.
If you plan to migrate PostgreSQL or MySQL, ensure the DB client is installed.

---

### Other Dependency

| Other Dependency | Version                  | Description                                    |
| ---------------- | ------------------------ | ---------------------------------------------- |
| **curl / wget**  | Latest package available | Used to download migrate binary releases       |
| **bash / shell** | Default OS shell         | Needed to run migration commands and pipelines |

➡️ Explanation:
DB migration tools fit into CLI pipelines.
curl downloads the binary.
Bash executes migration commands.

---

## 🚀 Installation — Ubuntu (Binary Release)

> This is the **recommended method** from official repo

### 1️⃣ Install wget if missing

```bash
sudo apt-get update -y
sudo apt-get install wget -y
```
<img width="954" height="383" alt="image" src="https://github.com/user-attachments/assets/53751a2a-b566-45be-b4ad-5ea322be7857" />

### 2️⃣ Download migrate latest binary

```bash
wget https://github.com/golang-migrate/migrate/releases/download/v4.16.2/migrate.linux-amd64.tar.gz
```
<img width="1919" height="604" alt="image" src="https://github.com/user-attachments/assets/80cdfb38-fef7-40e1-a32e-e334295de473" />

*(Replace version as needed)*

### 3️⃣ Extract the archive

```bash
tar -xvf migrate.linux-amd64.tar.gz
```
<img width="621" height="107" alt="image" src="https://github.com/user-attachments/assets/6b03ce21-4f30-4464-8038-3089aec6b5d0" />

### 4️⃣ Move binary to PATH

```bash
sudo mv migrate /usr/local/bin/
```
<img width="628" height="23" alt="image" src="https://github.com/user-attachments/assets/d1047aae-7e8a-4a42-b22d-4f9b902b8106" />

### 5️⃣ Add executable permissions

```bash
sudo chmod +x /usr/local/bin/migrate
```
<img width="610" height="20" alt="image" src="https://github.com/user-attachments/assets/16098a48-8306-4d32-94f7-1c8193c1b5c1" />

### 6️⃣ Verify installation

```bash
migrate -version
```

Expected output (example):

```
4.16.2
```
<img width="368" height="69" alt="image" src="https://github.com/user-attachments/assets/b25c8aac-ccfb-4479-a660-0fa55ec3537d" />

---

## 🧪 Quick Usage Test

### 1️⃣ Create a migration file

```bash
migrate create -ext sql -dir migrations create_users_table
```

Output:

<img width="890" height="86" alt="image" src="https://github.com/user-attachments/assets/c90b16c9-9c40-4977-bc1e-312294afc559" />

### 2️⃣ Check files exist

```bash
ls migrations/
```
<img width="960" height="72" alt="image" src="https://github.com/user-attachments/assets/47f140a1-35bb-4bbd-bd5e-381ca973c8b4" />

---

## 🛠 Troubleshooting (Ubuntu)

| Issue                        | Fix                                                            |
| ---------------------------- | -------------------------------------------------------------- |
| `migrate: command not found` | Recheck binary path or move file to `/usr/local/bin`           |
| Cannot connect to database   | Ensure DB server is running and credentials are correct        |
| `down` command not available | Make sure `.down.sql` scripts exist                            |
| Permission denied            | Add execute permission: `sudo chmod +x /usr/local/bin/migrate` |

---

## 🧹 Uninstall migrate

```bash
sudo rm /usr/local/bin/migrate
rm -rf migrations/
```
<img width="954" height="46" alt="image" src="https://github.com/user-attachments/assets/4a9475b4-d3f3-4c5c-80c1-1870b9333b51" />

---

## Examples

| Command                                               | Purpose                    |
| ----------------------------------------------------- | -------------------------- |
| `migrate create -ext sql -dir migrations init_schema` | Generate migration scripts |
| `migrate -path migrations -database $DB_URL up`       | Apply schema changes       |
| `migrate -path migrations -database $DB_URL down`     | Roll back schema           |
| `migrate -path migrations -database $DB_URL force 1`  | Force migrate version      |

---

## 📌 Summary

`migrate` is a powerful CLI tool for **managing database schema evolution**.
By tracking changes using versioned migration scripts, migrate ensures every environment — dev, stage, and production — stays aligned.

It supports **consistent, repeatable, and reversible** SQL upgrades, making database changes safe, automatable, and CI/CD friendly.

Migrate helps teams avoid schema drift and deployment errors while treating database updates with the same care as application code.

---

🎯 Bullet Punchline:

> migrate brings order, structure, and automation to database schema changes — safely and reliably.

---

