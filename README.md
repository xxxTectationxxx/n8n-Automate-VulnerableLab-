# 🤖 n8n-Automate-Pwn: CVE-2025-68613 Vulnerable Lab

![Security Rating](https://img.shields.io/badge/Severity-CRITICAL-red?style=for-the-badge)
![Docker](https://img.shields.io/badge/Docker-Enabled-blue?style=for-the-badge)
![n8n](https://img.shields.io/badge/Target-n8n_1.120.0-orange?style=for-the-badge)
![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green?style=for-the-badge)

> **⚠️ WARNING: INTENTIONALLY VULNERABLE APPLICATION**
>
> This repository contains a Dockerized application specifically configured to be vulnerable to **CVE-2025-68613 (RCE)**.
> * **DO NOT** deploy this container in a production environment or on a public server exposed to the internet.
> * **DO NOT** run this on a machine containing sensitive data without proper network isolation.
> * This lab is strictly for **educational purposes, security research, and CTF simulations**.

## 🎯 Challenge Overview

This lab is designed as a **Simple Web to Root** scenario, perfect for beginners to practice vulnerability exploitation and basic privilege escalation techniques in a Linux environment.

* **Difficulty:** Easy (Beginner Friendly)
* **Estimated Time:** ~20 Minutes
* **Objective:** Exploit the RCE vulnerability to gain initial access, then escalate privileges to root.
* **Flags to Capture:**
    1.  🚩 **User Flag:** `user.txt`
    2.  🚩 **Root Flag:** `root.txt`

---

## 🔍 Vulnerability Analysis

**n8n RCE (CVE-2025-68613)** is a critical Remote Code Execution (RCE) vulnerability located in the **workflow expression evaluation system** of the n8n platform.

### The Flaw
The vulnerability exists because expressions supplied by **authenticated users** during workflow configuration may be evaluated in an execution context that is not sufficiently isolated from the underlying runtime. Under certain conditions, an attacker can abuse this behavior to execute arbitrary code with the privileges of the n8n process. Successful exploitation leads to a full compromise of the affected instance, allowing unauthorized access to sensitive data, modification of workflows, and execution of system-level operations.

### Affected Components & Versions
According to the security advisory, the following versions are affected:

**1. Vulnerable Versions**
* All versions starting from **0.211.0** up to (but excluding) **1.120.4**.
* All versions prior to **1.121.1**.
* All versions prior to **1.122.0**.
* **Target Lab Version:** `1.120.0` (Vulnerable).

> **✅ Safe Configurations (Patched):**
> Applications updated to **n8n v1.121.0** (or later) which include the strict input sanitization patch are **NOT AFFECTED** by this specific vulnerability.

### Mitigation
If upgrading is not immediately possible, administrators are advised to limit workflow creation and editing permissions to fully trusted users only, and deploy n8n in a hardened environment with restricted OS privileges.

---

## 🚀 Lab Installation & Usage

This lab utilizes Docker to ensure a safe, isolated, and reproducible environment. No local Node.js setup is required.

### Prerequisites
* [Docker Desktop](https://www.docker.com/products/docker-desktop) or Docker Engine.
* Docker Compose.

### Quick Start

1.  **Clone the Repository**
    ```bash
    git clone https://github.com/xxxTectationxxx/n8n-Automate-VulnerableLab-.git
    cd n8n-Automate-VulnerableLab-
    ```

2.  **Launch the Victim Container**
    ```bash
    docker compose up -d
    ```

3.  **Access the Target**
    Open your browser or Burp Suite and navigate to:
    ```
    http://localhost:5678
    ```

4.  **Shutdown**
    To stop the lab and clean up resources:
    ```bash
    docker compose down
    ```

---

## 🛠️ Technical Stack

* **Vulnerable App**: n8n v1.120.0
* **Containerization**: Docker
* **OS Environment**: Alpine Linux (Node.js)
* **Port**: `5678`

## 📚 References

For verified technical details and official reports regarding this vulnerability, please refer to:

1.  **National Vulnerability Database (NIST)**: [CVE-2025-68613 Detail](https://nvd.nist.gov/vuln/detail/CVE-2025-68613)
2.  **GitHub Advisory Database**: [n8n Security Advisory](https://github.com/advisories)
3.  **Official n8n Security**: [n8n Security Policy & Updates](https://n8n.io/security/)

---

### 👤 Author
Maintained by **[Agus33ina](https://github.com/agus33ina)**.
