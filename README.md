
# Cybersecurity Incident Response Portfolio

**Gabriela Roa**  
B.A. Computer Science (AI & Cybersecurity)

## Overview
This repository contains a collection of incident response investigations, threat hunting exercises, and network traffic analyses. The case files document applied methodologies for detecting, analyzing, and mitigating cybersecurity threats using industry-standard tools and frameworks. 

## Technical Proficiencies
*   **Security Information & Event Management (SIEM):** Splunk Cloud
*   **Network Protocol Analysis:** Wireshark, TCP/IP, Packet Capture (PCAP) Analysis
*   **Log Analysis:** DHCP, System Security Logs, DNS, HTTP/FTP
*   **Frameworks & Playbooks:** MITRE ATT&CK, NIST Incident Response Lifecycle, Incident Response Consortium (IRC)

---

## Case Files

### 📁 [1. Insider Threat & Impersonation Analysis](./Unit-1-PCAP-Analysis)
**Summary:** Investigated a suspected insider threat and corporate data exfiltration event. 
**Methodology:** Utilized **Wireshark** to analyze raw `.pcap` files, isolating malicious SMTP traffic. Performed a three-layer correlation across network traffic, DHCP logs, and system security logs to attribute the unauthorized IP (`10.10.1.4`) to a specific authenticated user account.

---
*Note: This portfolio is continuously updated as new investigations are completed.*
