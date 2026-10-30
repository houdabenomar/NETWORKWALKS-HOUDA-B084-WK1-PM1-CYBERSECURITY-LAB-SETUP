```markdown
# 📝 Week 1 - Detailed Lab Setup Notes

## 🎯 Objective
Set up a virtual lab environment using VirtualBox and Kali Linux, configure the virtual network, and troubleshoot the VM network configuration.

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

📸 **Proof:** See `natnetwork2.png.png` in the main folder.

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

📸 **Proof:** See `virtualbox2.png.png` in the main folder.

---

## 3. IP Configuration & Troubleshooting (The Main Work)

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

I then verified the network configuration again with `ip a`.

### DNS Configuration
I also verified that the DNS server was set to `8.8.8.8` to ensure domain name resolution works.

### What I Learned
- How to inspect network interfaces using `ip a`
- The difference between a DHCP-assigned IP and a manually configured IP
- How to add an IP address to a Linux network interface
- Basic Linux network troubleshooting

---

## 4. Internet Connectivity Test

- **Action:** Ran the command `ping -c 4 8.8.8.8`.
- **Result:** Received 4 packets with 0% packet loss. The VM has full internet access through the NAT Network.
- 📸 **Proof:** See `kali3.png` in the main folder.

---

## 5. Snapshot Creation

- **Action:** After completing all configurations, I took a snapshot of the VM named **"Lab Setup Complete"** to save a clean, working state.
- 📸 **Proof:** See `snapshot.png` in the main folder.

---

## 📌 Week 1 Summary

**Completed:**
- [x] Installed VirtualBox and 7-Zip
- [x] Created a NAT Network (`10.0.0.0/24`)
- [x] Configured `NatNetwork`
- [x] Imported Kali Linux
- [x] Configured the VM network and shared folders
- [x] Checked the Kali network interface
- [x] Identified an IP configuration problem
- [x] Manually configured the required IP (`10.0.0.2`)
- [x] Verified the DNS (`8.8.8.8`) and internet connectivity
- [x] Created a VM snapshot

### Key Commands Learned
```bash
ip a
sudo ip addr add 10.0.0.2/24 dev eth0
sudo ip link set eth0 up
ping -c 4 8.8.8.8
```

**Main Takeaway:**  
This week was not only about installing tools. I also practiced basic Linux networking and troubleshooting by identifying and correcting an IP configuration issue, and I learned the importance of documenting each step.
```


