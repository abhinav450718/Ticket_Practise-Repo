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
| migrate  | Fill version here |

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

### 2️⃣ Download migrate latest binary

```bash
wget https://github.com/golang-migrate/migrate/releases/download/v4.16.2/migrate.linux-amd64.tar.gz
```

*(Replace version as needed)*

### 3️⃣ Extract the archive

```bash
tar -xvf migrate.linux-amd64.tar.gz
```

### 4️⃣ Move binary to PATH

```bash
sudo mv migrate /usr/local/bin/
```

### 5️⃣ Add executable permissions

```bash
sudo chmod +x /usr/local/bin/migrate
```

### 6️⃣ Verify installation

```bash
migrate -version
```

Expected output (example):

```
v4.16.2
```

---

## 🧪 Quick Usage Test

### 1️⃣ Create a migration file

```bash
migrate create -ext sql -dir migrations create_users_table
```

Output:

```
migrations/000001_create_users_table.up.sql
migrations/000001_create_users_table.down.sql
```

### 2️⃣ Check files exist

```bash
ls migrations/
```

### 3️⃣ Test migration apply (example: SQLite)

```bash
migrate -database sqlite3://sample.db -path migrations up
```

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

