Network Security Assessment Lab
Overview

This project simulates a basic internal network security assessment performed in a controlled lab environment using Kali Linux and Ubuntu Server.

The objective was to practice reconnaissance, port scanning, service enumeration, risk analysis, and hardening techniques following a structured security assessment methodology.

Objective

To identify exposed services within an internal network, analyze potential security risks, and implement mitigation strategies to reduce the attack surface.

Lab Environment
Role	System	IP Address
Attacker	Kali Linux	192.168.56.X
Target	Ubuntu Server	192.168.56.102

Network Configuration:

Host-Only Network (VirtualBox)

Subnet: 192.168.56.0/24

Methodology

The assessment followed five structured phases:

**1: Lab Setup**
VirtualBox environment configuration

Host-only network setup

Connectivity verification using ping

**2: Network Discovery**
Command used:

nmap -sn 192.168.56.0/24


Explanation:

-sn → Host discovery only (no port scan)

Technique used → ARP requests within local network

Result:

Multiple active hosts identified

Target machine confirmed at 192.168.56.102

**3: Port Scanning & Service Enumeration**

Command used:

nmap -sS -sV -O 192.168.56.102


Options explained:

-sS → SYN Scan (stealth scan)

-sV → Service version detection

-O → Operating system detection

Findings:
Port	State	Service	Version
22/tcp	Open	SSH	OpenSSH 9.6p1 (Ubuntu)

**4: Risk Analysis**

Identified risk:

SSH exposed with password authentication enabled

Potential Threat:

Brute force attack

Credential stuffing

Unauthorized remote access

Example attack attempt:

hydra -l user -P rockyou.txt ssh://192.168.56.102

**5: Mitigation Implemented**

Hardening applied on Ubuntu Server:

sudo nano /etc/ssh/sshd_config


Modified:

PasswordAuthentication no


Service restarted:

sudo systemctl restart ssh

**6: Validation of Mitigation**
Re-scanned SSH authentication methods.

**Results**
Password authentication disabled

Hydra brute-force attack no longer possible

Attack surface successfully reduced.

**Security Improvements Achieved**

Eliminated password-based SSH authentication
Enforced stronger authentication model
Reduced brute-force exposure
Validated mitigation effectiveness

**Key Skills Demonstrated**
Network reconnaissance

Port scanning techniques

Service enumeration

Risk assessment mindset (SOC perspective)

Linux hardening

Attack simulation

Security validation testing

Documentation & reporting

**Conclusion**

This lab demonstrates a complete mini security assessment cycle:

Discover

Enumerate

Analyze

Exploit attempt

Mitigate

Validate

The SSH service was identified as a potential attack vector and successfully hardened to reduce risk exposure within the internal network.

**Future Improvements**
Implement Fail2Ban

Configure firewall rules (UFW)

Add web server attack surface

Perform vulnerability scanning with NSE scripts

Create SIEM-style logging analysis

**Disclaimer**

This lab was conducted in a controlled virtual environment for educational purposes only. No real systems were targeted.
