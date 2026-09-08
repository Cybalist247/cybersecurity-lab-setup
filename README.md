```markdown
# 🛡️ Cybersecurity & Penetration Testing Lab Setup

> **A VirtualBox-based cybersecurity laboratory for ethical hacking, penetration testing, and security research.**

![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kali-linux&logoColor=white)
![VirtualBox](https://img.shields.io/badge/VirtualBox-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)

---

## 📋 Project Overview

This project focuses on setting up a **virtual cybersecurity and penetration-testing laboratory** using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

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
- Prepare the environment for future cybersecurity projects

---

## 🧪 Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

### Activities Include:
- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

> ⚠️ **Important:** This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

---

## 🏗️ Lab Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      HOST MACHINE                          │
│                   (Windows 10 / 8GB RAM)                   │
│                                                           │
│  ┌─────────────────────────────────────────────────────┐   │
│  │              VirtualBox 7.2                        │   │
│  │                                                   │   │
│  │  ┌─────────────────────────────────────────────┐  │   │
│  │  │           NAT Network: 10.0.0.0/24         │  │   │
│  │  │                                             │  │   │
│  │  │  ┌─────────────┐    ┌─────────────────┐   │  │   │
│  │  │  │ Kali Linux  │    │  Future VMs     │   │  │   │
│  │  │  │ 10.0.0.2/24 │◄──►│ 10.0.0.3-99     │   │  │   │
│  │  │  │ (Attacker)  │    │ (Targets)       │   │  │   │
│  │  │  └─────────────┘    └─────────────────┘   │  │   │
│  │  └─────────────────────────────────────────────┘  │   │
│  └─────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

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
| **Future VM Range** | 10.0.0.3–10.0.0.99 |

---

## 📝 Lab Setup Procedure

### Step 1: Install 7-Zip
7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `7z` archive.

**Tool:** [7-Zip](https://7-zip.org/download.html)

### Step 2: Install VirtualBox
VirtualBox was installed as the hypervisor.

**Tool:** [VirtualBox](https://virtualbox.org/wiki/Downloads)

### Step 3: Create the NAT Network
A dedicated NAT Network was created in VirtualBox.

**Configuration:**
- Network Name: `NatNetwork`
- IPv4 Prefix: `10.0.0.0/24`
- DHCP: **Disabled** (for static IP)
- IPv6: Disabled

> **Why NAT Network?** A NAT Network allows multiple virtual machines connected to the same network to communicate with one another while also having outbound network connectivity. This will allow future attacker and target VMs to communicate within the lab.

### Step 4: Import Kali Linux
The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

**VM Configuration:**
- **RAM:** 2048 MB
- **Adapter 1:** NAT Network → `NatNetwork`
- **Adapter Type:** Intel PRO/1000 MT Desktop
- **Shared Folder:** `/downloads` (from host)

### Step 5: Configure Kali Linux Network
The Kali Linux network configuration was configured with a consistent IPv4 address:

```bash
IP Address:  10.0.0.2/24
Gateway:     10.0.0.1
DNS:         8.8.8.8
```

**Commands used:**
```bash
sudo nmcli connection modify "Wired connection 1" ipv4.addresses 10.0.0.2/24
sudo nmcli connection modify "Wired connection 1" ipv4.gateway 10.0.0.1
sudo nmcli connection modify "Wired connection 1" ipv4.dns 8.8.8.8
sudo nmcli connection modify "Wired connection 1" ipv4.method manual
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

### Step 6: Create a Clean VM Snapshot
After completing the initial configuration, a VirtualBox snapshot was created:

**Snapshot Name:** `Clean Kali - Network Setup`

> The snapshot represents the clean baseline of the laboratory. If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

---

## ✅ Lab Verification

| Test | Command | Expected Result | Status |
|------|---------|-----------------|--------|
| Check IP address | `ip a` | 10.0.0.2/24 displayed | ✅ |
| Test gateway | `ping 10.0.0.1` | Successful replies | ✅ |
| Test Internet | `ping 8.8.8.8` | Successful replies | ✅ |
| Test DNS | `ping google.com` | Domain resolves | ✅ |
| Verify Nmap | `nmap --version` | Nmap version displayed | ✅ |

**Example Results:**
```bash
$ ip a
inet 10.0.0.2/24 scope global eth0

$ ping -c 4 8.8.8.8
64 bytes from 8.8.8.8: icmp_seq=1 ttl=64 time=40.3 ms
4 packets transmitted, 4 received, 0% packet loss

$ ping -c 4 google.com
64 bytes from lcmada-aa-in-f14.1e100.net: icmp_seq=1 ttl=64 time=139 ms
4 packets transmitted, 4 received, 0% packet loss
```

---

## 🐛 Problems Encountered & Solutions

### Problem 1: Internet Connectivity After Static IP Configuration
After manually configuring the IPv4 settings, Internet connectivity failed.

**Solution:**
```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

> **Note:** Network interface and connection names may differ between systems. Identify your actual connection name using `nmcli connection show`.

### Problem 2: VirtualBox VT-x / Virtualization Error
The VM initially failed to start because hardware virtualization was disabled in the BIOS.

**Solution:**
1. Restart the computer
2. Enter BIOS/UEFI settings
3. Enable Intel VT-x / hardware virtualization
4. Save and restart
5. Start the Kali VM

---

## 📚 What I Learned

### 1. NAT vs NAT Network
A standard NAT configuration and a NAT Network serve different purposes. A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

### 2. Virtual Machine Networking
I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

### 3. Static IP Configuration
I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

### 4. VM Snapshots
I learned that a clean snapshot should be created before performing risky or experimental activities.

### 5. Documentation
I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

---

## 🔒 Security & Ethical Use

This laboratory is intended strictly for **education purposes only**.

- ✅ Use only on systems you own or have explicit permission to test
- ✅ Follow all applicable laws and regulations
- ✅ Practice responsible disclosure
- ❌ Never attack unauthorized systems

---

## 🛠️ Tools & Resources

- **[7-Zip](https://7-zip.org/download.html)** - Archive extraction
- **[VirtualBox](https://www.virtualbox.org/wiki/Downloads)** - Hypervisor
- **[Kali Linux](https://kali.org/get-kali)** - Security OS
- **[Nmap](https://nmap.org/)** - Network scanning

---

## 📂 Project Structure

```
cybersecurity-lab-setup/
├── README.md                 # Main documentation
├── screenshots/              # Lab setup screenshots
│   ├── virtualbox-network.png
│   ├── kali-ip-config.png
│   └── ping-test.png
└── configs/                  # Configuration files
    └── interfaces-sample.txt # Network config reference
```

---

## 👨‍💻 Author

**Waqas Karim**  
Cybersecurity Professional  
[LinkedIn](https://www.linkedin.com/in/waqaskarim/) | [GitHub](https://github.com/yourusername)

---

## 📅 Program Information

| **Program** | Cybersecurity at Networkwalks |
| **Week** | 01 |
| **Project** | Cybersecurity & Pentesting Lab Setup |
| **Repository** | [GitHub](https://github.com/yourusername/cybersecurity-lab-setup) |

---

## 📜 License

This project is for educational purposes only. Please use responsibly.

---

⭐ **If you found this useful, please give it a star!** ⭐
```

---

### File 2: `screenshots/` Folder (Optional but Recommended)

Create a folder called `screenshots` and add images like:
- `virtualbox-network.png` - Screenshot of NAT Network configuration
- `kali-ip-config.png` - Screenshot showing `ip a` output with 10.0.0.2
- `ping-test.png` - Screenshot of successful ping tests
- `snapshot.png` - Screenshot showing the snapshot creation

---

## Step 3: Upload to GitHub

### Option A: Using Git Commands (Recommended)

```bash
# Navigate to your project folder
cd cybersecurity-lab-setup

# Initialize git
git init

# Add all files
git add .

# Commit the files
git commit -m "Initial commit: Cybersecurity Lab Setup with Kali Linux"

# Add remote repository (replace YOUR-USERNAME and REPO-NAME)
git remote add origin https://github.com/YOUR-USERNAME/cybersecurity-lab-setup.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Option B: Using GitHub Web Interface

1. Go to your repository on GitHub.
2. Click **"Add file"** → **"Upload files"**.
3. Drag and drop your `README.md` file.
4. Add a commit message and click **"Commit changes"**.

---

## Step 4: Add Screenshots (Optional)

To add images to your README:

1. Upload screenshots to the `screenshots/` folder.
2. In your README, reference them like this:

```markdown
![NAT Network Configuration](screenshots/virtualbox-network.png)
```

---

## Step 5: Add Badges (Optional)

Add these to the top of your README for a professional look:

```markdown
![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kali-linux&logoColor=white)
![VirtualBox](https://img.shields.io/badge/VirtualBox-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)
```

---

## Step 6: Share on LinkedIn (Portfolio)

Post on LinkedIn with something like:

> 🛡️ **Just completed my Cybersecurity Lab Setup!** 
>
> I've set up a complete penetration testing environment using VirtualBox and Kali Linux on a private NAT Network (10.0.0.0/24). This lab will be used for network reconnaissance, vulnerability assessment, and security testing during my Cybersecurity Internship at Networkwalks.
>
> Key achievements:
> - ✅ Kali Linux configured with static IP (10.0.0.2/24)
> - ✅ Full internet access and DNS resolution
> - ✅ Clean VM snapshot created for recovery
> - ✅ Comprehensive documentation
>
> Check out the full setup on GitHub: [Link to your repo]
>
> #Cybersecurity #KaliLinux #PenetrationTesting #VirtualBox #EthicalHacking #InfoSec #Networkwalks

---

## Summary Checklist

| Task | Status |
|------|--------|
| Create GitHub repository | ⬜ |
| Create README.md with all content | ⬜ |
| Add screenshots folder | ⬜ |
| Upload files to GitHub | ⬜ |
| Test README formatting | ⬜ |
| Share on LinkedIn/Portfolio | ⬜ |

---

**You've done amazing work!** This documentation is portfolio-ready and will impress anyone who sees it. 🎯
