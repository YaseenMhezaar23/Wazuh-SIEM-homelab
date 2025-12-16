# 🔐 Wazuh SIEM Home Lab – Security Event Analysis

## 📌 Project Overview
This project demonstrates a **hands-on Wazuh SIEM/XDR home lab** setup for **security monitoring, log analysis, and file integrity monitoring (FIM)**.  
The lab simulates a real-world SOC environment by deploying a **Wazuh Manager on Ubuntu** and a **Wazuh Agent on a Windows endpoint**, enabling centralized visibility of security events.

This project is designed to build **SOC Analyst (L1/L2)** skills and practical understanding of endpoint monitoring, alerting, and incident detection.

---

## 🛠️ Technologies Used
- **Wazuh SIEM / XDR (v4.12)**
- **Ubuntu Server** (Wazuh Manager + Dashboard)
- **Windows 10** (Wazuh Agent)
- **VirtualBox** (Hypervisor)
- **File Integrity Monitoring (FIM)**
- **Linux CLI & Windows OSSEC Agent**
- **TCP/IP Networking**

---

## 🧱 Lab Architecture
Windows 10 Endpoint (Wazuh Agent)
│
│ Logs & Security Events
▼
Ubuntu Server (Wazuh Manager + Dashboard)



- Both systems are connected using a **bridged network adapter**
- Communication occurs within the same subnet (e.g., `192.168.0.0/24`)
- Two-way connectivity ensures real-time log forwarding

---

## 📋 System Requirements
- Laptop/Desktop with **minimum 8 GB RAM**
- **VirtualBox** or any hypervisor
- Ubuntu ISO (for Wazuh Manager)
- Windows 10 system (physical or virtual)

---

## ⚙️ Wazuh Manager Installation (Ubuntu)
1. Add Wazuh GPG key:
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo gpg --dearmor -o /usr/share/keyrings/wazuh-archive-keyring.gpg
Download and run the installer:

curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh

sudo bash ./wazuh-install.sh -a -i

Access the Wazuh Dashboard:
https://<Ubuntu-IP>


Default username: admin
Password is displayed after installation

🖥️ Wazuh Agent Installation (Windows)
Download the Windows agent from the official Wazuh documentation

Install using GUI or CLI

Enter the Wazuh Manager IP address

Generate and import the authentication key from the manager:


sudo /var/ossec/bin/manage_agents
Restart the agent service

✅ Agent Verification
Navigate to Wazuh Dashboard → Agents

Confirm the Windows agent status shows Active

Verify logs are being received successfully

📂 File Integrity Monitoring (FIM)
To simulate real-world attack detection:

Configure a custom directory in the Windows agent:

<directories realtime="yes">C:\Users\<username>\Downloads\WAZUH-TEST</directories>
Restart the Wazuh Agent

Perform actions in the monitored directory:

Create a file

Modify a file

Delete a file

Observe real-time alerts in:


Wazuh Dashboard → File Integrity Monitoring
🔎 Security Events Observed
File creation events

File modification alerts

File deletion logs

Endpoint metadata (IP, agent name, timestamp)

These events closely mirror real SOC investigations.

🎯 Learning Outcomes
Practical experience with SIEM & XDR

Understanding agent–manager communication

Hands-on endpoint log monitoring

Real-time file integrity alerts

SOC-style event analysis workflow

📈 Use Case
This project is suitable for:

SOC Analyst L1 / L2

SIEM Engineer (Junior)

Cybersecurity Freshers

Blue Team & DFIR learning

📚 References
Official Wazuh Documentation

Hands-on Wazuh SIEM Home Lab Setup 


👤 Author
Yaseen Mhezaar
Aspiring SOC Analyst | SIEM & Blue Team Enthusiast


