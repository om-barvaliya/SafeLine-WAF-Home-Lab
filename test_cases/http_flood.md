# 🧪 HTTP Flood Test

## 📌 Objective

To evaluate how Safeline WAF responds to high-volume HTTP request attacks (HTTP Flood) on a DVWA-hosted target server.

## 🖥️ Environment

- **Target Machine**: Ubuntu VM running DVWA and Safeline WAF
- **Attacker Machine**: Kali Linux
- **Tool Used**: Browser + Repetitive manual refresh (simulating flood)
- **WAF Mode**: HTTP Flood Protection enabled

## ⚙️ Configuration Steps

1. DVWA was set to **Low security** in `config/security.php` for better visibility of behavior.
2. Safeline WAF was started in the default configuration with `HTTP Flood Protection` enabled.
3. Targeted endpoint: `http://<target-ip>/dvwa/index.php`
4. Repeatedly refreshed the browser to simulate multiple HTTP requests within a short time frame.

## 🔍 Observations

- After crossing a threshold (10–20 requests within a few seconds), Safeline detected the behavior.
- It issued a **403 Forbidden** response, effectively blocking further access.
- The Safeline log file recorded details of the flood attempt with IP and timestamp.

## 📸 Screenshots

- Safeline Logs
  ![http flood blocking](/screenshots/Safeline_httpFlood.jpg)
  
- Browser showing 403 Block Page
  ![http flood blocking](/screenshots/access_forbidden2_htmlFlood.png)


## ✅ Result

Safeline WAF successfully detected and blocked HTTP Flood activity without requiring any external tools or scripts. This confirms its effectiveness against basic DoS-style web attacks.
