<div align="center">

# InfraHardener-ZeroTrust 🛡️
### *Automated Multi-Node Enterprise Linux Hardening & CIS Compliance Engine*

[![Ansible Lint](https://github.com/your-org/InfraHardener-ZeroTrust/actions/workflows/ci.yml/badge.svg)](https://github.com/your-org/InfraHardener-ZeroTrust/actions)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Ansible Core](https://img.shields.io/badge/Ansible_Core-2.15+-red.svg)](https://docs.ansible.com/)
[![Molecule Verified](https://img.shields.io/badge/Molecule-Tested-green.svg)](https://molecule.readthedocs.io/)
[![CIS Benchmark Compliance](https://img.shields.io/badge/CIS_Benchmark-Level_1_%26_2-orange.svg)](https://www.cisecurity.org/)

[Architecture](#-architectural-overview) • [Quickstart](#-quickstart) • [Modular Tags](#-modular-execution-tags) • [Compliance Audit](#-automated-compliance--reporting) • [Testing](#-molecule-integration-testing)

</div>

---

## 📌 Architectural Overview

**InfraHardener-ZeroTrust** is a production-grade Infrastructure as Code (IaC) execution engine designed to strictly enforce **CIS (Center for Internet Security) Benchmarks** and **Zero-Trust network architecture** across heterogeneous Linux enterprise environments.

```text
               ┌────────────────────────────────────────────────────────┐
               │                InfraHardener Control Plane             │
               └───────────────────────────┬────────────────────────────┘
                                           │
                        ┌──────────────────┴──────────────────┐
                        │   Ansible Hardening & Zero-Trust   │
                        └──────────────────┬──────────────────┘
                                           │
         ┌─────────────────────────────────┴─────────────────────────────────┐
         │                                                                   │
┌────────▼────────────────────────┐                       ┌──────────────────▼─────────────────┐
│     Debian / Ubuntu Nodes       │                       │       RHEL / Rocky Linux Nodes     │
│ ─────────────────────────────── │                       │ ────────────────────────────────── │
│ • UFW Default-DROP Rules        │                       │ • Firewalld Zone Controls          │
│ • AppArmor / Sysctl Security    │                       │ • SELinux / Sysctl Hardening       │
│ • Auditd Integrity Monitoring   │                       │ • Auditd Integrity Monitoring      │
│ • OpenSSH Ciphers Enforcement   │                       │ • OpenSSH Hardening & Fail2ban     │
└─────────────────────────────────┘                       └────────────────────────────────────┘


```

# Prerequisites:
Ansible Control Node: Python 3.10+, ansible-core >= 2.15
Target Nodes: SSH access with sudo privileges

# Installation:
# Clone the repository
git clone [https://github.com/your-org/InfraHardener-ZeroTrust.git](https://github.com/your-org/InfraHardener-ZeroTrust.git)
cd InfraHardener-ZeroTrust

# Install required Ansible collection dependencies
ansible-galaxy collection install -r requirements.yml

# Dry-Run & Production Run:
# Dry-run execution (Check mode)
ansible-playbook -i inventory.ini site.yml --check --diff

# Enforce hardening across production inventory
ansible-playbook -i inventory.ini site.yml --limit production
