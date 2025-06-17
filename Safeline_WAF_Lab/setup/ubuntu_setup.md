# Ubuntu Server Setup (Target + WAF Machine)

This document details the setup for the **target server machine** running Ubuntu and protected by **Safeline WAF**.

---

## 🧰 Requirements

- [Ubuntu ISO](https://ubuntu.com/download/server)
- VirtualBox or VMware
- Minimum Specs:
  - 2 GB RAM
  - 2 CPU cores
  - 30 GB disk space (for web server + WAF)

---

## 🔧 Setup Steps

### 1. Create a New Virtual Machine

- Name: `Ubuntu Target`
- Type: `Linux`, Version: `Ubuntu (64-bit)`
- Assign:
  - Memory: `2048 MB`
  - Processors: `2`
  - Disk: `30 GB`

---

### 2. Attach Ubuntu ISO

- Settings → Storage → Mount the Ubuntu ISO

---

### 3. Network Configuration

- Adapter 1: **Bridged Adapter** (or NAT + Port Forwarding)

---

### 4. Install Ubuntu

- Standard server install:
  - Set hostname, username, and password
- Install **OpenSSH** (important for remote access)
- Skip optional services like Kubernetes for now

---

### 5. Update System

```bash
sudo apt update && sudo apt upgrade -y
