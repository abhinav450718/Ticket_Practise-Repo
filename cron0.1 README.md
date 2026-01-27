# Standard Operating Procedure (SOP) for **Cron**

## Guide to Create, Edit, and Manage Cron Jobs on Linux (Ubuntu)

---

## Purpose

This SOP explains **how to create, edit, and manage cron jobs**, including **cron syntax** and **how to check cron logs** to verify scheduled task execution.

---

## What is Cron?

Cron is a **time-based job scheduler** in Unix/Linux systems used to **automatically run commands or scripts at scheduled times or intervals**.

Cron runs as a background service (`cron`) and executes tasks defined in a **crontab (cron table)**.

---

## Why Cron is Used

Cron is commonly used to:

* Automate repetitive tasks
* Schedule backups
* Rotate logs
* Clean temporary files
* Run monitoring scripts
* Perform periodic maintenance

Cron eliminates **manual execution** and ensures **consistent automation**.

---

## Cron Components

| Component   | Description                                |
| ----------- | ------------------------------------------ |
| cron daemon | Background service that executes cron jobs |
| crontab     | File containing scheduled cron jobs        |
| cron job    | A scheduled command or script              |
| syslog      | System log where cron activity is recorded |

---

## Cron Syntax (Scheduling Format)

```text
* * * * * command_to_execute
│ │ │ │ │
│ │ │ │ └── Day of week (0–7) (Sunday = 0 or 7)
│ │ │ └──── Month (1–12)
│ │ └────── Day of month (1–31)
│ └──────── Hour (0–23)
└────────── Minute (0–59)
```

### Common Scheduling Examples

| Schedule          | Cron Expression |
| ----------------- | --------------- |
| Every minute      | `* * * * *`     |
| Every day at 2 AM | `0 2 * * *`     |
| Every Sunday      | `0 0 * * 0`     |
| Every 5 minutes   | `*/5 * * * *`   |

---

## How to Create a Cron Job

### Step 1 — Open crontab editor

```bash
crontab -e
```

### Step 2 — Add cron entry

Example: run a script every minute

```bash
* * * * * /bin/bash /path/to/script.sh
```

### Step 3 — Save and exit

The cron job is installed automatically.

---

## How to Edit a Cron Job

To modify existing cron jobs:

```bash
crontab -e
```

* Update the required entry
* Save and exit

---

## How to Manage Cron Jobs

### List cron jobs

```bash
crontab -l
```

### Remove all cron jobs

```bash
crontab -r
```

### Remove cron jobs with confirmation

```bash
crontab -i -r
```

---

## How to Verify Cron Job Execution

### Redirect output to a log file (recommended)

```bash
* * * * * /path/to/script.sh >> /tmp/cron.log 2>&1
```

Check execution output:

```bash
cat /tmp/cron.log
```

This confirms whether the job executed successfully.

---

## How to Check Cron Logs

### Ubuntu / Debian Systems

Cron activity is logged in:

```bash
/var/log/syslog
```

Filter cron entries:

```bash
grep CRON /var/log/syslog
```

Live monitoring:

```bash
tail -f /var/log/syslog | grep CRON
```

> Note: Syslog may contain **other system cron jobs** as well.

---

## Troubleshooting Cron Jobs

| Issue                                  | Cause                            | Solution                       |
| -------------------------------------- | -------------------------------- | ------------------------------ |
| Cron job not running                   | Cron service stopped             | `sudo systemctl start cron`    |
| Script works manually but not via cron | Environment variables missing    | Define variables inside script |
| Permission denied                      | Script not executable            | `chmod +x script.sh`           |
| No output                              | Output not redirected            | Redirect stdout & stderr       |
| Log file empty                         | Script writes directly to a file | Expected behavior              |

---

## Best Practices

* Always use **absolute paths**
* Explicitly specify shell (`/bin/bash`)
* Test scripts manually before scheduling
* Redirect output for debugging
* Keep cron jobs small and simple
* Avoid heavy jobs at frequent intervals
* Document cron jobs clearly

---

## Summary

Cron is a reliable Linux scheduling tool used to automate recurring tasks.
Understanding **cron syntax**, **job creation**, **editing**, **management**, and **log verification** ensures stable, predictable, and auditable automation in DevOps environments.

---

## References

* [https://man7.org/linux/man-pages/man5/crontab.5.html](https://man7.org/linux/man-pages/man5/crontab.5.html)
* [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
* [https://crontab.guru](https://crontab.guru)

---
