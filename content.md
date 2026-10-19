# 🛡️ Complete Nessus Vulnerability Scanning Tutorial

A comprehensive, step-by-step walkthrough for installing, configuring, and executing vulnerability scans using **Tenable Nessus**. This guide is optimized for security students, ethical hackers, and sysadmins looking to deploy industry-standard security mapping labs.

---

## 📋 Table of Contents
1. [Prerequisites & Lab Architecture](#1-prerequisites--lab-architecture)
2. [Nessus Installation (Kali Linux & Debian)](#2-nessus-installation-kali-linux--debian)
3. [Initial Web Activation Wizard](#3-initial-web-activation-wizard)
4. [Configuring Scan Templates & Policies](#4-configuring-scan-templates--policies)
5. [Running Your First Vulnerability Scan](#5-running-your-first-vulnerability-scan)
6. [Analyzing the Dashboard & Reporting](#6-analyzing-the-dashboard--reporting)

---

## 1. Prerequisites & Lab Architecture
Before beginning, ensure your host machine has at least **4GB RAM** allocated to the virtualization system to allow Nessus plugins to compile smoothly.

* **Target Setup:** A vulnerable target machine (e.g., Metasploitable 2 or a Windows 10 VM running outdated browser builds).
* **Scanner:** Kali Linux or Ubuntu 20.04+.
* **License:** A free **Nessus Essentials** activation code (supports scanning up to 16 individual IP addresses).

---

## 2. Nessus Installation (Kali Linux & Debian)

### Step 1: Download the Package
Navigate to the [Official Tenable Downloads Directory](https://tenable.com). Select **Linux-Debian-amd64** to download the official `.deb` installation file.

### Step 2: Unpack and Install via CLI
Open your terminal window inside the folder where your package was saved and run:

```bash
sudo dpkg -i Nessus-*.deb
```

### Step 3: Launch the Background Service
Enable and execute the system daemon to get the background web application operational:

```bash
sudo systemctl start nessusd.service
sudo systemctl enable nessusd.service
```

---

## 3. Initial Web Activation Wizard

Once the daemon is active, access the graphical installation wizard via your browser by hitting the secure localhost port:  
📍 **URL:** `https://localhost:8834` *(Accept the self-signed certificate warning to proceed)*

![Welcome and Product Choice Interface](https://kifarunix.com)

1. Select **Nessus Essentials** from the opening menu and hit **Continue**.
2. Supply your details to receive a key via email, or skip this step if you already have your activation string ready.
3. Establish your **Master Admin** profile by defining a unique system username and secure password.

![Admin Account Configuration Form](https://computingforgeeks.com)

> ⚠️ **Important:** Nessus will immediately begin downloading and compiling its extensive system of vulnerability plugins. This step can take 15 to 30 minutes depending on processor speed. The "New Scan" interface will remain locked until this operations background pipeline wraps up.

---

## 4. Configuring Scan Templates & Policies

Nessus handles system discovery, credential verification, and patch level observation via flexible pre-built policies.

![Tenable Nessus Pre-configured Templates Menu](https://kifarunix.com)

### Core Scanner Templates:
* **Host Discovery:** Fast mapping profile to verify live endpoints, hostnames, and accessible routing structures.
* **Basic Network Scan:** General full-stack scan covering system misconfigurations, patching deficits, and open logical ports.
* **Advanced Scan:** A deep-dive environment allowing customized control parameters for granular plugin isolation.

To tweak custom variables, choose **Policies** -> **New Policy**, pick your baseline structure, and fine-tune your parameters before locking in the profile.

---
## 5. Running Your First Vulnerability Scan

### Step 1: Define Target and Scope
Click **New Scan** and select your configuration profile (e.g., **Basic Network Scan**).

![Advanced Custom Scan Settings Menu](https://medium.com)

* **Name:** A logical title identifier for your testing history.
* **Folder:** Consolidate data fields inside the standard **My Scans** directory.
* **Targets:** Define individual target machine addresses or full subnets (e.g., `192.168.1.15` or `192.168.1.0/24`).

### Step 2: Run & Monitor Progress
Save the scan configuration to your active management pool. Click the **Launch icon (Play Button)** to immediately fire off the engine checks. 

---

## 6. Analyzing the Dashboard & Reporting

When the scanner rounds out its operational checklist, click on the completed scan log file to view the vulnerability matrix chart.

![Nessus Vulnerability Assessment Dashboard Overview](https://tenable.com)

### Decoding the Metrics
Vulnerabilities are dynamically categorized across color-coded risk scales derived from their foundational CVSS profile matrix:
* 🟥 **Critical:** Immediate exploitability hazard (e.g., Remote Code Execution vulnerabilities).
* 🟧 **High:** Definite threat profiles representing weak encryption properties or configuration gaps.
* 🟨 **Medium:** Service weaknesses or data disclosure liabilities requiring mitigation planning.
* 🟦 **Low / Info:** Structural environment declarations (e.g., tracking visible open ports or host info).

### Exporting Evidence Documentation
For reporting or remediation reference pipelines, click **Export** in the top right section and select **PDF** or **HTML** formats to export a highly detailed, clean operational audit layout.
