[Return to main readme](/readme.md)
# 🔍 Passive Reconnaissance Tools for Cybersecurity

This repository documents essential tools and techniques used for **passive reconnaissance**. These tools help gather information about a target **without directly interacting aggressively** with it.

---

# 🌐 1. Whois

Whois provides registration details about a domain.

---

## 🔹 What It Reveals

* Domain owner (sometimes hidden)
* Registration & expiry date
* Registrar information
* Name servers

---

## 🔹 Command

```bash
whois example.com
```

---

## 🔹 Use Case

* Identify domain ownership
* Check domain age (useful in phishing detection)
* Gather infrastructure clues

---

## 🔹 Key Insight

* Data may be masked (privacy protection)
* Still useful for metadata and infrastructure mapping

---

# 🔎 2. dig (Domain Information Groper)

Advanced DNS lookup tool.

---

## 🔹 Basic Command

```bash
dig example.com
```

---

## 🔹 Query Specific Records

```bash
dig example.com A
dig example.com MX
dig example.com NS
```

---

## 🔹 Reverse Lookup

```bash
dig -x <IP>
```

---

## 🔹 Use Case

* Extract DNS records
* Identify mail servers, subdomains
* Understand domain infrastructure

---

## 🔹 Key Insight

* More powerful and flexible than nslookup
* Essential for DNS analysis

---

# 🌍 3. WhatWeb

Identifies technologies used by a website.

---

## 🔹 Command

```bash
whatweb example.com
```

---

## 🔹 What It Detects

* CMS (WordPress, Joomla)
* Server type
* Frameworks (React, PHP)
* Plugins and libraries

---

## 🔹 Use Case

* Identify attack surface
* Find outdated technologies

---

## 🔹 Key Insight

* Helps plan targeted attacks based on tech stack

---

# 🌐 4. Nslookup

Basic DNS query tool.

---

## 🔹 Command

```bash
nslookup example.com
```

---

## 🔹 Use Case

* Quick DNS resolution
* Check domain-to-IP mapping

---

## 🔹 Key Insight

* Simpler than dig
* Often used for quick checks

---

# 🛡️ 5. wafw00f

Detects Web Application Firewalls (WAF).

---

## 🔹 Command

```bash
wafw00f example.com
```

---

## 🔹 What It Detects

* Cloudflare
* AWS WAF
* ModSecurity
* Other protection systems

---

## 🔹 Use Case

* Understand defenses before testing
* Adjust attack strategy

---

## 🔹 Key Insight

* If WAF is present, direct attacks may fail
* Helps in bypass planning

---

# 📧 6. theHarvester

Collects emails, subdomains, and OSINT data.

---

## 🔹 Command

```bash
theHarvester -d example.com -b google
```

---

## 🔹 Data Sources

* Google
* Bing
* Yahoo
* LinkedIn (limited)

---

## 🔹 Use Case

* Gather email addresses
* Discover subdomains
* Build target profile

---

## 🔹 Key Insight

* Useful for social engineering and footprinting

---

# 🧩 7. Sublist3r

Subdomain enumeration tool.

---

## 🔹 Command

```bash
sublist3r -d example.com
```

---

## 🔹 Use Case

* Discover hidden subdomains
* Expand attack surface

---

## 🔹 Key Insight

* More subdomains = more potential entry points

---

# 🧠 8. Recon-ng

Full-featured reconnaissance framework.

---

## 🔹 Start Tool

```bash
recon-ng
```

---

## 🔹 Key Features

* Modular framework
* Automated data gathering
* API integrations

---

## 🔹 Example Workflow

```bash
marketplace install all
modules load recon/domains-hosts/google_site_web
run
```

---

## 🔹 Use Case

* Automate reconnaissance
* Aggregate multiple data sources

---

## 🔹 Key Insight

* Powerful but requires understanding modules
* Not beginner-friendly without practice

---

# 🕵️ 9. Maltego

Graph-based OSINT tool for visualizing relationships.

---

## 🔹 What It Does

* Maps connections between:

  * Domains
  * Emails
  * IPs
  * People

---

## 🔹 Use Case

* Visual investigation
* Link analysis

---

## 🔹 Key Insight

* Helps see patterns humans miss in raw data

---

# 🔎 10. Google Dorking

Using advanced search queries to find sensitive information using google search engine.

Sites used:
- Google search
- [Google hacking database](https://www.exploit-db.com/google-hacking-database)
- [Dork search](https://dorksearch.com/)

---

## 🔹 Examples

```bash
site:example.com
site:example.com filetype:pdf OR filetype:xlsx
intitle:"index of"
inurl:admin
country: IN

gaming laptops site:www.amazon.com
site:www.amazon.com inurl: admin    //to get admin pages available on google


```

---

## 🔹 Use Case

* Find exposed files
* Locate admin panels
* Discover sensitive data

---

## 🔹 Key Insight

* Most powerful tool is still Google
* Misconfigured systems expose data publicly

---

# 🌍 11. Shodan

Search engine for internet-connected devices that are available on the internet.

site: **https://www.shodan.io/**
---

## 🔹 What It Finds

* Open ports
* Cameras
* Servers
* IoT devices

---

## 🔹 Example Query

```bash
apache country:IN
port:22
```

---

## 🔹 Use Case

* Identify exposed systems
* Find vulnerable services

---

## 🔹 Key Insight

* Shows how much of the internet is exposed
* Real-world attack surface discovery

---

# 🎯 Learning Outcome

After completing this, you should:

* Gather domain and DNS information
* Identify technologies and defenses
* Discover subdomains and emails
* Use search engines for reconnaissance
* Understand real-world exposure of systems

---

# ⚠️ Notes

* Always perform recon on authorized targets only
* Passive recon does not mean zero impact
* Data gathered here is used in later attack phases

---