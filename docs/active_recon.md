[Return to main readme](/readme.md)

# 🎯 Active Reconnaissance: Ping Sweep & Banner Grabbing

This repository documents core **active reconnaissance techniques** used in cybersecurity. Unlike passive recon, active recon involves **direct interaction with the target system**, making it more powerful but also more detectable.

---

# ⚡ What is Active Recon?

Active reconnaissance involves sending requests directly to target systems to gather information.

---

## 🔹 Key Characteristics

* Direct interaction with target
* Faster and more accurate data
* Can be detected by firewalls and IDS/IPS
* Requires proper authorization

---

# 📡 1. Ping Sweep

Ping sweep is used to discover **live hosts** in a network.

---

## 🔹 What It Does

* Sends ICMP echo requests (`ping`)
* Identifies which systems are active (alive)

---

## 🔹 Basic Concept

```bash id="ps1"
192.168.1.1   → Alive
192.168.1.2   → No response
192.168.1.3   → Alive
```

---

## 🔹 Using Nmap for Ping Sweep

```bash id="ps2"
nmap -sn 192.168.1.0/24
```

---

## 🔹 Explanation

* `-sn` → Ping scan (no port scan)
* Scans entire subnet
* Lists live hosts

---

## 🔹 Example Output

```bash id="ps3"
Nmap scan report for 192.168.1.1
Host is up

Nmap scan report for 192.168.1.5
Host is up
```

---

## 🔹 Use Cases

* Identify active machines in network
* Build target list for further scanning
* Network mapping

---

## 🔹 Limitations

* ICMP may be blocked
* Some hosts may not respond to ping
* False negatives possible

---

## 🔹 Key Insight

* No response ≠ host is down
* It may just be hiding

---

# 🛰️ 2. Banner Grabbing

Banner grabbing is used to extract **service information** from a target system.

---

## 🔹 What is a Banner?

A banner is a message sent by a service that reveals:

* Software name
* Version
* Sometimes OS details

---

## 🔹 Why It Matters

* Helps identify vulnerabilities
* Reveals outdated services
* Enables targeted attacks

---

## 🔹 Method 1: Using Netcat

```bash id="bg1"
nc 192.168.1.1 80
```

---

### Example Output

```bash id="bg2"
HTTP/1.1 200 OK
Server: Apache/2.4.41 (Ubuntu)
```

---

## 🔹 Method 2: Using Nmap

```bash id="bg3"
nmap -sV 192.168.1.1
```

---

### Explanation

* `-sV` → Service version detection
* Attempts to identify service and version

---

## 🔹 Method 3: Using Telnet

```bash id="bg4"
telnet 192.168.1.1 80
```

---

## 🔹 Use Cases

* Identify web server versions
* Detect running services
* Find outdated software

---

## 🔹 Real Example

```bash id="bg5"
Server: Apache/2.2.8
```

👉 This tells:

* Server is Apache
* Version is old → potential vulnerability

---

## 🔹 Key Insight

* More information = more attack opportunities
* Even small details can be critical

---

# 🎯 Learning Outcome

After completing this, you should:

* Identify active hosts in a network
* Understand limitations of ping sweep
* Extract service and version information
* Recognize potential vulnerabilities from banners

---

# ⚠️ Notes

* Active recon can trigger security alerts
* Always scan authorized systems only
* Some systems intentionally hide banners
* Lack of response does not mean absence

---
