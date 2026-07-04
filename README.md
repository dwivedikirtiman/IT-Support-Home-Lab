# Enterprise IT Support & Core Infrastructure Sandbox Lab

## Project Overview
This repository serves as a live, operational runbook and engineering portfolio documenting a from-scratch deployment of an enterprise-grade corporate IT infrastructure. Designed to mirror the operating standards of enterprise Tier-1 MSP networks (such as Wipro, HCL, and TCS), this sandbox environment simulates real-world user lifecycle management, core networking protocols (DHCP/DNS), Group Policy deployments, and daily helpdesk scenario remediation.

---

## 💻 Lab Hardware Specifications (Physical Host)
* **Processor:** AMD Ryzen 5 5600GT (6 Cores, 12 Threads @ 3.60 GHz)
* **Physical Memory:** 16 GB DDR4 RAM (Allocated dynamically to maintain host stability)
* **Storage Environment:** Dedicated high-capacity 160 GB secondary partition (E:\ Drive)
* **Hypervisor Platform:** Oracle VM VirtualBox (v7.0+ Architecture)

---

## 🛠️ Infrastructure Component Map
| Asset Name | Role Identity | Operating System | Allocated Resource Profile | Network Segment |
| :--- | :--- | :--- | :--- | :--- |
| **DC01** | Active Directory Domain Controller | Windows Server 2022 Standard | 4 GB RAM / 2 vCPU / 60 GB VDI | Host-Only Private Sandbox |
| **CLIENT01** | Enterprise Workplace Endpoint | Windows 11 Enterprise | 4 GB RAM / 2 vCPU / 50 GB VDI | Host-Only Private Sandbox |

---

## 📂 Portfolio Structure
* **`/Project-1-Active-Directory`**: Runbooks for Domain Services setup, DHCP scopes, and user provisioning.
* **`/Project-1-Active-Directory/tickets`**: Resolution logs for 10 distinct L1 technical helpdesk scenarios.
* **`/assets/images`**: Verified milestone screenshots validating successful lab configurations.

---

## 📈 Core Technical Competencies Demonstrated
1. **Directory Services Identity Management:** Active Directory Domain Services (AD DS) design, implementation, and user provisioning.
2. **Infrastructure Automation & Governance:** Group Policy Object (GPO) configuration and centralized baseline management.
3. **Core Networking Troubleshooting:** Diagnosing state issues within DHCP scope environments, APIPA fallbacks, and DNS resolution paths using command-line diagnostics (`nslookup`, `ipconfig`).
