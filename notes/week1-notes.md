# 📝 Week 1 - Lab Setup Notes

**Student:** Houda Benomar  
**Batch:** B084  
**Date:** October 2026

---

## 🎯 Objective

Set up a virtual cybersecurity testing lab using VirtualBox and Kali Linux, with a custom NAT Network (`10.0.0.0/24`), static IP for Kali (`10.0.0.2/24`), internet access, clipboard/drag-drop enabled, and a shared `/Downloads` folder from the host.

---

## 📋 Step-by-Step Configuration

### Step 1: Install 7-Zip and VirtualBox
- Downloaded and installed **7-Zip** from [7-zip.org](https://7-zip.org/download.html).
- Downloaded and installed **VirtualBox 7.2.22** from [virtualbox.org](https://virtualbox.org/wiki/Downloads).

### Step 2: Create NAT Network in VirtualBox
- Opened VirtualBox → **Tools** → **Network**.
- Selected the **NAT Networks** tab → clicked **Create**.
- Configured:
  - **Name**: `NatNetwork`
  - **IPv4 Prefix**: `10.0.0.0/24`
  - **Enable DHCP**: ✅ (checked)
- Clicked **Apply**.

### Step 3: Import Kali Linux VM
- Downloaded the Kali Linux VirtualBox image (`.7z` file) from [kali.org/get-kali](https://kali.org/get-kali).
- Extracted the `.7z` file using 7-Zip and imported the `.vbox` file into VirtualBox.

### Step 4: Configure Kali VM Settings
- **Network**:
  - Adapter 1 → Attached to: **NAT Network**
  - Name: `NatNetwork`
  - Promiscuous Mode: **Allow All**
  - ✅ Virtual Cable Connected
- **General → Advanced**:
  - ✅ Enable Clipboard: **Bidirectional**
  - ✅ Enable Drag'n'Drop: **Bidirectional**
- **Shared Folders**:
  - Added a shared folder:
    - **Folder Path**: `C:\Users\...\Downloads` (host)
    - **Folder Name**: `Downloads`
    - ✅ Auto-mount
    - ✅ Make Permanent
  - After starting Kali, the folder appeared on the Desktop as `sf_Downloads`.

### Step 5: Configure IP on Kali Linux (Terminal Method)
- Started the Kali VM and opened a terminal.
- Used the `ip` command to add the static IP manually:
```bash
sudo ip addr add 10.0.0.2/24 dev eth0
sudo ip link set eth0 up
    Note: I used this command-line method to quickly assign the IP as requested. The interface already had a DHCP IP (10.0.0.3), so 10.0.0.2 was added as a secondary address.

Step 6: Test Internet Connectivity

    Ran:

bash

ping -c 4 8.8.8.8

    Received replies → ✅ Internet access confirmed.

🛠️ Troubleshooting & Observations

Observation on IP Configuration:

    When I imported Kali, the VM initially received a DHCP IP (10.0.0.3).

    I used the ip addr add command to assign the static IP 10.0.0.2 as required by the lab.

    Note for future labs: This method is temporary. If the VM is restarted, the IP will revert to DHCP. A permanent solution would be to configure the IP via the Network Manager GUI (Wired Settings → IPv4 → Manual) or by editing the nmcli settings.

✅ Final Checklist
Requirement	Status
VirtualBox installed (latest)	✅
Kali Linux VM imported	✅
NAT Network 10.0.0.0/24 created	✅
Kali IP 10.0.0.2/24 assigned	✅
Internet access (ping 8.8.8.8)	✅
Clipboard & Drag/Drop enabled	✅
Shared /Downloads folder	✅
Snapshot taken	✅
📌 Notes

    All screenshots are available in the repository root.

    The shared folder sf_Downloads is visible on the Kali desktop.

