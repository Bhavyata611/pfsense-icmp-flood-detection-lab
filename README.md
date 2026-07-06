# 🛡️ ICMP Flood Attack Detection & Mitigation using pfSense Firewall

## 📌 Project Overview

This project demonstrates how a pfSense firewall can detect and mitigate an ICMP Flood (Denial-of-Service) attack in a virtual lab environment.

The lab was built using VirtualBox with three virtual machines: Kali Linux (Attacker), pfSense Community Edition (Firewall), and Ubuntu Desktop (Victim). An ICMP flood attack was generated from Kali Linux using **hping3**, monitored using **Wireshark**, and successfully mitigated by implementing a firewall rule in pfSense. Firewall logs were then analyzed to verify that the malicious traffic was blocked.

This project provides practical experience in firewall administration, packet analysis, attack simulation, network security, and log analysis—essential skills for a SOC Analyst.

---

# 🎯 Objectives

- Build a segmented virtual network using pfSense.
- Simulate an ICMP Flood (DoS) attack.
- Capture and analyze network traffic using Wireshark.
- Configure firewall rules to block malicious traffic.
- Verify mitigation using pfSense firewall logs.
- Understand firewall rule processing and traffic filtering.

---

# 🏗️ Lab Architecture

```
                Internet / Host Network
                        │
                        │
                Kali Linux (Attacker)
                 10.200.246.192
                        │
                WAN Interface
                  pfSense Firewall
                LAN Interface (192.168.1.1)
                        │
                        │
              Ubuntu Desktop (Victim)
                 192.168.1.100
```

---

# 🖥️ Lab Environment

| Component | Purpose |
|-----------|---------|
| VirtualBox | Virtualization Platform |
| pfSense CE 2.7.2 | Firewall |
| Kali Linux | Attacker Machine |
| Ubuntu Desktop | Victim Machine |
| hping3 | ICMP Flood Generation |
| Wireshark | Packet Analysis |

---

# 🌐 Network Configuration

| Device | IP Address |
|---------|------------|
| Kali Linux | 10.200.246.192 (WAN) & 192.168.1.101 (Internal) |
| pfSense WAN | 10.200.246.115 |
| pfSense LAN | 192.168.1.1 |
| Ubuntu | 192.168.1.100 |

---

# ⚙️ Technologies Used

- pfSense Community Edition
- VirtualBox
- Kali Linux
- Ubuntu Desktop
- Wireshark
- hping3
- ICMP
- TCP/IP Networking
- Firewall Rules
- Packet Capture

---

# 🔬 Attack Simulation

The attack machine (Kali Linux) generated an ICMP Flood against the Ubuntu victim using **hping3**.

### Attack Command

```bash
sudo hping3 --icmp --flood 192.168.1.100
```

The command continuously transmitted ICMP Echo Requests toward the target to simulate a Denial-of-Service attack.

---

# 📊 Traffic Analysis using Wireshark

Wireshark was used on the Ubuntu machine to monitor incoming network traffic.

Observations:

- Continuous ICMP Echo Requests
- High packet rate
- Source IP identified
- Destination IP verified
- Packet details inspected

The packet capture confirmed that the Ubuntu system was receiving the ICMP flood traffic before firewall mitigation.

---

# 🛡️ Firewall Mitigation using pfSense

A WAN firewall rule was created to block the attacker's IP address.

Rule Summary

- Interface: WAN
- Action: Block
- Protocol: IPv4 ICMP
- Source: 10.200.246.192
- Destination: LAN Address

The block rule was placed above the allow rule to ensure pfSense processed it first.

After applying the rule, ICMP flood traffic was successfully blocked.

---

# 📑 Firewall Log Analysis

The pfSense Firewall Logs were monitored after enabling the block rule.

The logs confirmed:

- Blocked ICMP packets
- Attacker source IP
- Victim destination IP
- Interface used
- Rule matched

This verified that pfSense successfully mitigated the simulated DoS attack.

---

# 📸 Screenshots

## pfSense Dashboard

![Dashboard](screenshots/01-pfsense-dashboard.png)

---

## Wireshark ICMP Traffic Capture

![Wireshark](screenshots/02-wireshark-icmp-flood.png)

---

## Kali Linux ICMP Flood Attack

![Attack](screenshots/03-kali-hping3-attack.png)

---

## pfSense Firewall Rules

![Rules](screenshots/04-pfsense-block-rule.png)

---

## pfSense Firewall Logs

![Logs](screenshots/05-pfsense-firewall-logs.png)

---

# 🎓 SOC Analyst Skills Demonstrated

- Firewall Administration
- Network Traffic Analysis
- Packet Capture
- ICMP Protocol Analysis
- DoS Attack Simulation
- Firewall Rule Configuration
- Threat Detection
- Log Analysis
- Network Troubleshooting
- Security Monitoring

---

# 📚 Key Learnings

- Understanding ICMP Flood attacks
- Firewall rule precedence in pfSense
- Packet inspection using Wireshark
- Traffic filtering techniques
- Firewall log analysis
- Virtual network configuration
- Network segmentation
- Attack detection and mitigation

---

# 🚀 Future Improvements

- Configure IDS/IPS using Suricata
- Integrate pfSense logs with Wazuh
- Forward firewall logs to Splunk
- Simulate TCP SYN Flood attacks
- Perform Nmap scan detection
- Implement Geo-IP blocking
- Configure firewall aliases
- Automate threat detection workflows

---

# 👨‍💻 Author

**Dhruv Kachchhi**

Aspiring SOC Analyst | Cybersecurity Enthusiast

- LinkedIn: *(Add your profile link)*
- GitHub: *(Add your GitHub profile link)*

---

## ⭐ If you found this project useful, consider giving it a star!
