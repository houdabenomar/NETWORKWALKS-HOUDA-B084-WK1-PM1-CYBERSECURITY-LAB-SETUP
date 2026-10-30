# 📝 Week 1 - Detailed Lab Setup Notes

## 🎯 Objective
Set up the virtual lab environment using VirtualBox and Kali Linux, configure the virtual network, and troubleshoot the VM network configuration.

## 1. VirtualBox Installation & Network Configuration
- **Action:** Installed Oracle VirtualBox (version 7.2.22) and 7-Zip on my Windows host.
- **Network Creation:** 
  - Opened **File > Tools > Network Manager**.
  - Created a new **NAT Network** named `NatNetwork`.
  - Set the IPv4 Prefix to `10.0.0.0/24`.
  - Enabled DHCP to allow the VM to get an IP automatically.
  - *Proof:* See `natnetwork2.png.png` in the screenshots folder.

## 2. Kali Linux VM Configuration
- **Action:** Extracted and imported the Kali Linux 2026.3 `.vbox` file into VirtualBox.
- **VM Settings:**
  - **Network:** Attached to `NAT Network` and selected `NatNetwork`.
  - **Shared Folders:** Added my host's `Downloads` folder with "Auto-mount" enabled.
  - **General:** Set Shared Clipboard and Drag-and-Drop to "Bidirectional".
  - *Proof:* See `virtualbox2.png.png` in the screenshots folder.

## 3. IP Configuration & Troubleshooting (The Real Work)
- **Initial State:** After starting Kali, I ran `ip a` and saw the IP was `10.0.0.3/24` (assigned by DHCP). 
- **Problem:** The project requires the IP to be exactly `10.0.0.2/24`.
- **Solution:** I manually set the static IP using the terminal:
  ```bash
  sudo ip addr add 10.0.0.2/24 dev eth0
  sudo ip link set eth0 up
