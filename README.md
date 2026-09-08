# 🛡️ Cybersecurity & Penetration Testing Lab Setup

> **A VirtualBox-based cybersecurity laboratory for ethical hacking, penetration testing, and security research.**

---

## 📋 Project Overview

This project focuses on setting up a **virtual cybersecurity and penetration-testing laboratory** using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

---

## 🎯 Objectives

- Install and configure VirtualBox
- Install/import Kali Linux as a virtual machine
- Create a private NAT Network for the cybersecurity lab
- Configure network connectivity for Kali Linux
- Assign a consistent IP address to the Kali VM
- Verify network connectivity and DNS resolution
- Take a clean VM snapshot for recovery
- Document the complete setup process

---

## ⚙️ Lab Configuration

| Component | Configuration |
|-----------|---------------|
| **Host OS** | Windows 10 |
| **Host RAM** | 8 GB |
| **Processor** | Intel Core i7 |
| **Hypervisor** | VirtualBox 7.2 |
| **Security OS** | Kali Linux 2026.2 |
| **Kali RAM** | 2048 MB |
| **Virtual Network** | NAT Network |
| **Network Address** | 10.0.0.0/24 |
| **Kali IP Address** | 10.0.0.2/24 |
| **Default Gateway** | 10.0.0.1 |
| **DNS Server** | 8.8.8.8 |

---

## 📝 Lab Setup Procedure

### Step 1: Install 7-Zip
Installed to extract the Kali Linux virtual-machine package.

**Tool:** [7-Zip](https://7-zip.org/download.html)

### Step 2: Install VirtualBox
Installed as the hypervisor.

**Tool:** [VirtualBox](https://virtualbox.org/wiki/Downloads)

### Step 3: Create the NAT Network
Created a dedicated NAT Network in VirtualBox.

**Configuration:**
- Network Name: `NatNetwork`
- IPv4 Prefix: `10.0.0.0/24`
- DHCP: Disabled
- IPv6: Disabled

### Step 4: Import Kali Linux
Downloaded and imported Kali Linux into VirtualBox.

**VM Configuration:**
- **RAM:** 2048 MB
- **Adapter:** NAT Network → `NatNetwork`
- **Shared Folder:** `/downloads`

### Step 5: Configure Kali Linux Network
Configured static IP address:

```bash
IP Address:  10.0.0.2/24
Gateway:     10.0.0.1
DNS:         8.8.8.8