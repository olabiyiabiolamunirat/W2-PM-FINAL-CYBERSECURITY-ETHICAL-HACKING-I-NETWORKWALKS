# W2-PM-FINAL-CYBERSECURITY-ETHICAL-HACKING-I-NETWORKWALKS
*PENETRATION TESTING REPORT*

*Footprinting, Reconnaissance & Network Scanning*

*W2-PM-FINAL | CYBERSECURITY & ETHICAL HACKING | NETWORKWALKS*

Field	Details
Pentester Name	Olabiyi Abiola Munirat
Program	Cybersecurity & Ethical Hacking Internship
Batch	B084 – NETWORKWALKS
Report Date	11 November 2026
Target Domain	http://networkwalks.com
Internal Network Target	My own VirtualBox Host-Only Network
Permission	Authorized educational testing / personally controlled lab
Phases Covered	Phase 1: Reconnaissance & Footprinting; Phase 2: Scanning & Network Discovery

---

1. Liability Disclaimer

This report was prepared for learning and research purposes only.

All tests were carried out on systems I was authorized to test, or on my own personal lab network. I did not attempt any unauthorized access, exploitation, or harmful activity.

The tools and methods described here should only be used within an approved scope. Accessing systems without permission can have legal consequences, and the user is responsible for using this knowledge lawfully.

1. Introduction

This report documents what I did in Week 2 of my Cybersecurity and Ethical Hacking Internship with NETWORKWALKS, Batch B084.

I focused on two stages of penetration testing:

1. *Footprinting and Reconnaissance:* Collecting public information about a target domain using different Kali Linux tools.
2. *Scanning and Network Discovery:* Finding active devices on my own local network using Zenmap.

For the scanning part, I used Kali Linux inside Oracle VirtualBox on my Windows laptop. I first checked my network settings, then ran a Ping Scan with Zenmap. The scan found three live hosts on my Host-Only network.

The aim was to learn how professionals gather information about a target, find active devices, and record possible risks before moving to advanced testing.

1. Tools and Technologies Used

Tool	Purpose
Kali Linux	Environment for reconnaissance
Oracle VirtualBox	Running Kali Linux as a virtual machine
WHOIS	Domain registration information
WhatWeb	Website technology identification
Nslookup	Domain to IP resolution
Curl	Checking HTTP response headers
Wafw00f	Checking for Web Application Firewall
DNSRecon	DNS enumeration
Zenmap	Graphical interface for Nmap
Nmap	Discovering live hosts
Windows CMD	Checking Windows network configuration
Npcap	Supporting packet capture on Windows

1. Activities Performed

4.1 Footprinting and Reconnaissance

Target domain: *networkwalks.com*

*4.1.1 WHOIS*
Command: `whois networkwalks.com`
I checked the registrar, creation and expiry dates, status, and name servers.

*4.1.2 WhatWeb*
Command: `whatweb networkwalks.com`
I checked the CMS, web server, and other technologies the site uses.


*4.1.3 Nslookup*
Command: `nslookup networkwalks.com`
I checked the IP address the domain resolves to.


*4.1.4 Curl*
Command: `curl -I https://networkwalks.com`
I checked the HTTP status, server, and content-type headers.


*4.1.5 Wafw00f*
Command: `wafw00f https://networkwalks.com`
I checked if the site is protected by a WAF.

*4.1.6 DNSRecon*
Command: `dnsrecon -d networkwalks.com`
I checked A, NS, MX, and TXT 

4.2 Network Scanning with Zenmap

*4.2.1 Network Environment*
My setup:
- Kali eth0: 10.0.2.15 (NAT)
- Kali eth1: 192.168.56.102 (Host-Only)
- Windows Host-Only Adapter: 192.168.56.1
- Network: 192.168.56.0/24, Subnet Mask: 255.255.255.0, Range: 192.168.56.1 - 192.168.56.254

*4.2.2 Identifying My IP*
Command on Windows CMD: `ipconfig`
I confirmed my Host-Only adapter was 192.168.56.1 with subnet 255.255.255.0.


*4.2.3 Zenmap Configuration*
Target: `192.168.56.0/24`
Profile: Ping Scan
Command: `nmap -sn 192.168.56.0/24`
The `-sn` option does host discovery only, without port scanning.

*4.2.4 Network Topology*
I opened the Topology tab in Zenmap to view the visual layout of the discovered hosts.
*Evidence:* screenshots/09-network-topology.png

1. Risk Analysis

No.	Finding	Impact	Risk
1	Website technologies visible via WhatWeb	Attackers can identify components to review	Medium
2	Public DNS information	Helps attacker understand infrastructure	Low
3	HTTP headers expose technical info	Aids further fingerprinting	Low
4	WAF information visible	Reveals defensive setup	Low
5	3 live hosts found on local network	Unknown devices need investigation	Medium
6	Shared Host-Only subnet	Misconfiguration could expose lab devices	Low

No exploitation was performed. These are observations only.

1. Recommendations

2. Review publicly exposed technologies regularly.
3. Keep CMS, plugins, and web apps updated.
4. Configure secure HTTP headers and remove unnecessary ones.
5. Review DNS records periodically.
6. Configure and monitor WAF properly.
7. Do regular network discovery to find new devices.
8. Investigate any unexpected device found.
9. Keep updated network documentation.
10. Restrict network access to authorized devices only.
11. Always test within an approved scope.

12. Conclusion

In Week 2, I learned how to use WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon for footprinting, and Zenmap for network discovery.

I confirmed my Host-Only network as 192.168.56.0/24 and discovered three live hosts using `nmap -sn 192.168.56.0/24`.

I also learned the difference between NAT and Host-Only networking in VirtualBox, and how to read Zenmap topology.

Most importantly, I learned that reconnaissance is the foundation of penetration testing — you must understand the target environment before any further assessment.

This practical improved my confidence in using Kali Linux, Windows networking tools, and Zenmap for authorized testing.
*PROGRAM:* Cybersecurity & Ethical Hacking Internship
*ORGANIZATION:* NETWORKWALKS
*BATCH:* B084
*REPORT:* W2-PM-FINAL
*AUTHOR:* Olabiyi Abiola Munirat
