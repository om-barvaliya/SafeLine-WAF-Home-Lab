# Safeline WAF Lab

Safeline is an open-source Web Application Firewall (WAF) developed by Chaitin Technology, designed to detect and prevent common web application attacks. This repository contains a complete lab setup, testing scenarios, and analysis performed using Safeline in a virtualized testbed.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
---

## 🚀 Overview

The goal of this project is to simulate real-world web attacks in a controlled environment and evaluate how effectively Safeline WAF mitigates these threats. The lab environment includes:

- A **host machine** running **Ubuntu** with a target web server.
- An **attacker machine** using **Kali Linux** to launch various attacks.
- **Safeline WAF** running as a protective layer in front of the target server.

---
### 🖼️ How Safeline WAF Works

![Safeline Architecture Diagram](/screenshots/Safeline.jpg)

> 📷 *Source: [The Hacker News – May 2025](https://thehackernews.com/2025/05/safeline-waf-open-source-web.html)*  
> 🧠 *Image credit to Chaitin Tech – creators of Safeline WAF*

---

## 🏗️ Lab Setup

The lab is built using **VirtualBox** with two VMs:

- **Target Machine:** Ubuntu 22.04 LTS (Apache2 web server)
- **Attacker Machine:** Kali Linux (Burp Suite, custom scripts, etc.)
- **WAF Layer:** Safeline running directly on Ubuntu or via Docker (optional)

> 📄 Setup instructions can be found [`here`](setup/)

---

## 🔒 WAF Testing Methodology

Multiple attack simulations were performed against the protected server to observe Safeline’s behavior and logging features.

### ✅ Attacks Covered:

1. **HTTP Flood**
   - Tool: Custom Python scripts
   - Result: Safeline detected and rate-limited the requests

2. **Authentication Bypass**
   - Tool: Crafted payloads via Burp Suite
   - Result: Logged and blocked malicious requests

3. **Cross-Site Scripting (XSS)**
   - Manual input and automated payloads
   - Result: Reflected XSS detected and neutralized

> 📄 See [`test_cases`](test_cases) for details and logs.

---

### Burp Suite in Action

Some key screenshots from Burp Suite during attack simulation:

- **Payload Analysis**
  
  ![Payloads Used](/screenshots/BurpSuite_payloads.png)

- **Logger Tab**
  
  ![Logger Tab](/screenshots/BurpSuite_logger.jpg)

- **Repeater Testing**
  
  ![Repeater Tab](/screenshots/BurpSuite_repeater.png)


> 📄 Sample screenshots and requests are [`here`](screenshots)

---

## 📸 Screenshots

All screenshots of environment, attacks, and logs are saved [`here`](screenshots).

Examples:
- Ubuntu and Kali setup
- Safeline startup terminal logs
- Attack detection logs from Safeline
- Burp Suite request/response

### WAF Console Log Example

Safeline logging a blocked SQL Injection attempt:

![Safeline SQL Detection](/screenshots/Safeline_SQL_detected.png)

---

## 📌 Requirements

- VirtualBox or VMware
- Kali Linux ISO
- Ubuntu ISO
- Python 3.x
- Burp Suite Community Edition
- Safeline Installation Script

---

## ⚖️ License

This project is under the MIT License. See [`LICENSE`](LICENSE.md) for details.

---
