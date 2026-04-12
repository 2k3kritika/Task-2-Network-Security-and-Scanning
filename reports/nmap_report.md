# 🛡️ Network Scan Report (Nmap Analysis)

## 📌 Scan Details

* **Tool Used:** Nmap
* **Scan Type:** TCP SYN Scan (-sS), Service Version Detection (-sV), OS Detection (-O)
* **Target Network:** 192.168.118.0/24
* **Date:** 12 April 2026

---

## 🌐 Network Overview

The scan identified **3 active hosts** within the network:

| IP Address      | Status | Notes                                   |
| --------------- | ------ | --------------------------------------- |
| 192.168.118.1   | Up     | No open ports (filtered)                |
| 192.168.118.132 | Up     | Multiple open ports (highly vulnerable) |
| 192.168.118.254 | Up     | No open ports (filtered)                |

---

## 🖥️ Host Analysis

### 🔹 Host: 192.168.118.1

* **Status:** Active
* **Ports:** All filtered (no visible services)
* **MAC Address:** VMware
* **Observation:**

  * Likely a gateway or firewall device
  * Strong filtering rules in place
  * Minimal attack surface

---

### 🔹 Host: 192.168.118.132 (Critical Target)

* **Status:** Active
* **OS:** Linux Kernel 2.6.x (Outdated)
* **Device Type:** General-purpose system
* **Hostname:** metasploitable.localdomain

#### 🚨 Open Ports & Services

| Port    | Service    | Version       | Risk                      |
| ------- | ---------- | ------------- | ------------------------- |
| 21      | FTP        | vsftpd 2.3.4  | Backdoor vulnerability    |
| 22      | SSH        | OpenSSH 4.7   | Weak/old version          |
| 23      | Telnet     | telnetd       | Insecure (plaintext auth) |
| 25      | SMTP       | Postfix       | Possible mail abuse       |
| 53      | DNS        | BIND 9.4.2    | Exploitable version       |
| 80      | HTTP       | Apache 2.2.8  | Known vulnerabilities     |
| 111     | RPCBind    | v2            | Enumeration risk          |
| 139/445 | SMB        | Samba         | Misconfig + exploits      |
| 512-514 | R-services | rsh/rlogin    | Highly insecure           |
| 1099    | Java RMI   | GNU Classpath | Remote execution risk     |
| 1524    | Bind Shell | Root shell    | 🚨 Critical backdoor      |
| 2049    | NFS        | v2-4          | File system exposure      |
| 2121    | FTP        | ProFTPD 1.3.1 | Vulnerable                |
| 3306    | MySQL      | 5.0.51        | Weak credentials likely   |
| 5432    | PostgreSQL | 8.3.x         | Outdated                  |
| 5900    | VNC        | v3.3          | Weak/no auth possible     |
| 6000    | X11        | -             | GUI exposure              |
| 6667    | IRC        | UnrealIRCd    | Backdoor history          |
| 8009    | AJP        | Apache JServ  | Ghostcat vuln             |
| 8180    | HTTP       | Tomcat        | Misconfig risk            |

#### ⚠️ Key Findings

* System is **intentionally vulnerable (Metasploitable)**
* Presence of:

  * **Backdoors (port 1524)**
  * **Insecure services (Telnet, RSH)**
  * **Outdated software across all services**
* Multiple **remote exploitation paths available**

#### 🔥 Risk Level: CRITICAL

This host is highly exploitable and should **never exist in a production environment**.

---

### 🔹 Host: 192.168.118.254

* **Status:** Active
* **Ports:** All filtered
* **MAC Address:** VMware
* **Observation:**

  * Likely another network device (router/firewall)
  * No exposed services

---

## 📊 Security Assessment

### ✅ Strengths

* Network perimeter devices (192.168.118.1 & .254) are well-filtered
* Limited exposure from gateway-level systems

### ❌ Weaknesses

* One host (192.168.118.132) is:

  * Completely exposed
  * Running outdated services
  * Hosting multiple insecure protocols
  * Containing known backdoors

---

## 🚧 Recommendations

### 🔴 Immediate Actions

* Isolate or shut down host **192.168.118.132**
* Block unnecessary ports using firewall rules
* Remove insecure services:

  * Telnet
  * RSH
  * Open bind shells

### 🟡 Medium-Term Fixes

* Upgrade all outdated services and OS versions
* Enforce strong authentication (SSH keys, DB passwords)
* Disable unused services

### 🟢 Long-Term Strategy

* Implement network segmentation
* Deploy IDS/IPS monitoring
* Conduct regular vulnerability scans
* Apply patch management policies

---

## 📌 Conclusion

The network contains a **highly vulnerable machine (192.168.118.132)** with multiple critical security flaws, making it an easy target for attackers. Immediate remediation is required to prevent full system compromise and lateral movement within the network.

---
