# Networkwalks – Week 2: Footprinting & Network Scanning

**Cybersecurity & Ethical Hacking Internship | Networkwalks**

| Details | Information |
|---|---|
| **Pentester Name** | Krrish Pravin Mukamad |
| **Program / Batch** | B084 – Networkwalks |
| **Date** | 10 November 2026 |
| **Modules Completed** | W2-PM1 (Multiple Kali Tools), W2-PM5 (Zenmap Scanning) |
| **Target** | networkwalks.com and My Own Local Network |
| **Permission** | Public footprinting and authorised local lab scanning |
| **Phases Covered** | Phase 1: Reconnaissance & Footprinting, Phase 2: Network Scanning |

---

## 1. Liability Disclaimer

All activities documented in this report were performed for educational purposes and within an authorised testing scope. Network scanning was performed on my own lab network. Domain reconnaissance was limited to publicly available information.

Unauthorised access or scanning of systems is prohibited. Always obtain permission before conducting security assessments.

## 2. Introduction

This report documents my Week 2 practical activities during the Cybersecurity & Ethical Hacking Internship at Networkwalks.

The practical covers two major phases of penetration testing:

- **Phase 1 – Footprinting and Reconnaissance:** Gathering publicly available information about the domain `networkwalks.com` using Kali Linux tools.
- **Phase 2 – Network Scanning:** Discovering active hosts on my local network using Nmap and Zenmap.

These activities helped me understand how security professionals gather information about a target before performing further security assessments.

## 3. Tools Used

| Tool | Purpose |
|---|---|
| Kali Linux | Operating system for reconnaissance |
| WHOIS | Domain registration information |
| WhatWeb | Website technology fingerprinting |
| nslookup | DNS lookup and IP resolution |
| curl -I | HTTP response header analysis |
| wafw00f | Web Application Firewall detection |
| dnsrecon | DNS record enumeration |
| Nmap | Network discovery and scanning |
| Zenmap | Graphical interface for Nmap |
| ip route | Identify Kali Linux network configuration |

## 4. Activities Performed

### 4.1 Footprinting & Reconnaissance (W2-PM1)

**Target Domain:** `networkwalks.com`

#### Task 1 – WHOIS Lookup

**Command:**
```bash
whois networkwalks.com
```

WHOIS was used to collect publicly available domain registration information.

**Findings:**

| Information | Result |
|---|---|
| Domain Name | NETWORKWALKS.COM |
| Registrar | GoDaddy.com, LLC |
| Creation Date | 06 November 2019 |
| Updated Date | 12 November 2025 |
| Expiry Date | 06 November 2027 |
| Name Server 1 | NS6135.HOSTGATOR.COM |
| Name Server 2 | NS6136.HOSTGATOR.COM |
| DNSSEC | Unsigned |

**Observation:** WHOIS provides useful information about domain registration, registrar details, domain status and name servers.

**Screenshot:**

![WHOIS Lookup](screenshots/whois.png)

#### Task 2 – WhatWeb

**Command:**
```bash
whatweb networkwalks.com
```

WhatWeb is used to identify technologies and frameworks used by a website.

**Purpose:**
- Identify web server technologies.
- Detect CMS platforms.
- Identify JavaScript libraries.
- Collect publicly exposed website information.

#### Task 3 – nslookup

**Command:**
```bash
nslookup networkwalks.com
```

This command was used to resolve the domain name into its corresponding IP address.

**Observed IP Address:**
```text
192.232.216.135
```

#### Task 4 – curl HTTP Headers

**Command:**
```bash
curl -I https://networkwalks.com
```

This command retrieves HTTP response headers.

**Purpose:**
- Identify HTTP response status.
- Inspect server information.
- Identify publicly exposed response headers.
- Check website response behaviour.

#### Task 5 – WAF Detection

**Command:**
```bash
wafw00f networkwalks.com
```

Wafw00f was used to identify whether a Web Application Firewall protects the website.

The practical notes reported ModSecurity (SpiderLabs) as the detected WAF.

#### Task 6 – DNS Enumeration

**Command:**
```bash
dnsrecon -d networkwalks.com
```

DNSRecon was used to enumerate publicly available DNS records.

**Purpose:**
- Identify A records.
- Identify MX records.
- Identify NS records.
- Identify SOA records.
- Review TXT and SPF records.

---

### 4.2 Network Scanning (W2-PM5)

For this activity, I used Kali Linux to identify my network configuration and perform host discovery on my own local virtual network.

#### Step 1 – Identify Network Configuration

**Command:**
```bash
ip route
```

**My Kali Linux Network Details:**

| Item | Result |
|---|---|
| Operating System | Kali Linux |
| Network Interface | eth1 |
| Kali IP Address | 192.168.226.132 |
| Default Gateway | 192.168.226.2 |
| Network Subnet | 192.168.226.0/24 |

#### Step 2 – Perform Network Scanning

**Command:**
```bash
nmap -sn 192.168.226.0/24
```

The `-sn` option performs host discovery without conducting a port scan.

**Scan Results:**

| Item | Result |
|---|---|
| Network Scanned | 192.168.226.0/24 |
| Scan Type | Ping Scan |
| Total IP Addresses | 256 |
| Live Hosts Discovered | 4 |

**Observation:**

The Nmap scan successfully discovered four active hosts on my local virtual network.

The scan helped me understand how Nmap identifies live devices within a network.

## 5. Risk Analysis

| No. | Finding | Potential Impact | Risk |
|---|---|---|---|
| 1 | Public WHOIS information | Helps identify domain registration details | Low |
| 2 | Website IP address exposed | Reveals the hosting endpoint | Low |
| 3 | Technology fingerprinting | May help identify outdated software | Medium |
| 4 | DNS information exposed | Helps map domain infrastructure | Low |
| 5 | DNSSEC unsigned | DNS responses do not receive DNSSEC validation | Medium |
| 6 | Four live hosts discovered | Requires device identification and inventory verification | Informational |

**Note:** These are preliminary observations and not confirmed vulnerabilities. Further authorised testing would be required to validate security weaknesses.

## 6. Recommendations

1. Regularly update website software and plugins.
2. Review publicly exposed server information.
3. Monitor DNS records and remove unnecessary records.
4. Consider implementing DNSSEC.
5. Maintain an inventory of network-connected devices.
6. Investigate unknown devices on the local network.
7. Perform regular network discovery and security assessments.
8. Always conduct penetration testing within an authorised scope.

## 7. Conclusion

During Week 2 of my Cybersecurity & Ethical Hacking Internship at Networkwalks, I completed practical activities related to footprinting, reconnaissance and network scanning.

I used different Kali Linux tools, including WHOIS, WhatWeb, nslookup, curl, wafw00f and dnsrecon, to understand how publicly available information can be collected from a domain.

I also used the `ip route` command to identify my Kali Linux network configuration and performed network discovery using Nmap.

The Nmap scan successfully identified four live hosts on my local virtual network.

Through these activities, I gained practical knowledge of reconnaissance techniques, DNS enumeration, website fingerprinting and network discovery.

These exercises helped me understand the importance of information gathering and network mapping in cybersecurity and ethical hacking.

## 8. Evidence Collected

### Evidence 1 – WHOIS Lookup

![WHOIS Screenshot](screenshots/whois.png)

### Additional Screenshots

Add your remaining screenshots to the `screenshots` folder and use these links when available:

| Evidence | Screenshot |
|---|---|
| WhatWeb Technology Fingerprinting | `screenshots/whatweb.png` |
| DNS Lookup | `screenshots/nslookup.png` |
| HTTP Response Headers | `screenshots/curl.png` |
| WAF Detection | `screenshots/wafw00f.png` |
| DNS Enumeration | `screenshots/dnsrecon.png` |
| Nmap Network Scan | `screenshots/nmap.png` |
| Network Topology | `screenshots/topology.png` |

---

## 9. Project Information

| Details | Information |
|---|---|
| Program | Cybersecurity & Ethical Hacking Internship |
| Organisation | Networkwalks |
| Week | Week 02 |
| Modules | W2-PM1 and W2-PM5 |
| Author | Krrish Pravin Mukamad |
| GitHub | [My GitHub Profile](https://github.com/KrrishMukadam) |

**End of Report**
