# 📧 SOC Phishing Email Investigation Playbook




\

**A practical guide for Security Operations Center (SOC) analysts to investigate Emails, URLs, Domains, IPs, and Malware.**

---

## 📚 Table of Contents

* [Overview](#-overview)
* [Email Analysis](#-1-email-analysis)
* [IP Address Analysis](#-2-ip-address-analysis)
* [URL Analysis](#-3-url-analysis)
* [File Analysis](#-4-file-analysis)
* [Malware Analysis Resources](#-5-malware-analysis-resources)
* [Correlation & Validation](#-6-correlation-and-validation)
* [Incident Classification](#-7-incident-classification)
* [Investigation Report Template](#-8-investigation-report-template)
* [Recommended Analyst Workflow](#-recommended-analyst-workflow)

---

# 📖 Overview

This playbook provides a structured methodology for investigating:

✅ Phishing Emails

✅ Malicious URLs

✅ Suspicious Domains

✅ IP Addresses

✅ Malware Samples

✅ Attachments

The objective is to determine whether an indicator is:

| Verdict       | Description                       |
| ------------- | --------------------------------- |
| 🟢 Benign     | No malicious activity detected    |
| 🟡 Suspicious | Requires additional investigation |
| 🔴 Malicious  | Confirmed malicious activity      |

---

# 📧 1. Email Analysis

## 🔍 Email Header Analysis

Review the complete email header and validate:

* SPF (Sender Policy Framework)
* DKIM (DomainKeys Identified Mail)
* DMARC (Domain-based Message Authentication, Reporting, and Conformance)
* Return-Path
* Reply-To Address
* Sender Domain
* Received Headers

### 🚩 Indicators of Suspicious Activity

| Indicator               | Description               |
| ----------------------- | ------------------------- |
| SPF Failure             | Sender may be spoofed     |
| DKIM Failure            | Message integrity issue   |
| DMARC Failure           | Authentication failed     |
| Reply-To Mismatch       | Possible phishing         |
| Suspicious Routing      | Unusual mail path         |
| Newly Registered Domain | Common phishing indicator |

---

## 📝 Email Content Analysis

### ⏰ Urgency Indicators

* Immediate action required
* Account suspension warnings
* Password reset requests
* Payment requests
* Executive impersonation
* Financial requests

### 🎭 Social Engineering Indicators

* Credential harvesting attempts
* Requests for sensitive information
* Poor grammar and spelling
* Unexpected attachments
* Suspicious URLs

---

# 🌍 2. IP Address Analysis

## 🔎 Initial Verification

### Questions to Ask

* Does the IP belong to the organization?
* Does the IP belong to a trusted vendor?
* Is communication expected?

---

### ✅ If YES

* Verify activity is legitimate
* Document findings
* Close case if no malicious indicators exist

---

### ❌ If NO

Proceed with a full investigation.

---

## 📊 IP Reputation Analysis

Collect:

* Geolocation
* ASN
* ISP
* Historical reputation
* Threat intelligence records

### 🛠 Tools

| Tool       | Purpose         |
| ---------- | --------------- |
| MxToolbox  | IP Intelligence |
| VirusTotal | Reputation      |
| AbuseIPDB  | Abuse Reports   |

### 🚩 Review

* Malicious reports
* Spam activity
* Botnet activity
* Known C2 infrastructure
* Hosting provider reputation

---

# 🔗 3. URL Analysis

## 🌐 URL Reputation

### Tools

| Tool                 | Purpose                |
| -------------------- | ---------------------- |
| VirusTotal           | URL Reputation         |
| BlueCoat Site Review | Website Categorization |
| Zscaler Zulu         | URL Classification     |

### Review

* Detection count
* Vendor classifications
* Website category
* Reputation score

---

## 🧪 URL Sandbox Analysis

### Tools

| Tool       | Purpose               |
| ---------- | --------------------- |
| ANY.RUN    | Dynamic Analysis      |
| URLScan.io | Website Investigation |

### Look For

* Credential harvesting pages
* Fake login portals
* Malicious redirects
* Obfuscated JavaScript
* Malware downloads

---

## 🏢 Domain Intelligence

### Tool

**DomainTools WHOIS**

### Review

* Domain age
* Registration date
* Registrar
* Registrant details
* Historical WHOIS records

### 🚩 Red Flags

* Newly registered domains
* Privacy-protected registrations
* Typosquatting domains
* Suspicious registrars

---

## 🎣 Phishing Database Verification

### Tools

| Tool      | Purpose            |
| --------- | ------------------ |
| URLHaus   | Malware URLs       |
| OpenPhish | Phishing Detection |
| PhishTank | Phishing Database  |

### Purpose

Determine whether the URL has previously been reported as:

* Phishing
* Malware delivery
* Credential theft
* Scam infrastructure

---

# 📁 4. File Analysis

## 🔬 File Reputation Analysis

### Tools

| Tool            | Purpose                |
| --------------- | ---------------------- |
| VirusTotal      | Reputation             |
| Hybrid Analysis | Threat Intelligence    |
| Intezer Analyze | Malware Classification |

### Review

* Detection ratio
* File type
* Malware family
* Community comments

---

## 🧪 Dynamic Analysis (Sandboxing)

### Tools

| Tool            | Purpose             |
| --------------- | ------------------- |
| ANY.RUN         | Dynamic Analysis    |
| Joe Sandbox     | Malware Analysis    |
| Hybrid Analysis | Threat Analysis     |
| Triage          | Behavioral Analysis |

---

### ⚙️ Process Activity Analysis

Review:

* Parent-child process relationships
* PowerShell execution
* CMD execution
* Script interpreters
* Process injection attempts
* DLL loading

---

### 📂 File System Activity

Review:

* File creation
* File deletion
* Dropped payloads
* Encrypted files
* Temporary file creation

---

### 🌐 Network Activity

Review:

* DNS requests
* HTTP/HTTPS traffic
* C2 communication
* Suspicious domains
* Suspicious IPs

---

### 🗄 Registry Activity

Review:

* Run Keys
* Startup Entries
* Service Creation
* Registry Modifications

---

### 🔄 Persistence Mechanisms

Review:

* Scheduled Tasks
* Services
* Startup Folders
* Registry Persistence

---

### 🔓 Privilege Escalation

Review:

* New User Creation
* Token Manipulation
* UAC Bypass Attempts
* Administrative Access Changes

---

# 🦠 5. Malware Analysis Resources

## 🔍 Malware Lookup

* VirusTotal
* Zelster Malicious Website Lookup

---

## 🧪 Sandboxing Platforms

* ANY.RUN
* Joe Sandbox
* Hybrid Analysis
* Triage
* Intezer Analyze

---

## 📡 Threat Intelligence Feeds

* Feed Seguranca Informatica

---

## 🍳 Investigation Utilities

### CyberChef

Useful for:

* Base64 Decoding
* URL Decoding
* Hash Generation
* IOC Extraction
* Data Transformation
* Deobfuscation

---

# 🔗 6. Correlation and Validation

Correlate findings across:

📧 Email

🌍 Domain

🔗 URL

🌐 IP Address

📁 Attachment

---

## ❓ Questions to Answer

* Do indicators appear in multiple intelligence sources?
* Is the sender legitimate?
* Is the domain trusted?
* Is the URL malicious?
* Is the attachment malicious?
* Is communication expected?

---

> ⚠️ **Important**
>
> A clean VirusTotal result alone does NOT mean an indicator is safe.
>
> Always correlate findings across multiple sources before making a final determination.

---

# 🚦 7. Incident Classification

| Classification | Description         |
| -------------- | ------------------- |
| 🟢 Benign      | Legitimate activity |
| 🟡 Suspicious  | Requires monitoring |
| 🔴 Malicious   | Confirmed threat    |

---

# 📋 8. Investigation Report Template

## Case Information

| Field       | Value |
| ----------- | ----- |
| Case Number |       |
| Analyst     |       |
| Date        |       |
| Severity    |       |

---

## Indicators

### Email

* Sender:
* Subject:
* SPF:
* DKIM:
* DMARC:

### URL

* URL:
* Domain Age:
* Reputation Result:

### IP Address

* IP:
* ASN:
* ISP:
* Reputation Result:

### File

* File Name:
* SHA256:
* Reputation Result:

---

## Findings

Document all evidence collected during the investigation.

---

## Indicators of Compromise (IOCs)

### Domains

### URLs

### IP Addresses

### Hashes

---

## Verdict

* Benign
* Suspicious
* Malicious

---

## Recommended Actions

* Block Indicators
* Quarantine Email
* Reset Credentials
* Isolate Host
* Escalate Incident
* Continue Monitoring

---

# 🔄 Recommended Analyst Workflow

```text
Email Header Analysis
        ↓
Sender Validation
        ↓
Domain Investigation
        ↓
URL Reputation Check
        ↓
URL Sandbox Analysis
        ↓
Attachment Analysis
        ↓
IP Reputation Analysis
        ↓
Correlation of Findings
        ↓
Classification & Reporting
```

---

### 🛡️ Think Before You Trust

"Trust is earned through verification."

Built for SOC Analysts, Incident Responders, and Threat Hunters.
