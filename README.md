<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**A controlled virtual lab for cybersecurity learning, ethical hacking and authorized penetration testing practice.**

![Host](https://img.shields.io/badge/Host-Windows%2011-0078D4?style=for-the-badge&logo=windows11&logoColor=white)
![Hypervisor](https://img.shields.io/badge/VirtualBox-7.1.4-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)
![Kali](https://img.shields.io/badge/Kali%20Linux-2023.2-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)
![Network](https://img.shields.io/badge/NAT%20Network-10.0.0.0%2F24-2E8B57?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

<img width="1918" height="948" alt="03-kali-desktop" src="https://github.com/user-attachments/assets/0230a37b-ab3f-465c-b686-5cce69748500" />


</div>

---

## 📑 Table of Contents

- [Project Overview](#-project-overview)
- [Objectives](#-objectives)
- [Lab Architecture](#%EF%B8%8F-lab-architecture)
- [Lab Configuration](#%EF%B8%8F-lab-configuration)
- [Setup Procedure](#-setup-procedure)
- [Lab Verification](#-lab-verification)
- [Troubleshooting](#-troubleshooting)
- [What I Learned](#-what-i-learned)
- [Security & Ethical Use](#-security--ethical-use)
- [Tools & Resources](#-tools--resources)
- [Author](#-author)

---

## 📌 Project Overview

This project documents how I built a beginner-friendly cybersecurity lab using **Oracle VirtualBox** and **Kali Linux** on a **Windows 11** host.

The lab gives me a safe, controlled place to learn security fundamentals, practice authorized testing, and build hands-on portfolio projects. The setup includes:

- 🌐 A dedicated VirtualBox **NAT Network**
- 🐉 A Kali Linux VM with a manual static IP
- 📡 Connectivity and DNS testing
- 📸 A clean **VM snapshot** for quick recovery

## 🎯 Objectives

| # | Objective |
|---|---|
| 1 | Install and configure Oracle VirtualBox |
| 2 | Import and run the Kali Linux virtual machine |
| 3 | Create a private NAT Network for the lab |
| 4 | Configure the Kali Linux network settings |
| 5 | Verify network connectivity and DNS resolution |
| 6 | Take a clean VM snapshot for recovery |
| 7 | Document the whole process with screenshots |
| 8 | Prepare the environment for future security projects |

### 🧭 Future learning areas

`Network Security` · `Linux Administration` · `Ethical Hacking` · `Digital Forensics` · `Security Monitoring` · `Incident Investigation`

---

## 🏗️ Lab Architecture

A Windows 11 host runs VirtualBox. Kali Linux is the attacker/security machine, and all VMs share one custom NAT Network (`10.0.0.0/24`). More target machines can be added later.

<div align="center">

<img width="1370" height="623" alt="05-lab-architecture" src="https://github.com/user-attachments/assets/610d5107-8fd7-4760-bd16-15ba9ce51af4" />

<sub>Reference architecture diagram — credit: <a href="https://networkwalks.com">NetworkWalks</a>. Only the Kali VM is built in this project; the other VMs are optional future additions.</sub>

</div>

> **Note:** A NAT Network provides virtual networking and outbound internet access, but it is **not automatically a fully isolated security boundary**. Review network and access settings before running security experiments or adding vulnerable machines.

---

## ⚙️ Lab Configuration

| Component | Configuration |
|---|---|
| 🖥️ Host OS | Windows 11 |
| 🧠 Host RAM | 20 GB |
| ⚡ Processor | Intel Core i5 |
| 🧰 Hypervisor | VirtualBox 7.1.4 |
| 🐉 Security OS | Kali Linux 2023.2 |
| 🧠 Kali RAM | 4096 MB |
| 🌐 Virtual Network | NAT Network (`NatNetwork`) |
| 📡 Network Address | `10.0.0.0/24` |
| 🐧 Kali IP Address | `10.0.0.2/24` (netmask `255.255.255.0`) |
| 🚪 Default Gateway | `10.0.0.1` |
| 🌍 DNS Server | `8.8.8.8` |
| 🔮 Future VM Range | `10.0.0.3 – 10.0.0.99` |

---

## 🪜 Setup Procedure

### Step 1 — Install 7-Zip 🗜️

Installed [7-Zip](https://www.7-zip.org/) on the Windows 11 host to extract compressed `.7z` archives used for the virtual machine files.

### Step 2 — Install Oracle VirtualBox 📦

Installed [Oracle VirtualBox](https://www.virtualbox.org/) on the host. It lets Kali Linux run inside a virtual machine without replacing Windows.

### Step 3 — Create a Private NAT Network 🌐

1. Opened VirtualBox's network manager.
2. Created a new NAT Network named **`NatNetwork`**.
3. Set the IPv4 prefix to **`10.0.0.0/24`**.
4. Kept **DHCP enabled** and IPv6 disabled.
5. Attached the Kali VM to this network.

<div align="center">

<img width="955" height="932" alt="02-virtualbox-nat-network" src="https://github.com/user-attachments/assets/4ee2a109-c9fa-414e-a00f-6ed106ec978c" />


<sub>VirtualBox → NAT Networks: <code>NatNetwork</code> with prefix <code>10.0.0.0/24</code> and DHCP enabled.</sub>

</div>

### Step 4 — Import and Start Kali Linux 🐉

The Kali VM was downloaded from the [official Kali website](https://www.kali.org/get-kali/) and imported into VirtualBox.

```text
Adapter 1
  Attached to : NAT Network
  Network     : NatNetwork
  Adapter Type: Intel PRO/1000 MT Desktop

RAM: 4096 MB
```

<div align="center">

<img width="1918" height="948" alt="03-kali-desktop" src="https://github.com/user-attachments/assets/780a6206-d6e8-4530-81c2-31edc59257d5" />


<sub>Kali Linux booted successfully inside VirtualBox.</sub>

</div>

### Step 5 — Configure the Kali Linux Network 🔧

Opened the Kali network settings (**Wired → IPv4**) and set a manual static configuration:

| Setting | Value |
|---|---|
| IPv4 Method | Manual |
| Address | `10.0.0.2` |
| Netmask | `255.255.255.0` |
| Gateway | `10.0.0.1` |
| DNS | `8.8.8.8` |

<div align="center">

<img width="743" height="596" alt="01-kali-network-settings" src="https://github.com/user-attachments/assets/1707aed4-f54b-4020-9fc5-24d68037359a" />


<sub>Kali Linux Wired connection → IPv4 manual configuration.</sub>

</div>

### Step 6 — Configure a Shared Folder 📂

A VirtualBox shared folder was used to move screenshots and documentation between Windows and Kali.

1. Created a transfer folder on the Windows host.
2. Opened the Kali VM **Settings → Shared Folders**.
3. Added the host folder and enabled **Auto-mount** if needed.
4. Confirmed Kali can access the folder.

### Step 7 — Take a Clean VM Snapshot 📸

Created a clean snapshot with VirtualBox's snapshot feature. It is a recovery point I can restore if a future experiment breaks the configuration.

<div align="center">

<img width="953" height="932" alt="04-virtualbox-snapshot" src="https://github.com/user-attachments/assets/5cbfaa20-7ed7-4de8-87b8-3d20814a0a9f" />


<sub>Snapshots tab showing the saved Kali Linux snapshot and the current (changed) state.</sub>

</div>

---

## 🔎 Lab Verification

Run these commands inside Kali to verify the lab:

| Test | Command | Expected Result |
|---|---|---|
| 🧾 Check IP address | `ip a` | Shows `10.0.0.2/24` |
| 🚪 Test gateway | `ping -c 4 10.0.0.1` | Successful replies |
| 🌍 Test internet | `ping -c 4 8.8.8.8` | Successful replies |
| 🔤 Test DNS | `ping -c 4 google.com` | Name resolves and replies |
| 📸 Verify snapshot | Restore snapshot, then run `ip a` | Baseline configuration restored |

**Expected network values**

```text
IP Address : 10.0.0.2/24
Gateway    : 10.0.0.1
DNS        : 8.8.8.8
```

> ✅ Always confirm these against your real command output before treating them as verified.

---

## 🐞 Troubleshooting

<details>
<summary><b>Click to expand common problems and fixes</b></summary>

<br>

| Problem | What to check |
|---|---|
| Archive cannot be extracted | Make sure 7-Zip is installed and the download is complete |
| Kali does not start | Review VM settings and confirm the image was imported correctly |
| No network connection | Check the VirtualBox network attachment and Kali network settings |
| Domain ping fails | Check DNS settings, connection status, and whether ICMP is filtered |
| Shared folder not accessible | Review shared-folder settings and guest permissions |
| VM becomes unstable | Restore the clean snapshot (unsaved changes will be lost) |

*These are general troubleshooting references, not a claim that every issue occurred during this setup.*

</details>

---

## 💡 What I Learned

- ✅ Preparing a virtualization environment on Windows 11
- ✅ Importing and running Kali Linux in VirtualBox
- ✅ Creating a dedicated NAT Network for a security lab
- ✅ Configuring a static IP and DNS on Linux
- ✅ Testing basic connectivity with `ip a` and `ping`
- ✅ Creating and using VM snapshots for recovery
- ✅ Documenting technical work clearly for GitHub

---

## 🔐 Security & Ethical Use

> ⚠️ **This lab is for educational purposes and authorized security testing only.**
> Only use it on systems you **own** or have **explicit written permission** to test. Never use the lab or its tools against unauthorized systems.

---

## 🔗 Tools & Resources

| Tool | Purpose |
|---|---|
| [Oracle VirtualBox](https://www.virtualbox.org/) | Virtualization platform |
| [Kali Linux](https://www.kali.org/) | Security and penetration testing OS |
| [7-Zip](https://www.7-zip.org/) | Archive extraction utility |
| [Kali Documentation](https://www.kali.org/docs/) | Official installation and usage docs |
| [NetworkWalks](https://networkwalks.com) | Lab architecture reference |
| [GitHub](https://github.com/) | Source control and portfolio hosting |

---

## 👤 Author

<div align="center">

**Shahid Latif**
*Aspiring Cybersecurity Professional*

[![GitHub](https://img.shields.io/badge/GitHub-shahidlatif00777-181717?style=for-the-badge&logo=github)](https://github.com/shahidlatif00777)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Shahid%20Latif-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shahid-latif-03a8813a/)

<sub>This project is the foundation for future cybersecurity labs, practical exercises and GitHub portfolio projects.</sub>

</div>
