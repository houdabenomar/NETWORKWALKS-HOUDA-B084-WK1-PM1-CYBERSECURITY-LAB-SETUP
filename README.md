# 🛡️ Cybersecurity Lab Environment Setup

**Networkwalks Internship - Batch B084**

## 📖 Project Overview

Welcome to my Week 1 project! This repository documents the setup of my personal virtual cybersecurity laboratory. The goal was to create a safe, isolated environment using **VirtualBox** and **Kali Linux** to practice penetration testing.

## 🖥️ Host Machine Specifications

| Component | Details |
| :--- | :--- |
| **Host OS** | Windows 11 (64-bit) |
| **Processor** | Intel(R) Core(TM) i7-8665U CPU @ 1.90GHz (2.11 GHz) |
| **RAM** | 16.0 GB |
| **Storage** | 238 GB (227 GB used) |
| **Graphics** | Intel(R) UHD Graphics 620 |

## ⚙️ Virtual Lab Configuration

| Component | Details |
| :--- | :--- |
| **Virtualization** | Oracle VirtualBox 7.2.22 |
| **Attacker Machine** | Kali Linux (2026.3) |
| **Network Type** | NAT Network (`10.0.0.0/24`) |
| **Kali IP** | `10.0.0.2/24` (Static) |
| **Gateway** | `10.0.0.1` |
| **DNS Server** | `8.8.8.8` |
| **Clipboard & Drag/Drop** | Enabled (Bidirectional) |
| **Shared Folders** | `/downloads` (Host) → `/media/sf_downloads` (Kali) |
| **Snapshot** | `Clean_State_After_Config` (created after full configuration) |

> **Note**: Phase 2 (Windows/Android VMs) is optional and not included in this submission.

## 📸 Proof of Work (Screenshots)

### 1. NAT Network Configuration (10.0.0.0/24)
*Setting up the custom NAT Network in VirtualBox.*
![NAT Network](natnetwork2.png)

### 2. Virtual Machine Network Settings
*Configuring the Kali VM to use the NAT Network and Shared Folders.*
![VM Network Settings](virtualbox2.png)

### 3. Kali Linux Terminal (IP & Internet Test)
*Successfully assigning the static IP `10.0.0.2` and verifying internet connectivity with a ping to 8.8.8.8.*
![Kali Terminal](kali3.png)

### 4. Snapshot Verification
*Successfully created a snapshot of the clean VM state after configuration (named `Clean_State_After_Config`).*
![Snapshot](snapshot.png)

## 🧠 Detailed Notes & Troubleshooting

For a step-by-step breakdown of the commands used and the issues I faced (like the DHCP IP issue), please read my detailed notes:
👉 **[Click here to read the Week 1 Notes](notes/week1-notes.md)**

---

*Created by **Houda Benomar** - Cybersecurity Intern at Networkwalks*
