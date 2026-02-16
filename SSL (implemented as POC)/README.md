# Implementation of SSL Certificate Using Let's Encrypt and Nginx

---

| Author           | Created    | Version | Last updated by  | Last Edited On | L0 Reviewer | L1 Reviewer | L2 Reviewer |
| ---------------- | ---------- | ------- | ---------------- | -------------- | ----------- | ----------- | ----------- |
| Abhinav Sikarwar | 2026-02-16 | 1.0     | Abhinav Sikarwar | 2026-02-16     |Aayush Verma |Shreya Jaiswal|Ashwani     |

---

# Table of Contents

1. Introduction
2. Objective
3. Prerequisites
4. Architecture (High Level)
5. Infrastructure Setup (EC2 / VM)
6. Step-by-Step Implementation

   * Step 1: Update System Packages
   * Step 2: Install Nginx
   * Step 3: Verify Domain DNS Resolution
   * Step 4: Install Certbot
   * Step 5: Generate and Install SSL Certificate
   * Step 6: Verify Nginx SSL Configuration
   * Step 7: Test SSL Auto Renewal
7. Validation & Verification

   * SSL Verification using Browser
   * SSL Verification using Command Line
8. SSL Certificate File Location
9. Security and Best Practices
10. Contact Information
11. References

---

# 1. Introduction

This document describes the **standard operating procedure (SOP)** to implement an **SSL certificate using Let's Encrypt and Certbot** on an Ubuntu server running Nginx.

SSL ensures secure communication between client and server by encrypting transmitted data and enabling HTTPS protocol.

This implementation follows industry best practices and provides automated certificate renewal.

---

# 2. Objective

The objective of this implementation is to:

* Secure a domain using HTTPS protocol
* Install and configure SSL certificate using Let’s Encrypt
* Enable encrypted communication between client and server
* Configure automatic SSL certificate renewal
* Ensure secure and production-ready web server configuration

---

# 3. Prerequisites

Ensure the following prerequisites are met before implementation:

* Ubuntu Server (20.04 or 22.04 recommended)
* Domain name configured (example: `example.com`)
* Domain DNS A record pointing to server public IP
* Public IP assigned to server
* Sudo access on server
* Ports 80 and 443 open in firewall/security group
* Nginx installed and configured

---

# 4. Architecture (High Level)

```
User Browser
     │
     │ HTTPS Request (Port 443)
     ▼
Domain (example.com)
     │
     ▼
Public IP → Ubuntu Server
     │
     ▼
Nginx Web Server
     │
     ▼
SSL Certificate (Let’s Encrypt)
     │
     ▼
Secure Encrypted Response
```

---

# 5. Infrastructure Setup (EC2 / VM)

Launch an Ubuntu EC2 instance or VM with:

* Ubuntu 22.04
* Open ports:

  * 22 (SSH)
  * 80 (HTTP)
  * 443 (HTTPS)

Connect to server:

```bash
ssh ubuntu@your-server-ip
```

---

# 6. Step-by-Step Implementation

---

## Step 1: Update System Packages

Update system package repository:

```bash
sudo apt update
sudo apt upgrade -y
```

---

## Step 2: Install Nginx

Install nginx web server:

```bash
sudo apt install nginx -y
```

Enable and start nginx:

```bash
sudo systemctl enable nginx
sudo systemctl start nginx
```

Verify status:

```bash
sudo systemctl status nginx
```

---

## Step 3: Verify Domain DNS Resolution

Verify domain points to server:

```bash
nslookup example.com
```

Expected output:

```
example.com → YOUR_SERVER_PUBLIC_IP
```

If DNS is incorrect, SSL certificate generation will fail.

---

## Step 4: Install Certbot

Install certbot and nginx plugin:

```bash
sudo apt install certbot python3-certbot-nginx -y
```

Verify installation:

```bash
certbot --version
```

---

## Step 5: Generate and Install SSL Certificate

Run certbot command:

```bash
sudo certbot --nginx -d example.com -d www.example.com
```

Provide the following inputs when prompted:

* Enter email address
* Accept Terms and Conditions → Yes
* Redirect HTTP to HTTPS → Select Redirect option

Certbot automatically performs:

* Domain validation
* SSL certificate generation
* Nginx SSL configuration
* HTTP to HTTPS redirection
* Automatic renewal configuration

---

## Step 6: Verify Nginx SSL Configuration

Test nginx configuration:

```bash
sudo nginx -t
```

Reload nginx:

```bash
sudo systemctl reload nginx
```

---

## Step 7: Test SSL Auto Renewal

Test auto renewal process:

```bash
sudo certbot renew --dry-run
```

Successful output confirms auto-renewal is working correctly.

---

# 7. Validation & Verification

---

## 7.1 SSL Verification using Browser

Open the domain in browser:

```
https://example.com
```

Expected result:

* HTTPS enabled
* Lock icon visible
* Secure connection established

---

## 7.2 SSL Verification using Command Line

Verify SSL certificate:

```bash
sudo certbot certificates
```

Verify SSL connection:

```bash
openssl s_client -connect example.com:443
```

---

# 8. SSL Certificate File Location

SSL certificate files are stored at:

```bash
/etc/letsencrypt/live/example.com/
```

Important files:

| File          | Description     |
| ------------- | --------------- |
| fullchain.pem | SSL Certificate |
| privkey.pem   | Private key     |

---

# 9. Security and Best Practices

Recommended best practices:

* Always redirect HTTP to HTTPS
* Enable firewall ports 80 and 443 only
* Keep certbot updated
* Monitor certificate expiration
* Use automated renewal

Check renewal timer:

```bash
systemctl status certbot.timer
```

---

# 10. Contact Information

| Name             | Team   | Contact Type | Details                                                             |
| ---------------- | ------ | ------------ | ------------------------------------------------------------------- |
| Abhinav Sikarwar | DevOps | Email        | [abhinav.sikarwar@example.com](mailto:abhinav.sikarwar@example.com) |

---

# 11. References

| Description                          | Link                                                           |
| ------------------------------------ | -------------------------------------------------------------- |
| Let's Encrypt Official Documentation | [https://letsencrypt.org/docs/](https://letsencrypt.org/docs/) |
| Certbot Documentation                | [https://certbot.eff.org/docs/](https://certbot.eff.org/docs/) |

---
