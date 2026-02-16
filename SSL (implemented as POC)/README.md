# Implementation of SSL Certificate Using Let's Encrypt and Nginx

---

| Author           | Created    | Version | Last updated by  | Last Edited On | L0 Reviewer  | L1 Reviewer    | L2 Reviewer |
| ---------------- | ---------- | ------- | ---------------- | -------------- | ------------ | -------------- | ----------- |
| Abhinav Sikarwar | 2026-02-16 | 1.0     | Abhinav Sikarwar | 2026-02-16     | Aayush Verma | Shreya Jaiswal | Ashwani     |

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Objective](#2-objective)
3. [Prerequisites](#3-prerequisites)
4. [Architecture (High Level)](#4-architecture-high-level)
5. [Infrastructure Setup (EC2 / VM)](#5-infrastructure-setup-ec2--vm)
6. [Step-by-Step Implementation](#6-step-by-step-implementation)
7. [Validation & Verification](#7-validation--verification)
8. [SSL Certificate File Location](#8-ssl-certificate-file-location)
9. [Security and Best Practices](#9-security-and-best-practices)
10. [Contact Information](#10-contact-information)
11. [References](#11-references)

---

## 1. Introduction

This document describes the **Standard Operating Procedure (SOP)** to implement an **SSL certificate using Let's Encrypt and Certbot** on an Ubuntu server running Nginx.

SSL (Secure Sockets Layer) ensures encrypted communication between client and server by securing transmitted data and enabling HTTPS protocol.

This implementation follows industry best practices and provides automatic certificate renewal.

---

## 2. Objective

The objective of this implementation is to:

* Secure a domain using HTTPS protocol
* Install and configure SSL certificate using Let’s Encrypt
* Enable encrypted communication between client and server
* Configure automatic SSL certificate renewal
* Ensure secure and production-ready web server configuration

---

## 3. Prerequisites

Ensure the following prerequisites are met before implementation:

* Ubuntu Server (20.04 or 22.04 recommended)
* Domain name configured (example: `example.com`)
* DNS A record pointing domain to server public IP
* Public IP assigned to server
* Sudo privileges on server
* Ports 80 (HTTP) and 443 (HTTPS) open in firewall/security group
* Nginx installed and accessible via domain

---

## 4. Architecture (High Level)

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
SSL Certificate (Let's Encrypt)
     │
     ▼
Encrypted Secure Response
```

---

## 5. Infrastructure Setup (EC2 / VM)

Launch an Ubuntu EC2 instance or Virtual Machine with the following configuration:

* OS: Ubuntu 22.04 LTS
* Open ports:

  * 22 (SSH)
  * 80 (HTTP)
  * 443 (HTTPS)

Connect to the server using SSH:

```bash
ssh ubuntu@your-server-ip
```

---

## 6. Step-by-Step Implementation

### Update System Packages

Update package repository and system packages:

```bash
sudo apt update
sudo apt upgrade -y
```

---

### Install Nginx Web Server

Install nginx:

```bash
sudo apt install nginx -y
```

Enable and start nginx service:

```bash
sudo systemctl enable nginx
sudo systemctl start nginx
```

Verify nginx status:

```bash
sudo systemctl status nginx
```

---

### Verify Domain DNS Resolution

Verify domain points to server public IP:

```bash
nslookup example.com
```

Expected output:

```
example.com → YOUR_SERVER_PUBLIC_IP
```

SSL generation will fail if DNS is not configured correctly.

---

### Install Certbot

Install certbot and nginx plugin:

```bash
sudo apt install certbot python3-certbot-nginx -y
```

Verify installation:

```bash
certbot --version
```

---

### Generate and Install SSL Certificate

Run certbot command:

```bash
sudo certbot --nginx -d example.com -d www.example.com
```

Provide required inputs:

* Enter email address
* Accept Terms and Conditions → Yes
* Select Redirect HTTP to HTTPS

Certbot will automatically:

* Verify domain ownership
* Generate SSL certificate
* Configure nginx for SSL
* Enable HTTPS redirect
* Configure automatic renewal

---

### Verify Nginx Configuration

Test nginx configuration:

```bash
sudo nginx -t
```

Reload nginx:

```bash
sudo systemctl reload nginx
```

---

### Test SSL Auto Renewal

Verify certificate auto-renewal:

```bash
sudo certbot renew --dry-run
```

Successful execution confirms renewal is configured properly.

---

## 7. Validation & Verification

### Browser Verification

Open domain in browser:

```
https://example.com
```

Expected result:

* HTTPS enabled
* Lock icon visible
* Secure encrypted connection

---

### Command Line Verification

Check installed certificates:

```bash
sudo certbot certificates
```

Verify SSL connection:

```bash
openssl s_client -connect example.com:443
```

---

## 8. SSL Certificate File Location

SSL certificates are stored at:

```bash
/etc/letsencrypt/live/example.com/
```

Important files:

| File          | Description     |
| ------------- | --------------- |
| fullchain.pem | SSL Certificate |
| privkey.pem   | Private Key     |

---

## 9. Security and Best Practices

Recommended best practices:

* Always enforce HTTPS redirection
* Keep ports 80 and 443 open only as required
* Regularly update system packages
* Ensure automatic certificate renewal is active
* Monitor certificate expiration

Check certbot renewal service:

```bash
systemctl status certbot.timer
```

---

## 10. Contact Information

| Name             | Team   | Contact Type | Details                                                             |
| ---------------- | ------ | ------------ | ------------------------------------------------------------------- |
| Abhinav Sikarwar | Saarthi| Email        | [abhinav.sikarwar@mygurukulam.co](mailto:abhinav.sikarwar@mygurukulam.co) |

---

## 11. References

| Description                          | Link                                                                                                                           |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Let's Encrypt Official Documentation | [Let's Try Doc](https://letsencrypt.org/docs/)                                                                 |
| Certbot Official Documentation       | [Certbot Doc](https://certbot.eff.org/docs/)                                                                 |
| SSL POC Implementation Reference     | [SSL POC README](https://github.com/Snaatak-Saarthi/Saarthi_Sprint1/blob/SCRUM-76-suraj/Domain_And_Security/SSL/POC/README.md) |

---
