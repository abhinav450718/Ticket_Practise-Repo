# Standard Operating Procedure (SOP)

## Managing Cron Jobs on Ubuntu (Create, Edit, View, Delete & Monitor)

---

## Objective

This SOP explains how to create, edit, manage, verify, and troubleshoot cron jobs on Ubuntu Linux.
It also covers cron job syntax and methods to check system logs to ensure scheduled tasks are running properly.

---

## Scope

Applies to:

* Developers
* System administrators
* DevOps engineers
* Anyone responsible for scheduling automated tasks on Linux systems

---

## Prerequisites

* Ubuntu/Linux machine
* Terminal access
* Basic command-line knowledge
* Appropriate permissions to create user or system-level cron jobs
* Scripts or commands ready to be scheduled

---

## Terminology

| Term     | Description                                          |
| -------- | ---------------------------------------------------- |
| Cron     | Linux scheduler daemon that runs tasks based on time |
| Crontab  | File storing cron job definitions for a user         |
| Cron Job | A scheduled command or script executed by cron       |

---

## Cron File Types

| Location              | Purpose                                                         |
| --------------------- | --------------------------------------------------------------- |
| `crontab -e`          | User-specific scheduled jobs                                    |
| `/etc/crontab`        | System-wide cron jobs (requires sudo)                           |
| `/etc/cron.*` folders | Predefined execution intervals (hourly, daily, weekly, monthly) |

---

## Creating or Editing Cron Jobs

### Step 1 — Open Crontab

```
crontab -e
```

### Step 2 — Add a new scheduled task

Example: Run a script at 6:30 PM daily

```
30 18 * * * /home/ubuntu/backup.sh
```

### Step 3 — Save & Exit

* nano: CTRL + O → ENTER → CTRL + X
* vim: `:wq`

### Step 4 — Verify job added

```
crontab -l
```

---

## Cron Scheduling Syntax

Cron expressions contain five time fields followed by a command:

```
* * * * * command
│ │ │ │ └── day of week (0-6)
│ │ │ └──── month (1-12)
│ │ └────── day of month (1-31)
│ └──────── hour (0-23)
└────────── minute (0-59)
```

### Common Examples

| Schedule             | Syntax                    | Description              |
| -------------------- | ------------------------- | ------------------------ |
| Every minute         | `* * * * *`               | Runs constantly          |
| Every 5 minutes      | `*/5 * * * *`             | Executes every 5 minutes |
| Daily at midnight    | `0 0 * * *`               | Standard daily job       |
| Weekly on Sunday 3AM | `0 3 * * 0`               | Weekly maintenance       |
| At system startup    | `@reboot /path/script.sh` | Useful for init tasks    |

---

## Managing Cron Jobs

### View current cron jobs

```
crontab -l
```

### Remove a job

1. Open crontab:

   ```
   crontab -e
   ```
2. Delete the corresponding line

### Remove ALL cron jobs for the user

```
crontab -r
```

> Caution: This cannot be undone

---

## Checking Cron Execution Logs

Cron sends execution events to syslog.
Check recent activity:

```
grep CRON /var/log/syslog
```

Live log monitoring:

```
sudo tail -f /var/log/syslog
```

Filter for current user:

```
grep CRON /var/log/syslog | grep $USER
```

Some systems may use:

```
journalctl -u cron
```

---

## Permission & Script Considerations

Before scheduling a script:

1. Ensure script is executable:

   ```
   chmod +x /path/to/script.sh
   ```

2. Always use **absolute paths** both for files and programs
   Example:

   ```
   /usr/bin/python3 /home/ubuntu/job.py
   ```

3. Test manually first:

   ```
   /path/to/script.sh
   ```

---

## Troubleshooting Guide

| Issue                               | Probable Cause         | Solution                                    |
| ----------------------------------- | ---------------------- | ------------------------------------------- |
| Task works manually but not in cron | Relative paths missing | Use full paths (e.g., `/usr/bin/python3`)   |
| No output/logs                      | Output not redirected  | Append output `>> /var/log/script.log 2>&1` |
| Cron job not present                | Wrong file inspected   | Confirm using `crontab -l`                  |
| Cron service stopped                | Service inactive       | `sudo systemctl start cron`                 |
| Permission denied                   | Script not executable  | `chmod +x file`                             |

---

## Best Practices

* Use descriptive comments in crontabs
* Track scripts in version control
* Log all cron-based jobs to aid troubleshooting
* Avoid scheduling long-running or overlapping tasks
* Use lock files or `flock` for concurrency control
* Monitor system clock or enable NTP time sync

---

## Summary

Cron is a core Linux scheduling tool that runs tasks automatically at defined intervals.
By using crontab correctly, testing commands, applying proper syntax, and monitoring logs, users can automate maintenance, monitoring, and operational workflows efficiently and reliably.

---

## References

| Link                                                                                                                                         | Description                    |
| -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| [https://man7.org/linux/man-pages/man5/crontab.5.html](https://man7.org/linux/man-pages/man5/crontab.5.html)                                 | Official crontab specification |
| [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)                                                   | Ubuntu Cron Guide              |
| [https://crontab.guru/](https://crontab.guru/)                                                                                               | Cron syntax validator          |
| [https://www.atlassian.com/engineering/devops/automate-with-cron-jobs](https://www.atlassian.com/engineering/devops/automate-with-cron-jobs) | Cron in DevOps                 |

---
