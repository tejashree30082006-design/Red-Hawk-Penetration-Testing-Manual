# 🦅 Red Hawk – Penetration Testing Manual

A comprehensive practical manual documenting the installation, configuration, and usage of the **Red Hawk** open-source web reconnaissance and vulnerability scanning tool, performed on Kali Linux.

---

## 📌 About This Project

This manual was created as part of a hands-on cybersecurity lab exercise to understand the **reconnaissance phase** of penetration testing. Red Hawk automates the process of gathering information about a target website and identifying potential security weaknesses.

> ⚠️ **Ethical Disclaimer:** All tests documented in this manual were performed on intentionally vulnerable or legally authorized targets only. Unauthorized scanning of systems is illegal. This manual is for **educational purposes only**.

---

## 🛠️ Tool Overview

| Property | Details |
|----------|---------|
| **Tool** | Red Hawk v2.0 |
| **Language** | PHP |
| **Platform** | Kali Linux |
| **Purpose** | Web Reconnaissance & Vulnerability Scanning |
| **GitHub** | [Tuhinshubhra/RED_HAWK](https://github.com/Tuhinshubhra/RED_HAWK) |

---

## ⚙️ Requirements

- Kali Linux (or any Linux-based system)
- Git
- PHP
- Active internet connection

---

## 🚀 Installation

```bash
# Clone the repository
git clone https://github.com/Tuhinshubhra/RED_HAWK

# Navigate into the directory
cd RED_HAWK

# Verify files
ls

# Launch the tool
php rhawk.php
```

---

## 🔍 Lab Results – Target: testphp.vulnweb.com

> All scans below were performed on **http://testphp.vulnweb.com**, a deliberately vulnerable website provided by Acunetix for legal penetration testing practice.
> Results are specific to this target — output will vary depending on the website being scanned.

### Basic Recon
- Target IP resolved to **44.228.249.3**
- Web server: **Apache** (banner partially hidden by server config)
- No **CMS** (Content Management System) detected
- No **CloudFlare** protection found
- **robots.txt** file was missing — indicates possible exposure of unlisted directories

### Geo-IP Lookup
- IP **44.228.249.3** located in **Boardman, Oregon, United States**
- ISP and hosting details successfully retrieved

### DNS Lookup
- **A record** resolved to 44.228.249.3
- **TXT record** retrieved (Google site verification token)
- DNS records successfully mapped

### Subnet Calculator
- Network: 44.228.249.3/32
- Subnet Mask: 255.255.255.255
- Host Range: single host (loopback-style allocation)

### Subdomain Scanner
- **No subdomains discovered** for this target
- This is expected for simple hosted apps — results will differ for larger domains

### Crawler
- Successfully loaded **817 URLs** from the target
- Notable paths discovered:
  - `/login.php` → accessible (HTTP 200)
  - `/javascript/` → redirected (HTTP 301)
  - `/.htpasswd` → restricted but confirmed to exist (HTTP 403)
- Admin panel paths were also probed automatically

### MX Lookup
- Mail server records successfully retrieved for the target domain

### Banner Grabbing
- Server did **not** disclose banner information
- This is a server-side security configuration — many modern servers intentionally hide this

### Reverse IP Lookup & CMS Detection
- No other domains found sharing the same IP
- CMS could not be detected — site does not use a standard CMS

### SQL Vulnerability Scanner
- No confirmed SQL injection points automatically detected
- Manual testing or dedicated tools like sqlmap are recommended for deeper analysis

---

## 🔒 Tool Limitations (Fixed – Not Target Dependent)

The following features require **paid third-party API credentials** regardless of the target. These are permanent limitations of the tool, not results:

- **Whois Lookup** — requires a paid Whois API key
- **NMAP Port Scan** (via Red Hawk) — requires API configuration
- **Bloggers View** — requires a paid Moz API key

For Whois and port scanning, standalone tools like `whois` command and direct `nmap` are recommended as free alternatives.

---

## 📂 Repository Structure

```
📁 Red-Hawk-Manual/
│
├── 📄 README.md               ← You are here
└── 📄 MANUAL.pdf              ← Full documented lab manual with screenshots
```

---

## 📚 What I Learned

- How to perform the **reconnaissance phase** of a penetration test
- How tools like Red Hawk automate information gathering
- The difference between **active** and **passive** reconnaissance
- How DNS, Geo-IP, banner grabbing, and subdomain scanning work
- Why some features fail without proper API credentials (real-world tool limitation)
- How to read and interpret scan outputs critically

---

## 🎓 Author

**V Tejashree**
2nd Year B.Tech – Cyber Security
Roll No: 24BYB1176

---

## 🔗 References

- [Red Hawk Official Repository](https://github.com/Tuhinshubhra/RED_HAWK)
- [OWASP Reconnaissance Guide](https://owasp.org/www-project-web-security-testing-guide/)
- Test target: [testphp.vulnweb.com](http://testphp.vulnweb.com) (Acunetix legal practice site)
