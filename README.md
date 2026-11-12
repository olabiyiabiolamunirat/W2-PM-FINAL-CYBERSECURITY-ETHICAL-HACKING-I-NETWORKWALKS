# W2-PM-FINAL-CYBERSECURITY-ETHICAL-HACKING-I-NETWORKWALKS

PENETRATION TESTING ASSESSMENT REPORT

Phase 1 & 2: Reconnaissance, Footprinting, and Network Discovery
Document ID: W2-PM-FINAL | Track: Cybersecurity & Ethical Hacking | Organization: NETWORKWALKS

Assessment Attribute	Information
Security Analyst	OLABIYI ABIOLA MUNIRAT
Internship Track	Cybersecurity & Ethical Hacking Internship
Cohort / Batch	Batch B084 – NETWORKWALKS
Submission Date	11 November 2026
Lab Modules	W2-PM1 (Kali Linux Recon Suite) & W2-PM5 (Zenmap Discovery)
External Target	http://networkwalks.com
Internal Scope	Local VirtualBox Host-Only Virtual Network
Authorization	Approved educational lab environment & self-managed virtual network
Testing Stages	Passive/Active Footprinting & Local Host Enumeration


1. Authorization & Scope Disclaimer

This assessment was conducted strictly for academic and skill-development purposes as part of my internship training. Every test documented herein was performed either against an authorized training domain or within a private virtual network under my direct control. No intrusive exploitation, service disruption, or unauthorized access was attempted. All methodologies outlined in this document should only be applied within legally sanctioned engagements.

2. Executive Summary & Objectives

This document outlines the practical lab exercises I completed during the second week of my NETWORKWALKS Cybersecurity and Ethical Hacking Internship (Batch B084). The objective was to execute the foundational stages of a structured penetration test:
• Information Gathering (Footprinting): Collecting publicly accessible infrastructure, DNS, and web technology data for a target domain using command-line reconnaissance tools in Kali Linux.
• Host Discovery (Scanning): Mapping active endpoints across an isolated internal subnet using Zenmap.

For the internal network phase, I configured a lab environment consisting of a Windows host operating system and a Kali Linux virtual machine hosted in Oracle VirtualBox. After verifying the local IP addressing scheme and subnet boundaries, I executed a host discovery sweep via Zenmap, which successfully identified three active devices on the Host-Only segment.

3. Testing Environment & Toolset

• Operating Environment: Kali Linux deployed inside Oracle VirtualBox alongside a Windows host OS.
• Domain & DNS Enumeration: WHOIS (registration records), Nslookup (IP resolution), and DNSRecon (DNS record mapping).
• Web & Application Profiling: WhatWeb (CMS and technology fingerprinting), Curl (HTTP header inspection), and Wafw00f (Web Application Firewall detection).
• Network Mapping: Zenmap / Nmap (active host discovery) and Windows CMD (ipconfig interface verification).

4. Technical Execution & Findings

4.1 External Footprinting & Reconnaissance

• Target URL: http://networkwalks.com / https://networkwalks.com
4.1.1 Domain Registration Lookup (WHOIS)

4.2 Internal Network Discovery (Zenmap)

Before initiating the scan, I inspected the network adapter properties on my host and guest machines to define the exact target range
5. Troubleshooting & Lessons Learned
• Working through these labs presented a few technical hurdles that sharpened my attention to detail:
• Specifying URL Protocols in Wafw00f: My initial scan failed because I omitted the https:// prefix from the target domain. Running the command with the full protocol (wafw00f https://networkwalks.com) resolved the issue and successfully identified a ModSecurity Web Application Firewall.
• Interpreting HTTP Redirections in WhatWeb: Seeing two separate output blocks in WhatWeb was initially confusing. Closer inspection revealed that the server automatically redirects standard HTTP traffic (301 Moved Permanently) to an encrypted HTTPS endpoint (200 OK).
• Correlating Zenmap Results with Host Interfaces: Reading the raw scan output at first felt overwhelming. By switching to Zenmap’s Topology view and cross-referencing the discovered IP addresses against my Windows ipconfig output, I accurately mapped each live host on my virtual network.

6. Preliminary Risk Observations

The findings gathered during this phase represent informational observations rather than verified security flaws, as no active exploitation was conducted. However, publicly visible details—such as web server headers, underlying technologies, and DNS records—can assist an adversary in profiling an organization's attack surface if left unhardened. The presence of a Web Application Firewall provides a strong defensive layer, though proper rule tuning remains essential.

7. Security Hardening Recommendations

To minimize information exposure and strengthen network visibility, the following defensive practices are recommended:
• Minimize Banner & Header Exposure: Configure web servers to suppress detailed software version numbers and enforce strict HTTP security headers (such as HSTS and X-Frame-Options).
• Maintain Patch Hygiene: Conduct routine software and CMS audits to ensure all public-facing components run supported, patched versions.
• Harden DNS & WAF Controls: Periodically review public DNS records to remove stale entries, and continuously monitor ModSecurity WAF logs for anomalous traffic patterns.
• Enforce Internal Network Visibility: Maintain up-to-date asset inventories, restrict unauthorized network access, and routinely scan internal subnets to detect rogue devices.

8. Conclusion

Completing the Week 2 practical labs demonstrated how structured reconnaissance and network scanning establish the groundwork for any security assessment.
By combining passive domain profiling with active local host discovery, I gained hand’s on experience in accurately mapping an environment's digital footprint before moving into deeper vulnerability analysis.
