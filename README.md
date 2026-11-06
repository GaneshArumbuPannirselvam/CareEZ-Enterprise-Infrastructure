# Project 00: Enterprise Hybrid Cloud Architecture & Security Hardening Framework
**Company Asset Layer:** CareEZ IT SOL (careezitsol.com)
**Category:** Multi-Cloud Engineering, Identity Access Management (IAM), Perimeter Defense, Compliance Engineering  
**Core Technologies:** Microsoft Azure, Google Cloud Platform (GCP), Cloudflare Edge Proxy, pfSense, Wireshark, Let's Encrypt (Certbot), NIST SP 800-53, CIS Benchmarks

---
## 1. Executive Summary & Architectural Overview
This repository documents the production-grade deployment, administration, and security hardening of the enterprise web application infrastructure hosting **CareEZ IT SOL (careezitsol.com)**. To ensure high availability, layered perimeter defense, and data confidentiality, a hybrid multi-cloud framework was engineered across **Microsoft Azure** and **Google Cloud Platform (GCP)**. 

The baseline infrastructure has been wrapped in a zero-trust network topology leveraging **Cloudflare Edge Proxies** to obscure origin environments, automated **Let's Encrypt SSL/TLS pipelines** to enforce strict data-in-transit confidentiality, and granular Identity and Access Management policies aligned directly with **NIST SP 800-53** controls and **CIS Foundations Benchmarks**.

---

## 2. Technical Execution & Operational Deliverables

### 2.1 Multi-Cloud & Endpoint Administration
* **Infrastructure Provisioning:** Engineered and administered decoupled compute instances across Azure Virtual Machines and GCP Compute Engine to distribute operational risk and optimize asset hosting availability.
* **DNS Zone Management:** Configured global DNS zone record parameters, establishing secure CNAME Flattening profiles and routing parameters to handle active user connection loads seamlessly.
* **Virtual Networking:** Structured Virtual Networks (VNet/VPC) mapping strict Subnet segment boundaries to isolate public web-facing endpoints from critical back-end database layers.

### 2.2 Identity & Microsoft 365 Management
* **Zero-Trust IAM Policy Enforcements:** Implemented comprehensive Identity and Access Management (IAM) controls, assigning Role-Based Access Controls (RBAC) following the security principle of Least Privilege.
* **Tenant Security Baselines:** Configured tenant-wide multi-factor authentication (MFA) parameters across administrative identity endpoints, eliminating single-factor vector vulnerabilities.

### 2.3 Perimeter & Network Security (Cloudflare & pfSense Integration)
* **Origin Obfuscation (Proxy Mode):** Deployed Cloudflare reverse proxy architectures (Orange Cloud mode) across destination CNAME strings, rendering actual Azure/GCP backend hosting public IP addresses invisible to public malicious scanning bots.
* **Virtual Firewall Engineering:** Configured virtual perimeter firewall boundaries (pfSense rule logic) to restrict management access ports; blocked global inbound port 22 (SSH) routes, locking administrative lanes exclusively to authorized source IPs.
* **Edge Boundary Hardening:** Leveraged Cloudflare Bot Fight Mode and automated DDoS rate-limiting engines to intercept and drop malicious automated bot vectors at the provider edge.

### 2.4 Traffic Analysis, Encryption & Incident Support
* **Deep Packet Inspection Telemetry:** Utilized **Wireshark** to conduct deep packet inspection (DPI) and protocol analysis across local interfaces, baselining standard connection states and verifying the TCP 3-Way Handshake mechanics.
* **Strict Transit Data Encryption:** Configured automated **Let's Encrypt SSL/TLS certificates** via **Certbot** on the Linux hosting nodes, upgrading the cloud edge profile to **Full (Strict) Encryption Mode** to prevent Man-in-the-Middle (MitM) wire interception attempts.

---

## 3. Regulatory Framework & Governance Mapping

To validate that the infrastructure meets enterprise corporate compliance auditing parameters, all technical implementations were mapped directly back to the **NIST SP 800-53 Rev. 5** catalog and **CIS Foundations Benchmarks**:

| Implemented Infrastructure Control | CIS Benchmark Alignment | NIST SP 800-53 Control Mapping |
| :--- | :--- | :--- |
| **Cloudflare Proxy & Port 22 Closure** | CIS Networking v2.0 - Control 4.1 | **AC-4** (Information Flow Enforcement) |
| **Let's Encrypt / Full (Strict) SSL Mode** | CIS Data Protection v2.0 - Control 7.1 | **SC-8** (Transmission Confidentiality) |
| **Cloud-Hosted Role-Based Access (RBAC)** | CIS Identity & Access v2.0 - Control 1.1 | **AC-6** (Least Privilege) |
| **Cloudflare Bot Fight Mode & DDoS Filters** | CIS Monitoring v2.0 - Control 5.2 | **SI-4** (System Monitoring & Telemetry) |

---

## 4. Disaster Recovery & System Availability
* **Automated Data Protection:** Deployed automated cron-job data backup script workflows to securely write localized system changes to detached cloud storage buckets, ensuring zero-data-loss capabilities.
* **Cross-Cloud Failover Playbooks:** Maintained structured snapshot restoration protocols to facilitate rapid environment migration and disaster recovery failover actions across cloud provider nodes in the event of an outage.
* **Patch Management Lifecycle:** Enforced automated system security kernel updates and software patch deployment schedules across host virtual machine OS images to defend against emerging logic exploits.
