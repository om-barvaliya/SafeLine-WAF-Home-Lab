# SQL Injection Test

This document explains the process of manually testing **SQL Injection (SQLi)** attacks on a vulnerable application (DVWA) and analyzing the protection and detection provided by the Safeline Web Application Firewall (WAF).

## 📌 Objective

To verify whether **Safeline WAF** is capable of identifying and blocking SQL injection attempts made to a vulnerable target web application.

---

## 🧪 Environment Setup

- **Target Machine (Ubuntu)**:
  - OS: Ubuntu 20.04
  - Web Application: [DVWA](http://www.dvwa.co.uk/)
  - Apache, MySQL, PHP configured
  - Safeline WAF deployed and reverse proxying DVWA

- **Attacker Machine (Kali Linux)**:
  - Tools used: Web browser (Firefox), Burp Suite (Community Edition)
  - Manual attack techniques via DVWA forms and Burp interception

---

## 🔍 Testing Procedure

### Step 1: Prepare DVWA

1. Login to DVWA with default credentials.
2. Set DVWA **Security Level** to **Low**.
3. Navigate to the **SQL Injection** module.

### Step 2: Manual SQL Injection Attempts

Examples of payloads tested:

- `' OR '1'='1`
- `admin'--`
- `admin' #`
- `' OR 1=1 -- -`
- `1' UNION SELECT null, version()--`

Executed via:

- **DVWA input forms**
- **Burp Suite's HTTP Request Editor (Repeater)**
  
### Step 3: Observe Server Behavior

- Monitored response pages to identify if:
  - SQL injection succeeded (e.g., bypassed login, dumped DB info)
  - WAF intercepted or blocked the request
  - WAF triggered any alerts or error responses

---

## 🧰 Safeline WAF Configuration

- Deployed as a reverse proxy in front of DVWA (Nginx)
- Logged all detected attacks via `/var/log/safeline/` and Dashboard

---

## ✅ Results

| Attempted Payload              | WAF Detection | Response      |
|-------------------------------|---------------|----------------|
| `' OR '1'='1`                  | ✅ Blocked     | HTTP 403 Error |
| `admin'--`                    | ✅ Blocked     | HTTP 403 Error |
| `' OR 1=1 --`                 | ✅ Blocked     | HTTP 403 Error |
| `1' UNION SELECT null,...`   | ✅ Blocked     | HTTP 403 Error |
| Random SQL keywords in input | ✅ Blocked     | HTTP 403 Error |

- All high-risk payloads were blocked by Safeline.
- Requests intercepted and modified using Burp were still detected.

---

## 📸 Screenshots

- DVWA SQL Injection page
- Burp Suite Intercepted SQLi payload
- Safeline WAF logs showing detection
- HTTP 403 error page returned

---

## 📝 Conclusion

The Safeline WAF successfully detected and blocked all tested SQL injection payloads, demonstrating effective protection against manual SQLi attacks. Even basic SQLi attempts were intercepted when passed through Burp Suite. Safeline's default SQLi module provided adequate coverage during this test.

---
