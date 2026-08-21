<div align="center">

# 🔐 Footprinting & Network Scanning

**Week 2 practical activities in reconnaissance, footprinting, and local network scanning**

</div>

<p align="center">
  <img src="https://img.shields.io/badge/Module-W2--PM1-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Module-W2--PM5-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Footprinting-Reconnaissance-C00000?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Network%20Scanning-Zenmap-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Furahia%20Mwampamba-C00000?style=flat-square" />
</p>

---

# Penetration Testing Report — Footprinting & Network Scanning Phases

**Program:** Cybersecurity Program at Networkwalks (B082-Networkwalks)
**Week:** 02
**Module:** W2-PM-FINAL
**Author:** Furahia Mwampamba
**Date:** 21 August 2026

## Overview

This repository documents Week 2 of my **Cybersecurity & Ethical Hacking internship at Networkwalks**. It covers two practical activities:

* **W2-PM1** — Footprinting and reconnaissance of `networkwalks.com` using multiple Kali Linux tools
* **W2-PM5** — Local network scanning and host discovery using Zenmap

Together, these activities helped me understand how information can be collected about a publicly accessible website and how active devices can be identified within a local network.

> **Scope & Permission:** The footprinting activity was performed on the `networkwalks.com` domain as part of the assigned educational cybersecurity lab, while the network scanning activity was performed only on my own local network. No exploitation or vulnerability validation was performed. The activities focused on information gathering, reconnaissance, and host discovery.

## Tools Used

| Tool              | Purpose                                                                                |
| ----------------- | -------------------------------------------------------------------------------------- |
| Kali Linux        | Operating system used for the footprinting and reconnaissance activities               |
| WHOIS             | Obtain publicly available domain registration information and name server details      |
| WhatWeb           | Identify web technologies, CMS, plugins, server information and other exposed metadata |
| Nslookup          | Resolve the domain name to its IP address using DNS                                    |
| Curl              | Inspect HTTP response headers and identify exposed web application information         |
| Wafw00f           | Identify whether a Web Application Firewall is protecting the website                  |
| DNSRecon          | Enumerate DNS records such as NS, MX, A, TXT and SRV records                           |
| Zenmap (Nmap GUI) | Discover active hosts on the local network and collect IP and MAC address information  |
| Windows CMD       | Check local network configuration and identify IP and MAC address information          |

## Steps Followed

### Phase 1: Footprinting & Reconnaissance (`networkwalks.com`)

#### 1. WHOIS Lookup

```bash
whois networkwalks.com
```

The WHOIS lookup provided publicly available domain registration information. The results showed that the domain was registered through **GoDaddy.com, LLC**, with a creation date of **6 November 2019** and a registration expiry date of **6 November 2027**. The output also identified **NS6135.HOSTGATOR.COM** and **NS6136.HOSTGATOR.COM** as name servers and showed that DNSSEC was unsigned.

#### 2. WhatWeb Scan

```bash
whatweb networkwalks.com
```

WhatWeb identified several technologies used by the website. The results showed **WordPress 7.1** and **WordPress Download Manager 3.3.58**, together with **Apache, Bootstrap 7.1, jQuery 3.7.1, Google Tag Manager**, and other exposed website information. The website was also associated with the IP address **192.232.216.135** and displayed the title **Networkwalks Academy**.

#### 3. DNS Resolution with Nslookup

```bash
nslookup networkwalks.com
```

The domain was successfully resolved to the IP address **192.232.216.135**. The DNS query used **8.8.8.8** as the DNS server.

#### 4. HTTP Header Inspection with Curl

```bash
curl -I https://networkwalks.com
```

The command returned an **HTTP/2 200** response and identified **Apache** as the web server. The response headers also revealed the WordPress REST API endpoints **`/wp-json/`** and **`/wp-json/wp/v2/pages/53`**, providing additional information about the web application.

#### 5. WAF Detection with Wafw00f

```bash
wafw00f networkwalks.com
```

Wafw00f identified **ModSecurity (SpiderLabs)** as the Web Application Firewall protecting the website.

#### 6. DNS Enumeration with DNSRecon

```bash
dnsrecon -d networkwalks.com
```

DNSRecon identified several DNS records associated with the domain. These included **NS records** for HostGator, an **MX record** for `mail.networkwalks.com`, an **A record** pointing to **192.232.216.135**, **TXT records** containing Google site verification and SPF information, and several **SRV records** associated with email autodiscovery.

### Phase 2: Network Scanning with Zenmap (Local LAN)

1. I used Windows `ipconfig` to identify my local IP address and subnet configuration.
2. I opened **Zenmap** and entered my local subnet as the target.
3. I performed a **Ping Scan** to identify active devices on the network.
4. I recorded the discovered hosts together with their IP and MAC address information.
5. I used the **Topology** tab in Zenmap to visualize the discovered network devices and created a network topology based on the scan results.

> **Note:** The IP addresses, number of hosts, and network topology in this section should match the actual results obtained from my local network scan.


<img width="680" height="693" alt="WK2-PM1- Results of whois" src="https://github.com/user-attachments/assets/a11ae8fb-81fc-43a8-9755-37f88c54bb87" />

<img width="652" height="414" alt="WK2-PM1-Results of whatweb" src="https://github.com/user-attachments/assets/b8fcbe8a-06f9-448d-a07b-136f0ffa92f4" />

<img width="276" height="144" alt="WK2-PM1-Results of nslookup" src="https://github.com/user-attachments/assets/9b56f4d9-ad19-479b-a60b-368d73615b40" />

<img width="666" height="339" alt="WK2-PM1-Results of curl-I https" src="https://github.com/user-attachments/assets/04e1c40d-30d2-4122-8d62-01cc8dff1f6e" />

<img width="658" height="380" alt="WK2-PM1 Results of wafw00f" src="https://github.com/user-attachments/assets/0f80e9ad-784c-44fd-8403-8b859b4dd293" />

<img width="653" height="514" alt="WK2-PM1- Results of dnsrecon" src="https://github.com/user-attachments/assets/12a4953d-a1c2-4e62-b2cb-f57620695aec" />







## Key Findings & Risk Summary

| # | Finding                                                                                                                 | Risk Level |
| - | ----------------------------------------------------------------------------------------------------------------------- | ---------- |
| 1 | Web technologies and software versions were identifiable, including WordPress 7.1 and WordPress Download Manager 3.3.58 | Medium     |
| 2 | The public IP address of the website was identifiable through DNS resolution                                            | Low        |
| 3 | HTTP response headers and WordPress REST API endpoints were exposed                                                     | Low        |
| 4 | The website's WAF technology, ModSecurity (SpiderLabs), was identifiable                                                | Low        |
| 5 | DNS infrastructure, including NS, MX, TXT and SRV records, was publicly discoverable                                    | Medium     |
| 6 | Multiple active devices were identified during local network scanning                                                   | Medium     |

> **Important:** These findings represent observations obtained during reconnaissance and network scanning. They do **not** confirm that the identified systems contain exploitable vulnerabilities. Further authorized security testing would be required to determine whether any actual vulnerabilities exist.

## Recommendations

Based on the findings obtained during the activities, the following security improvements are recommended:

1. **Limit unnecessary information exposure —** publicly available information about the web server, CMS, plugins and other technologies should be reviewed regularly to ensure that unnecessary technical details are not exposed.

2. **Keep web technologies updated —** WordPress, WordPress Download Manager, Apache and other identified technologies should be kept up to date and checked against relevant security advisories.

3. **Review exposed web endpoints —** the WordPress REST API endpoints identified during the Curl test should be reviewed to ensure that they do not expose unnecessary or sensitive information.

4. **Review HTTP response information —** HTTP headers should be checked regularly to identify and reduce unnecessary technical information being revealed to external users.

5. **Maintain secure DNS configuration —** DNS records should be reviewed periodically to ensure that they are accurate, necessary and do not expose unnecessary services.

6. **Maintain effective WAF protection —** the identified ModSecurity (SpiderLabs) WAF should remain enabled, properly configured and monitored to provide an additional layer of protection.

7. **Monitor the local network —** regular network discovery should be performed to maintain awareness of devices connected to the network.

8. **Investigate unexpected devices —** any unfamiliar or unauthorized device identified during network scanning should be investigated and verified.

9. **Perform security testing with authorization —** reconnaissance, scanning and further vulnerability testing should only be performed on systems and networks where appropriate permission has been provided.

## Repository Contents

```text
├── README.md
├── Penetration_Testing_Report.docx
└── evidence/
    ├── whois/
    ├── whatweb/
    ├── nslookup/
    ├── curl/
    ├── wafw00f/
    ├── dnsrecon/
    └── zenmap/
```

The `evidence/` directory contains screenshots and supporting evidence from the individual activities.

## Disclaimer

These activities were performed as part of an authorized educational cybersecurity internship and on my own local network. No exploitation or unauthorized access was attempted. The purpose of the activities was to gain practical experience in footprinting, reconnaissance, network scanning, and security documentation.

---

*Cybersecurity Program at Networkwalks | Week 02*
