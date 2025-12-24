# 🏠 Cybersecurity Home Lab

A documented journey of building and configuring my personal cybersecurity lab environment for hands-on learning and skill development.

## Overview

This repository documents my home lab setup designed for practicing cybersecurity concepts including:
- Network security monitoring
- Vulnerability assessment
- Log analysis and SIEM fundamentals
- Malware analysis (isolated environment)
- Incident response procedures

## Lab Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        HOST MACHINE                              │
│                    (Windows/Mac/Linux)                           │
├─────────────────────────────────────────────────────────────────┤
│                      VIRTUALIZATION LAYER                        │
│                  (VirtualBox / VMware / Proxmox)                 │
├──────────────┬──────────────┬──────────────┬───────────────────┤
│   KALI VM    │  UBUNTU VM   │ WINDOWS VM   │  SECURITY ONION   │
│  (Attacker)  │  (Target)    │  (Target)    │  (Monitoring)     │
│              │              │              │                    │
│ • Nmap       │ • DVWA       │ • Vulnerable │ • Suricata        │
│ • Burp Suite │ • Metasploit-│   services   │ • Zeek            │
│ • Wireshark  │   able       │ • Logging    │ • Elasticsearch   │
│ • Metasploit │ • SSH        │   enabled    │ • Kibana          │
└──────────────┴──────────────┴──────────────┴───────────────────┘
                              │
                    [Isolated Virtual Network]
                     (No internet access for
                      vulnerable machines)
```

## Components

### Virtual Machines
| VM | Purpose | Resources |
|----|---------|-----------|
| Kali Linux | Penetration testing & security tools | 4GB RAM, 2 CPU |
| Ubuntu Server | Target system, log generation | 2GB RAM, 1 CPU |
| Windows 10 | Windows security testing | 4GB RAM, 2 CPU |
| Security Onion | Network monitoring & SIEM | 8GB RAM, 4 CPU |

### Network Configuration
- **NAT Network**: For VMs needing internet access (updates only)
- **Internal Network**: Isolated network for attack simulations
- **Host-Only**: For management access

## Setup Guides

Each subfolder contains detailed setup instructions:
- [`/kali-setup`](./kali-setup) - Kali Linux configuration
- [`/vulnerable-targets`](./vulnerable-targets) - Setting up intentionally vulnerable systems
- [`/siem-setup`](./siem-setup) - Security Onion installation and configuration
- [`/network-config`](./network-config) - Virtual network configuration

## Lab Exercises Completed

- [x] Network scanning with Nmap
- [x] Packet capture and analysis with Wireshark
- [x] Web application testing on DVWA
- [x] Log analysis and correlation
- [ ] Malware analysis (in progress)
- [ ] Active Directory attacks and defenses

## Skills Demonstrated

- **Virtualization**: VirtualBox/VMware configuration and management
- **Linux Administration**: CLI proficiency, service management, networking
- **Network Security**: Firewall rules, network segmentation, monitoring
- **Security Tools**: Nmap, Wireshark, Burp Suite basics

## Screenshots

*Screenshots of your lab in action go here*

## Resources Used

- [VirtualBox Documentation](https://www.virtualbox.org/manual/)
- [Kali Linux Docs](https://www.kali.org/docs/)
- [Security Onion Documentation](https://docs.securityonion.net/)
- [DVWA GitHub](https://github.com/digininja/DVWA)

## Future Improvements

- Add Splunk or ELK stack for log aggregation
- Implement Active Directory environment
- Add cloud integration (AWS/Azure free tier)
- Automate VM deployment with Vagrant

## License

This project is for educational purposes only. Do not use these techniques on systems you do not own or have explicit permission to test.
