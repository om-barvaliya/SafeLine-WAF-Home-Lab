# Kali Linux Setup (Attacker Machine)

This document outlines the setup process for the **attacker machine** using **Kali Linux** in a virtualized environment.

---

## 🧰 Requirements

- [Kali Linux ISO](https://www.kali.org/get-kali/)
- VirtualBox or VMware
- Minimum Specs:
  - 2 GB RAM
  - 2 CPU cores
  - 20 GB disk space

---

## 🔧 Setup Steps

### 1. Create a New Virtual Machine

- Open **VirtualBox**
- Click **New** → Name: `Kali Attacker`
- Type: `Linux`, Version: `Debian (64-bit)`
- Assign:
  - Memory: `2048 MB`
  - Processors: `2`
- Create a virtual hard disk (20 GB minimum)

---

### 2. Attach Kali ISO

- Go to **Settings → Storage**
- Mount the Kali ISO under the **Empty** optical drive

---

### 3. Network Configuration

- **Adapter 1**: Set to **Bridged Adapter** or **NAT with Port Forwarding**
  - This allows communication with the target Ubuntu machine

---

### 4. Boot and Install Kali

- Start the VM
- Choose **Graphical Install**
- Follow standard steps (Language, Location, Keyboard)
- Set:
  - Username: `kali`
  - Password: `your_password`
- Partition disk → Use entire disk → All files in one partition
- Install GRUB → Yes → Continue

---

### 5. Post-Install Updates

```bash
sudo apt update && sudo apt upgrade -y
