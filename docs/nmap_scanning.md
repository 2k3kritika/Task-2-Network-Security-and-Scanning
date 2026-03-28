[Return to main readme](/readme.md)

# 🔍 Nmap Scanning Techniques & Reporting

This repository documents essential **Nmap scanning techniques** used in cybersecurity for network discovery, service identification, and OS detection. It also includes a sample scan report for real-world understanding.

---

# 🌐 What is Nmap?

Nmap (Network Mapper) is a powerful tool used to:

* Discover hosts on a network
* Identify open ports
* Detect services and versions
* Identify operating systems

---

# ⚡ 1. TCP SYN Scan (-sS)

Also called **Stealth Scan**.

---

## 🔹 Command

```bash id="tcp1"
nmap -sS <target-ip>
```

---

## 🔹 How It Works

* Sends SYN packet
* Receives SYN-ACK → port is open
* Sends RST → avoids full connection

---

## 🔹 Why Use It?

* Faster than full TCP scan
* Less detectable (but not invisible)

---

## 🔹 Key Insight

* Commonly used in real-world reconnaissance

---

# 📡 2. UDP Scan (-sU)

Used to detect UDP services.

---

## 🔹 Command

```bash id="udp1"
nmap -sU <target-ip>
```

---

## 🔹 Common UDP Ports

* 53 → DNS
* 67/68 → DHCP
* 123 → NTP

---

## 🔹 Challenges

* Slower than TCP scan
* No response ≠ closed port

---

## 🔹 Key Insight

* UDP scanning is unreliable but important

---

# 🔍 3. Service Version Detection (-sV)

Identifies service and version running on open ports.

---

## 🔹 Command

```bash id="sv1"
nmap -sV <target-ip>
```

---

## 🔹 Example Output

```bash id="sv2"
80/tcp open  http    Apache httpd 2.4.41
22/tcp open  ssh     OpenSSH 7.6p1
```

---

## 🔹 Why It Matters

* Helps identify vulnerabilities
* Enables targeted attacks

---

# 🧠 4. OS Detection (-O)

Attempts to detect the operating system.

---

## 🔹 Command

```bash id="os1"
nmap -O <target-ip>
```

---

## 🔹 Example Output

```bash id="os2"
OS: Linux 3.x or 4.x
```

---

## 🔹 How It Works

* Analyzes TCP/IP stack behavior
* Compares with known signatures

---

## 🔹 Limitations

* May not always be accurate
* Requires open/filtered ports

---

# 🧪 Combined Scan (Recommended)

```bash id="combo1"
nmap -sS -sV -O <target-ip>
```

---

## 🔹 What It Does

* Performs stealth scan
* Detects services and versions
* Attempts OS detection

---

# 📊 5. Sample Scan Report

## 🔹 Target Information

* Target IP: 192.168.1.10
* Scan Type: TCP SYN Scan + Service Detection + OS Detection

---

## 🔹 Scan Command Used

```bash id="rep1"
nmap -sS -sV -O 192.168.1.10
```

---

## 🔹 Open Ports & Services

| Port     | State | Service | Version       |
| -------- | ----- | ------- | ------------- |
| 22/tcp   | open  | SSH     | OpenSSH 7.6   |
| 80/tcp   | open  | HTTP    | Apache 2.4.41 |
| 443/tcp  | open  | HTTPS   | OpenSSL       |
| 3306/tcp | open  | MySQL   | MySQL 5.7     |

---

## 🔹 OS Detection

* Detected OS: Linux (Kernel 3.x – 4.x)
* Confidence: Medium

---

## 🔹 Analysis

* SSH service is exposed → potential brute-force target
* Apache version may have known vulnerabilities
* MySQL exposed → high-risk if not secured
* HTTPS present → encryption enabled

---

## 🔹 Risk Assessment

| Service | Risk Level | Reason                    |
| ------- | ---------- | ------------------------- |
| SSH     | Medium     | Common attack vector      |
| HTTP    | Medium     | Possible outdated version |
| HTTPS   | Low        | Secure communication      |
| MySQL   | High       | Database exposure         |

---

## 🔹 Recommendations

* Restrict SSH access (use firewall or key-based auth)
* Update Apache to latest version
* Secure MySQL (bind to localhost or use authentication)
* Perform vulnerability scan on detected services

---

# 🎯 Learning Outcome

After completing this, you should:

* Perform TCP and UDP scans
* Identify services and versions
* Detect operating systems
* Analyze scan results
* Create structured scan reports

---

# ⚠️ Notes

* Always scan authorized targets only
* Some scans may trigger security alerts
* Results may vary due to firewalls or filtering

---
