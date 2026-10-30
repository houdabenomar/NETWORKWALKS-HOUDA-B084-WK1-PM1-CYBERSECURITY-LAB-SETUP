# Week 1 — Lab Setup & Network Configuration

## 🎯 Objective

Set up the virtual lab environment using VirtualBox and Kali Linux, configure the virtual network, and troubleshoot the VM network configuration.

---

## 1. VirtualBox Installation & Network Configuration

### Tools

- Oracle VirtualBox 7.2.22
- 7-Zip
- Kali Linux 2026.3
- Windows 11 host

### NAT Network Configuration

I created a new **NAT Network** in VirtualBox:

- **Network name:** `NatNetwork`
- **IPv4 Prefix:** `10.0.0.0/24`
- **DHCP:** Enabled

DHCP was initially enabled so that the Kali Linux VM could automatically receive an IP address.

📸 **Proof:** `screenshots/natnetwork.png`

---

## 2. Kali Linux VM Configuration

I extracted the Kali Linux 2026.3 virtual machine and imported the `.vbox` file into VirtualBox.

### VM Configuration

**Network**
- Attached to: `NAT Network`
- Network name: `NatNetwork`

**Shared Folder**
- Host folder: `Downloads`
- Auto-mount: Enabled

**General**
- Shared Clipboard: `Bidirectional`
- Drag and Drop: `Bidirectional`

📸 **Proof:** `screenshots/virtualbox.png`

---

## 3. IP Configuration & Troubleshooting

This was the main troubleshooting step of the week.

After starting Kali Linux, I checked the network configuration with:

```bash
ip a
```

The interface initially received:

```text
10.0.0.3/24
```

The lab requirement was:

```text
10.0.0.2/24
```

### Problem

The VM received an IP address from DHCP, but the assigned address did not match the IP required by the lab.

### Solution

I manually added the required IP address to the network interface:

```bash
sudo ip addr add 10.0.0.2/24 dev eth0
sudo ip link set eth0 up
```

I then verified the network configuration again with:

```bash
ip a
```

### What I learned

- How to inspect network interfaces using `ip a`
- The difference between a DHCP-assigned IP and a manually configured IP
- How to add an IP address to a Linux network interface
- How VirtualBox NAT Networks provide connectivity to virtual machines
- Basic Linux network troubleshooting

---

## 📌 Week 1 Summary

**Completed:**

- [x] Installed VirtualBox
- [x] Installed 7-Zip
- [x] Created a NAT Network
- [x] Configured `NatNetwork`
- [x] Imported Kali Linux
- [x] Configured the VM network
- [x] Configured shared folders
- [x] Checked the Kali network interface
- [x] Identified an IP configuration problem
- [x] Manually configured the required IP address
- [x] Verified the network configuration

### Key commands learned

```bash
ip a
sudo ip addr add 10.0.0.2/24 dev eth0
sudo ip link set eth0 up
```

**Main takeaway:**  
This week was not only about installing the tools. I also practiced basic Linux networking and troubleshooting by identifying and correcting an IP configuration issue.
