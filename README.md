Network Security Assessment Lab
1. Project Overview

This project simulates a small internal network to perform a basic security assessment using Nmap. The objective was to identify active hosts, detect open ports and running services, analyze potential security risks, and propose mitigation strategies aligned with SOC-level analysis.

2. Lab Environment

Virtualization Platform: VirtualBox
Attacker Machine: Kali Linux
Target Machine: Ubuntu Server
Network Configuration: Host-Only Network

Both machines were configured within the same isolated network segment to simulate an internal enterprise environment.

3. Methodology
Step 1 – Host Discovery
nmap -sn 192.168.X.0/24


Purpose: Identify active hosts within the subnet.
Technique: ICMP echo requests and ARP discovery (ping scan).

Step 2 – Port Scanning & Service Detection
nmap -sS -sV -O <TARGET_IP>


-sS → TCP SYN Scan (stealth scan)

-sV → Service version detection

-O → Operating system detection

4. Findings

Example (replace with your real results):

Port	State	Service	Version
22	Open	SSH	OpenSSH 8.x
80	Open	HTTP	Apache 2.x

The scan identified exposed services running on the target system.

5. Risk Analysis
Port 22 – SSH

Risk: Potential brute-force attacks or credential compromise.
Impact: Unauthorized remote access.
Recommendation:

Disable root login

Implement key-based authentication

Configure fail2ban

Restrict access via firewall

Port 80 – HTTP

Risk: Exposure to web-based vulnerabilities.
Impact: Possible information disclosure or exploitation.
Recommendation:

Apply server hardening

Keep services updated

Restrict unnecessary exposure

6. Conclusion

This lab demonstrates foundational skills in network enumeration, service detection, and security risk analysis. The exercise reflects practical SOC-level tasks such as identifying exposed services, analyzing potential threats, and recommending mitigation strategies.

7. Tools Used

Nmap

VirtualBox

Kali Linux

Ubuntu Server
