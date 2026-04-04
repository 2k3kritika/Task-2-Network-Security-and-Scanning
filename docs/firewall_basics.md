[Return to main readme](/readme.md)

# 🔥 Firewall Configuration with iptables

This repository documents the basics of firewall configuration using `iptables`, including creating rules to allow/deny traffic and demonstrating how to block a port scan attempt.

---

# 🧠 1. What is iptables?

`iptables` is a command-line firewall utility in Linux used to control incoming and outgoing network traffic based on predefined rules.

---

## 🔹 Why It Matters

* Controls access to system ports
* Protects against unauthorized connections
* Helps mitigate network attacks (e.g., port scanning)

---

## 🔹 Key Concepts

* **Rule** → Instruction to allow/deny traffic
* **Chain** → Set of rules (INPUT, OUTPUT, FORWARD)
* **Table** → Type of rules (filter, nat, etc.)

---

## 🔹 Common Chains

| Chain   | Purpose                        |
| ------- | ------------------------------ |
| INPUT   | Incoming traffic               |
| OUTPUT  | Outgoing traffic               |
| FORWARD | Traffic passing through system |

---

# ⚙️ 2. Basic iptables Rules

---

## 🔹 View Current Rules

```bash id="ipt1"
sudo iptables -L -n -v
```

---

## 🔹 Allow a Specific Port (Example: SSH - Port 22)

```bash id="ipt2"
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

---

## 🔹 Allow HTTP (Port 80)

```bash id="ipt3"
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
```

---

## 🔹 Deny a Specific Port

```bash id="ipt4"
sudo iptables -A INPUT -p tcp --dport 23 -j DROP
```

---

## 🔹 Allow Established Connections

```bash id="ipt5"
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

---

## 🔹 Set Default Policy (Deny All)

```bash id="ipt6"
sudo iptables -P INPUT DROP
```

---

## 🔹 Allow Localhost

```bash id="ipt7"
sudo iptables -A INPUT -i lo -j ACCEPT
```

---

# 📡 3. Example Rule Set (Basic Firewall)

```bash id="ipt8"
# Allow localhost
iptables -A INPUT -i lo -j ACCEPT

# Allow established connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow SSH
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Allow HTTP
iptables -A INPUT -p tcp --dport 80 -j ACCEPT

# Drop everything else
iptables -P INPUT DROP
```

---

## 🔹 Explanation

* Only essential ports are open
* All other incoming traffic is blocked
* System becomes less exposed to attacks

---

# 🚫 4. Blocking a Port Scan Attempt

Port scans (e.g., using Nmap) try to identify open ports on a system.

---

## 🔹 Detect Suspicious Traffic Pattern

Example: Multiple connection attempts in short time

---

## 🔹 Limit Connection Rate

```bash id="ipt9"
sudo iptables -A INPUT -p tcp --syn -m limit --limit 1/s -j ACCEPT
```

---

## 🔹 Drop Excess Requests

```bash id="ipt10"
sudo iptables -A INPUT -p tcp --syn -j DROP
```

---

## 🔹 Block Specific IP (Manual)

```bash id="ipt11"
sudo iptables -A INPUT -s <attacker-ip> -j DROP
```

---

## 🔹 Effect

* Slows down scanning attempts
* Blocks aggressive scanners
* Reduces attack surface visibility

---

# 🧪 5. Demonstration: Blocking Nmap Scan

---

## 🔹 Step 1: Run Scan (Attacker Machine)

```bash id="ipt12"
nmap -sS <target-ip>
```

---

## 🔹 Step 2: Apply Firewall Rules (Target)

* Enable restrictive rules
* Limit incoming connections

---

## 🔹 Step 3: Observe Results

### Before Firewall:

* Open ports visible
* Scan completes quickly

---

### After Firewall:

* Ports appear filtered
* Scan slows down or fails
* Reduced information leakage

---

## 🔹 Key Insight

* Firewall does not just block traffic
* It controls **what information is exposed**

---

# 🎯 6. Learning Outcome

After completing this, you should:

* Understand how iptables works
* Create rules to allow/deny traffic
* Configure a basic firewall
* Limit and block port scanning attempts
* Reduce system visibility to attackers

---

# ⚠️ Notes

* Incorrect rules can block your own access (especially SSH)
* Always test in a controlled environment
* Rules are not persistent unless saved
* Modern systems may use `ufw` or `nftables` instead

---
