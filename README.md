# 🌐 Network Scanning & Host Discovery with Zenmap (W2-PM5)

![Cybersecurity](https://img.shields.io/badge/Track-Offensive_Security-red.svg)
![Tool](https://img.shields.io/badge/Tool-Zenmap_Nmap-blue.svg)
![Batch](https://img.shields.io/badge/Batch-B082_Networkwalks-green.svg)
![Environment](https://img.shields.io/badge/Scope-192.168.56.0%2F24-orange.svg)

---

## 📌 Executive Summary
Network scanning constitutes Phase 2 of penetration testing and ethical hacking. In this practical module, Zenmap (the official graphical frontend for Nmap) was utilized to perform local area network (LAN) discovery, active host identification, and network topology mapping.

The objective of this assessment was to map active devices across the subnet, identify live IP and interface parameters, and visually document connected network assets.

---

## ⚙️ Target & Environment Scope
* **Pentester / Author:** Faheem Ali Wattoo
* **Program:** Networkwalks Cybersecurity & Ethical Hacking Internship
* **Batch Code:** B082-Networkwalks
* **Target Network Subnet:** `192.168.56.0/24` (VirtualBox Host-Only Network Adapter)
* **Scanner Platform:** Windows PC (Zenmap GUI v7.991)

---

## 🧰 Tools & Commands Matrix

| Tool / Utility | Role | Command Executed |
| :--- | :--- | :--- |
| **Windows CMD** | Local IP & Subnet Discovery | `ipconfig` |
| **Zenmap (GUI)** | Ping Scan / Host Discovery | `nmap -sn 192.168.56.0/24` |
| **Zenmap Topology** | Visual Node Mapping | Radial Net Graph Export |

---

## 🔬 Hands-on Technical Activities & Verification

### 🔹 Task 1 & 2: Local Subnet Identification
Executed the `ipconfig` command in the Windows Command Prompt to identify the local network configuration and subnet boundaries:
* **Local Subnet:** `192.168.56.0/24`
* **Default Host Interface:** `192.168.56.1`

---

### 🔹 Task 3 & 4: Ping Scan & Live Host Discovery
Configured Zenmap with the target subnet `192.168.56.0/24` and selected the **Ping Scan** profile to identify active hosts.

`nmap -sn 192.168.56.0/24`

* **Scan Duration:** Scanned 256 IP addresses in 12.10 seconds.
* **Live Hosts Discovered:** 1 active host (`192.168.56.1`).

#### Evidence - Nmap Output Scan:
![Zenmap Ping Scan](Screenshot_ping_scan.png)

---

### 🔹 Task 5 & 6: IP & MAC Address Enumeration
* **Active Host IP:** `192.168.56.1`
* **MAC Address Observation:** Nmap does not display the MAC address for the scanning machine's own local adapter (verified locally via `ipconfig /all`).

---

### 🔹 Task 7: Network Topology Generation & Export
Opened the **Topology** tab in Zenmap, enabled the visual legend, and inspected the radial node graph. Exported the network map as a vector graphic/PDF.

#### Evidence - Zenmap Topology Interface:
![Zenmap Topology GUI](Screenshot_1st_nmap_scan.png)

#### Rendered Network Topology Graphic:
[Download/View Topology PDF](https://github.com/user-attachments/files/31264812/1st_sacn.pdf)

---

## 📊 Risk Analysis & Security Impact

| # | Finding | Observation / Proof | Potential Security Risk | Risk Level |
| :---: | :--- | :--- | :--- | :---: |
| **01** | Subnet Responsiveness | Active ICMP/probe response on `192.168.56.1` | Enables attackers to verify live targets across the address space | `Low` |
| **02** | Unsegmented Local Adapters | Host interface responds to internal discovery scans | Unrestricted discovery aids lateral movement and reconnaissance | `Low` |

---

## 🛡️ Defensive Recommendations & Hardening

* **ICMP Probe Filtering:** Configure host firewall rules to drop unsolicited ICMP echo requests if stealth asset discovery protection is required.
* **Network Segmentation & VLANs:** Isolate virtual adapters and test lab environments from primary production networks to prevent unintended reachability.
* **Routine Asset Auditing:** Conduct periodic internal network discovery scans to identify unauthorized or rogue devices connected to internal subnets.

---

## 👨‍💻 Author / Pentester Details
* **Pentester Name:** Faheem Ali Wattoo
* **Program:** Networkwalks Cybersecurity & Ethical Hacking Internship
* **Batch:** B082-Networkwalks
* **Lead Instructor:** [Waqas Karim CCIE](https://www.linkedin.com/in/waqaskarim/)
