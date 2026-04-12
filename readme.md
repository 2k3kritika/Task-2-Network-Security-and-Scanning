# 🔐 Task 2: Network Security & Scanning

## 📌 Overview

This phase focuses on **reconnaissance, network scanning, and traffic analysis** to understand how attackers discover and analyze target systems.

The goal is to simulate real-world attack scenarios by:

* Gathering intelligence (Passive & Active Recon)
* Identifying open ports and services
* Detecting vulnerabilities in systems
* Analyzing network traffic and attack patterns

---

## 🚀 What This Project Demonstrates

* Ability to perform **passive and active reconnaissance**
* Hands-on experience with **network scanning using Nmap**
* Practical understanding of **service enumeration and OS detection**
* Ability to perform **vulnerability scanning using OpenVAS/Nessus**
* Skills in **network traffic analysis using Wireshark**
* Basic **firewall rule creation and attack mitigation**

---

## 🕵️ Reconnaissance

### 🔍 Passive Recon (No Direct Interaction with Target)

* Whois – Domain ownership and registration details
* Nslookup – DNS information gathering
* Google Dorking – Finding exposed sensitive data
* Shodan – Discovering internet-exposed devices

📄 Detailed Notes → [Day 1 Passive Recon](/docs/passive_recon.md)

---

### ⚡ Active Recon (Direct Interaction with Target)

* Ping Sweep – Identify live hosts in a network
* Banner Grabbing – Extract service information from open ports

📄 Detailed Notes → [Day 2 Active Recon](/docs/active_recon.md)

---

## 🌐 Port & Service Scanning

### 🔎 Nmap Scanning Techniques

* TCP SYN Scan (`-sS`) – Stealthy and fast scanning
* UDP Scan (`-sU`) – Detect UDP services

### 🧪 Enumeration Features

* Service Version Detection (`-sV`)
* OS Detection (`-O`)

These techniques help in identifying:

* Open ports
* Running services
* System details of the target machine

📄 Detailed Notes → [Day 3 Nmap Scanning](/docs/nmap_scanning.md)

---

## 🛡️ Vulnerability Scanning

### 🔧 Tools Used

* OpenVAS / Nessus Essentials

### 🧪 Lab Setup

* Target: Metasploitable2

### 📊 Analysis

Vulnerabilities are categorized as:

* Critical
* High
* Medium
* Low

This helps prioritize security risks and understand potential attack paths.

📄 Detailed Notes → [Day 4 Vulnerability Scanning](/docs/vulnerability_scanning.md)

---

## 🔥 Network Traffic Analysis

### 📡 Packet Capture & Analysis

* Captured protocols:

  * HTTP
  * FTP
  * DNS

### 🔍 Key Findings

* Identified credentials in **unencrypted FTP traffic**
* Observed request-response patterns in HTTP
* Analyzed DNS queries and resolutions

### ⚠️ Attack Simulation

* SYN Flood attack simulated using `hping3`
* Traffic analyzed using Wireshark

📄 Detailed Notes → [Day 5 Traffic Analysis](/docs/traffic_analysis.md)

---

## 🧱 Firewall Basics

### 🔐 iptables Configuration

* Created rules to:

  * Allow specific ports
  * Deny unauthorized access

### 🛡️ Defense Demonstration

* Simulated port scan attempts
* Demonstrated blocking using firewall rules

📄 Detailed Notes → [Day 6 Firewall](/docs/firewall_basics.md)

---

## 📊 Scan Reports

### 🧾 Nmap Scan Report

* Identified open ports and services
* Interpreted attack surface of target system

### 🧾 OpenVAS / Nessus Report

* Detailed vulnerability breakdown
* Risk categorization and analysis

📁 Reports Folder → [./reports/](/reports/)

---

## 🧪 Lab Environment

[Kali Linux] ---> [Metasploitable2]

* Controlled and isolated environment
* Safe for testing offensive techniques

---

## 📁 Repository Structure (Task 2)

```
Task2_Network_Scanning/
│
├── README.md
│
├── docs/
│   ├── passive_recon.md
│   ├── active_recon.md
│   ├── nmap_scanning.md (Port & Service Scanning)
│   ├── vulnerability_scanning.md
│   ├── traffic_analysis.md (Packet Analysis with Wireshark)
│   └── firewall_basics.md
│
├── screenshots/
│
├── reports/
│   ├── nmap_report.txt
│   └── nessus_report.pdf
│
└── scripts/
```

---

## 🎥 Demo Video

📌 LinkedIn Video: [Task 2 Demonstration](https://www.linkedin.com/posts/kritika-sharma-0150b6396_cybersecurity-ethicalhacking-nmap-activity-7449148784342745088-QpGV?utm_source=share&utm_medium=member_android&rcm=ACoAAGEww5EBVvPI4u2oCblZQLHt_Y9Hl0saEIk)

---

## 🧠 Real-World Relevance

These skills are directly used in:

* Penetration Testing (Reconnaissance & Scanning Phase)
* Security Operations Center (SOC Monitoring)
* Threat Intelligence & Attack Surface Mapping

---

## 🧾 Key Learnings

* Performed structured reconnaissance (passive & active)
* Conducted advanced scanning using Nmap
* Identified vulnerabilities in a test environment
* Analyzed real network traffic and attack patterns
* Implemented basic firewall rules for defense

---

## ⚠️ Disclaimer

This project is for educational purposes only.
All activities were performed in a controlled lab environment.

---

## 🚀 Next Step

➡️ Task 3: Web Application Security

---
