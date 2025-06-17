# 🔐 Authentication Protection Test (DVWA)

## 📌 Objective

To test Safeline WAF's response to repeated failed login attempts (basic brute-force) on the DVWA login page.

## 🖥️ Environment

- **Target Machine**: Ubuntu VM with DVWA + Safeline WAF
- **Attacker Machine**: Kali Linux
- **Tool Used**: Manual login attempts via browser
- **WAF Feature**: Authentication Protection

## ⚙️ Configuration Steps

1. Enabled **Authentication Protection** in the Safeline web interface.
2. Logged in to DVWA at `http://<target-ip>/dvwa/login.php`.
3. Repeatedly tried logging in with incorrect credentials (admin/admin, root/root, etc.).
4. Attempted this from the same IP without clearing cookies to simulate persistent brute force.

## 🔍 Observations

- Safeline tracked the number of failed authentication attempts.
- After 5 consecutive failed logins, further attempts were blocked.
- The WAF issued a 403 Forbidden page and prevented access to the login page.

## 📸 Screenshots

- Safeline web interface showing Auth Protection enabled
- DVWA login page blocked after repeated failures

## ✅ Result

Safeline effectively identified and blocked brute-force authentication attempts based on login failure patterns. The block was enforced automatically without the need for external scripting.
