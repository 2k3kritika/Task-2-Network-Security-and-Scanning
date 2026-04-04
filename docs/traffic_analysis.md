[Return to main readme](/readme.md)

# 📡 Packet Analysis with Wireshark

This repository documents practical packet analysis using Wireshark, including capturing protocols, filtering sensitive data, and analyzing network attacks.

---

# 🔍 1. What is Packet Analysis?

Packet analysis involves capturing and inspecting network traffic to understand how data flows across a network.

---

## 🔹 Why It Matters

* Debug network issues
* Analyze protocols (HTTP, DNS, FTP)
* Detect attacks and anomalies
* Extract sensitive data (if unencrypted)

---

# ⚙️ 2. Capturing Traffic in Wireshark

---

## 🔹 Steps

1. Open Wireshark
2. Select active network interface (Wi-Fi/Ethernet)
3. Click **Start Capture**
4. Generate traffic (browse websites, run commands)

---

## 🔹 Stop Capture

* Click the red stop button

---

# 🌐 3. Capture & Analyze Protocols

---

## 🔹 HTTP Traffic

### Filter:

```bash id="httpf1"
http
```

---

### What to Observe

* Request methods (GET, POST)
* URLs accessed
* Headers (User-Agent, Host)

---

### Key Insight

* HTTP is **unencrypted**
* Data can be read directly

---

## 🔹 DNS Traffic

### Filter:

```bash id="dnsf1"
dns
```

---

### What to Observe

* Domain queries
* Response IP addresses

---

### Example:

```bash id="dnsf2"
Query: google.com
Response: 142.250.x.x
```

---

### Key Insight

* Shows what domains user is accessing

---

## 🔹 FTP Traffic

### Filter:

```bash id="ftpf1"
ftp
```

---

### What to Observe

* Commands (USER, PASS)
* File transfers

---

### Key Insight

* FTP is **not encrypted**
* Credentials are visible in plaintext

---

# 🔑 4. Extract Credentials from FTP Traffic

---

## 🔹 Filter for FTP Login

```bash id="cred1"
ftp.request.command == "USER" || ftp.request.command == "PASS"
```

---

## 🔹 Example Output

```bash id="cred2"
USER admin
PASS password123
```

---

## 🔹 Analysis

* Username and password visible
* Major security risk

---

## 🔹 Key Insight

* Unencrypted protocols expose sensitive data
* Reason why secure alternatives (SFTP, FTPS) exist

---

# ⚡ 5. Analyze SYN Flood Attack

A SYN flood is a type of Denial-of-Service (DoS) attack.

---

## 🔹 What Happens

* Attacker sends many SYN requests
* Server responds with SYN-ACK
* Attacker does not complete handshake
* Server resources get exhausted

---

## 🔹 Simulate Attack using hping3

```bash id="syn1"
sudo hping3 -S --flood -p 80 <target-ip>
```

---

## 🔹 Explanation

* `-S` → SYN flag
* `--flood` → send packets rapidly
* `-p 80` → target port

---

## 🔹 Wireshark Filter

```bash id="syn2"
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

---

## 🔹 What to Observe

* Large number of SYN packets
* No corresponding ACK responses
* Traffic spike

---

## 🔹 Example Behavior

* Continuous SYN packets from attacker IP
* Server unable to handle requests

---

## 🔹 Key Insight

* Indicates possible DoS attack
* Helps in intrusion detection

---

# 🎯 Learning Outcome

After completing this, you should:

* Capture and analyze network traffic
* Understand protocol behavior (HTTP, DNS, FTP)
* Extract sensitive data from unencrypted traffic
* Identify SYN flood attack patterns

---

# ⚠️ Notes

* Only capture traffic in authorized environments
* Packet capture may expose sensitive data
* Encrypted traffic (HTTPS) cannot be read directly
* SYN flood simulation should be done in a controlled lab

---
