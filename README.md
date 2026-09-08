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




# 📝 **Step-by-Step Guide to Publish Your Project on GitHub**

Let's do this **one step at a time**. Follow each step carefully before moving to the next.

---

## Step 1: Create a GitHub Account (If You Don't Have One)

1. Open your web browser and go to **[github.com](https://github.com)**
2. Click the **"Sign up"** button in the top-right corner
3. Enter your:
   - Email address
   - Password
   - Username (e.g., `waqaskarim` or `cyberwaqas`)
4. Complete the verification puzzle
5. Click **"Create account"**
6. Check your email for a verification code and enter it
7. Click **"Continue"**

**✅ STOP HERE - Let me know when you've completed Step 1**

---

## Step 2: Create a New Repository

1. Make sure you're logged in to GitHub
2. Click the **"+"** icon in the top-right corner of the page (next to your profile picture)
3. From the dropdown menu, click **"New repository"**

Now you'll see a form. Fill it out like this:

4. **Repository name:** Type `cybersecurity-lab-setup`
5. **Description:** Type `VirtualBox and Kali Linux Cybersecurity Lab Setup for Penetration Testing`
6. **Public/Private:** Select **"Public"** (so employers can see it)
7. **Add a README file:** ❌ **LEAVE UNCHECKED** (we'll add our own)
8. **Add .gitignore:** Leave as **"None"**
9. **Choose a license:** Leave as **"None"**

10. Click the green **"Create repository"** button at the bottom

You'll now see a page with some commands and your empty repository.

**✅ STOP HERE - Let me know when you've completed Step 2**

---

## Step 3: Create Your README.md File on Your Computer

1. On your computer, open **Notepad** (Windows) or any text editor
2. Copy ALL of the text below and paste it into Notepad:

```markdown
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
```

### Step 6: Create a Clean VM Snapshot
Created snapshot named: `Clean Kali - Network Setup`

---

## ✅ Lab Verification

| Test | Command | Result |
|------|---------|--------|
| Check IP | `ip a` | ✅ 10.0.0.2/24 |
| Test Gateway | `ping 10.0.0.1` | ✅ Successful |
| Test Internet | `ping 8.8.8.8` | ✅ Successful |
| Test DNS | `ping google.com` | ✅ Successful |

**Example Output:**
```bash
$ ip a
inet 10.0.0.2/24 scope global eth0

$ ping -c 4 8.8.8.8
4 packets transmitted, 4 received, 0% packet loss
```

---

## 🐛 Problems Encountered & Solutions

### Problem 1: No Internet After Static IP
After configuring static IP, internet connectivity failed.

**Solution:**
```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

### Problem 2: Virtualization Error
VM failed to start because VT-x was disabled in BIOS.

**Solution:**
1. Restart computer
2. Enter BIOS/UEFI
3. Enable Intel VT-x
4. Save and restart

---

## 📚 What I Learned

1. **NAT vs NAT Network** - NAT Network allows multiple VMs to communicate
2. **VM Networking** - How virtual adapters connect to different networks
3. **Static IP Configuration** - Configuring IPv4 in Kali Linux
4. **VM Snapshots** - Creating recovery points before risky activities
5. **Documentation** - Importance of professional project documentation

---

## 🔒 Security & Ethical Use

This laboratory is intended strictly for **education purposes only**.

- ✅ Use only on systems you own or have permission to test
- ❌ Never attack unauthorized systems

---

## 🛠️ Tools & Resources

- [7-Zip](https://7-zip.org/download.html)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Kali Linux](https://kali.org/get-kali)

---

## 👨‍💻 Author

**Waqas Karim**  
Cybersecurity Professional

---

## 📅 Program Information

| **Program** | Cybersecurity at Networkwalks |
| **Week** | 01 |
| **Project** | Cybersecurity & Pentesting Lab Setup |
```

3. Click **File** → **Save As**
4. Navigate to where you want to save it (like your Desktop)
5. In the **"File name"** field, type exactly: `README.md`
6. In the **"Save as type"** dropdown, select **"All Files (*.*)"**
7. Click **Save**

**✅ STOP HERE - Let me know when you've completed Step 3**

---

## Step 4: Upload Your README.md to GitHub

1. Go back to your GitHub repository page (it should look like an empty folder)
2. You'll see a button that says **"Add file"** - Click it
3. From the dropdown, click **"Upload files"**

Now you'll see a box where you can drag and drop files.

4. Drag your `README.md` file from your Desktop (or wherever you saved it) into the box
   - OR click **"choose your files"** and select the file

5. You'll see the file appear with a green checkmark

6. Scroll down to the bottom of the page to the **"Commit changes"** section:
   - **"Commit message"** field: Type `Initial commit: Add lab setup documentation`
   - **"Description"** field (optional): Leave blank
   - Select **"Commit directly to the main branch"**

7. Click the green **"Commit changes"** button

**✅ STOP HERE - Let me know when you've completed Step 4**

---

## Step 5: Verify Your README Looks Good

1. Your repository page should now reload automatically
2. Scroll down - you should see your README content displayed beautifully
3. Check that:
   - Headings show correctly
   - Tables look organized
   - Code blocks have grey backgrounds
   - All text is readable

If something looks wrong, you can click the pencil icon (✏️) to edit it.

**✅ STOP HERE - Let me know when you've completed Step 5**

---

## Step 6: (Optional) Add Screenshots to Make It Better

If you want to add screenshots to make your README more visual:

1. On your repository page, click **"Add file"** → **"Upload files"**
2. Create a folder by typing `screenshots/` in the file upload box (this creates a folder)
3. Drag your screenshot images into the box
4. Add a commit message like `Add screenshots` and click **"Commit changes"**

To add images to your README, you can add lines like:

```markdown
![IP Configuration](screenshots/ip-config.png)
```

**✅ STOP HERE - Let me know when you've completed Step 6**

---

## Step 7: Create a GitHub Profile README (Optional - Makes You Look Professional)

1. Click the **"+"** icon in the top-right → **"New repository"**
2. Repository name: Type your username exactly (e.g., `waqaskarim`)
3. Description: Type `My GitHub Profile`
4. Make it **Public**
5. ✅ **Check** "Add a README file"
6. Click **"Create repository"**

Now you can add a professional profile README that shows up on your GitHub page.

**✅ STOP HERE - Let me know when you've completed Step 7**

---

## Step 8: Share on LinkedIn

1. Go to **[linkedin.com](https://linkedin.com)**
2. Click on the **"Start a post"** box
3. Copy and paste this (replace YOUR-USERNAME with your GitHub username):

```
🛡️ Just completed my Cybersecurity Lab Setup! 

I've set up a complete penetration testing environment using VirtualBox and Kali Linux on a private NAT Network (10.0.0.0/24). This lab will be used for network reconnaissance, vulnerability assessment, and security testing.

✅ Kali Linux configured with static IP (10.0.0.2/24)
✅ Full internet access and DNS resolution
✅ Clean VM snapshot created for recovery
✅ Comprehensive documentation

Check out the full setup on GitHub:
https://github.com/YOUR-USERNAME/cybersecurity-lab-setup

#Cybersecurity #KaliLinux #PenetrationTesting #VirtualBox #EthicalHacking #InfoSec #Networkwalks #CybersecurityInternship
```

4. Click **Post**

**✅ STOP HERE - You're done!**

---

## 🎯 **Quick Summary Checklist**

| Step | Task | Done? |
|------|------|-------|
| 1 | Created GitHub account | ⬜ |
| 2 | Created repository | ⬜ |
| 3 | Created README.md file | ⬜ |
| 4 | Uploaded README to GitHub | ⬜ |
| 5 | Verified README looks good | ⬜ |
| 6 | Added screenshots (optional) | ⬜ |
| 7 | Created profile README (optional) | ⬜ |
| 8 | Shared on LinkedIn | ⬜ |

