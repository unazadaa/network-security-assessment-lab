Network Security Assessment Lab

**Executive Summary**
This project simulates an internal network security assessment conducted in a controlled lab environment.
The goal was to identify exposed services, assess associated risks, simulate attack scenarios, apply mitigation strategies, and validate remediation effectiveness.
The assessment successfully identified SSH password authentication as a potential attack vector and implemented hardening measures to reduce brute-force risk exposure.

**Scope**

Environment: VirtualBox (Host-Only Network)
Attacker: Kali Linux
Target: Ubuntu Server
Subnet: 192.168.56.0/24

This assessment was conducted in a non-production lab environment for educational purposes.

**Methodology**
The engagement followed a structured security workflow:

1 Network Discovery
2 Port Scanning
3 Service Enumeration
4 Risk Analysis
5 Exploit Simulation
6 Hardening
7Post-Mitigation Validation

**Phase 1 – Network Discovery**
Command:
nmap -sn 192.168.56.0/24

Technique Used:
  ARP-based host discovery (Layer 2)
Result:
  Active hosts identified
  Target confirmed at 192.168.56.102
  **Phase 2 – Port Scanning & Service Detection**
Command:
nmap -sS -sV -O 192.168.56.102

Findings:
| Port   | Service | Version       | Risk             |
| ------ | ------- | ------------- | ---------------- |
| 22/tcp | SSH     | OpenSSH 9.6p1 | Brute-force risk |

**Identified Risk:**
SSH service exposed with password authentication enabled.

**Threat Scenario:**
  Brute force attacks
  Credential stuffing
  Unauthorized remote access

**Attack Simulation**
**Tool used:**
  Hydra
  Attempted brute-force attack against SSH service.

**Result:**
Password authentication initially allowed attack attempts.

**Mitigation Implemented**
Configuration change in:
  /etc/ssh/sshd_config

**Modified parameter:**
  PasswordAuthentication no

**Service restarted:**
  sudo systemctl restart ssh

**Validation**
Post-mitigation testing confirmed:
  Password authentication disabled
  Brute-force attempts blocked
  Reduced attack surface

**Security Impact**
| Before                 | After                  |
| ---------------------- | ---------------------- |
| Password login enabled | Disabled               |
| Brute-force possible   | Prevented              |
| Higher exposure        | Reduced attack surface |


**Skills Demonstrated**
  Network reconnaissance
  SYN scanning
  Service enumeration
  Risk identification
  Attack simulation
  Linux system hardening
  Security validation
  Security documentation
  
**Future Improvements**
  Implement Fail2Ban
  Configure UFW firewall rules
  Add centralized logging
  Deploy a vulnerable web service for extended testing
  Simulate SIEM monitoring

**Disclaimer**
This project was conducted in a controlled lab environment for ethical and educational purposes only.
