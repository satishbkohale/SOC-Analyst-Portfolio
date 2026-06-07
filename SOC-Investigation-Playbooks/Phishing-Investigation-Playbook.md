# 🛡️ SOC Phishing Email Investigation Playbook

## 📖 Overview

This playbook provides a structured methodology for investigating phishing emails, suspicious URLs, domains, IP addresses, and attachments.

The objective is to determine whether an indicator is:

| Verdict       | Description                       |
| ------------- | --------------------------------- |
| 🟢 Benign     | No malicious activity detected    |
| 🟡 Suspicious | Requires additional investigation |
| 🔴 Malicious  | Confirmed malicious activity      |

---

## 📚 Table of Contents

* [📧 Email Analysis](#-1-email-analysis)
* [🌍 IP Address Analysis](#-2-ip-address-analysis)
* [🔗 URL Analysis](#-3-url-analysis)
* [📁 File Analysis](#-4-file-analysis)
* [🦠 Malware Analysis Resources](#-5-malware-analysis-resources)
* [🛠 Tools Reference](#-6-tools-reference)
* [🔗 Correlation and Validation](#-7-correlation-and-validation)
* [🚦 Incident Classification](#-8-incident-classification)
* [🔄 Recommended Analyst Workflow](#-recommended-analyst-workflow)

---

# 📧 1. Email Analysis

## 🎯 Objective

Determine whether the email is legitimate, suspicious, or malicious.

## 🛠 Tools Used

| Tool                                      | Purpose                     |
| ----------------------------------------- | --------------------------- |
| [MxToolbox](https://mxtoolbox.com/)       | Email Header Analysis       |
| [VirusTotal](https://www.virustotal.com/) | URL & Attachment Reputation |
| [ANY.RUN](https://any.run/)               | URL & Attachment Analysis   |

---

## 🔍 Email Header Analysis

Review the complete email header and validate:

* SPF (Sender Policy Framework)
* DKIM (DomainKeys Identified Mail)
* DMARC (Domain-based Message Authentication, Reporting, and Conformance)
* Return-Path
* Reply-To Address
* Sender Domain
* Received Headers

### Check

* SPF Result
* DKIM Result
* DMARC Result
* Sender Domain
* Return Path
* Reply-To Address

### 🚩 Indicators of Suspicious Activity

* SPF Failure
* DKIM Failure
* DMARC Failure
* Reply-To Mismatch
* Suspicious Mail Routing
* Newly Registered Domain

---

## 📝 Email Content Analysis

### Check for Urgency

* Immediate action required
* Account suspension warnings
* Password reset requests
* Payment requests
* Executive impersonation
* Financial requests

### Check for Social Engineering

* Credential harvesting attempts
* Requests for sensitive information
* Poor grammar and spelling
* Unexpected attachments
* Suspicious URLs

---

⬆️ [Back to Table of Contents](#-table-of-contents)

---

# 🌍 2. IP Address Analysis

## 🎯 Objective

Determine whether the IP address is trusted, expected, suspicious, or malicious.

## 🛠 Tools Used

| Tool                                                | Purpose                 |
| --------------------------------------------------- | ----------------------- |
| [MxToolbox](https://mxtoolbox.com/)                 | DNS & IP Investigation  |
| [VirusTotal](https://www.virustotal.com/)           | Reputation Analysis     |
| [AbuseIPDB](https://www.abuseipdb.com/)             | Abuse Reports           |
| [DomainTools WHOIS](https://whois.domaintools.com/) | Infrastructure Research |

## 🔎 Initial Verification

### Questions to Ask

* Does the IP belong to the organization?
* Does the IP belong to a trusted vendor?
* Is communication expected?

### If YES

* Verify activity is legitimate.
* Document findings.
* Close the case if no malicious indicators exist.

### If NO

Proceed with full investigation.

## 📊 IP Reputation Analysis

### Review

* Geolocation
* ASN
* ISP
* Historical Reputation
* Threat Intelligence Reports

### Check Reputation Using

* VirusTotal
* AbuseIPDB

### Investigate Infrastructure Using

* DomainTools WHOIS
* MxToolbox

### Look For

* Malicious Reports
* Spam Activity
* Botnet Activity
* Known C2 Infrastructure
* Hosting Provider Reputation

---

⬆️ [Back to Table of Contents](#-table-of-contents)

---

# 🔗 3. URL Analysis

## 🎯 Objective

Determine whether a URL is benign, suspicious, or malicious.

## 🛠 Tools Used

### URL Reputation

* [VirusTotal](https://www.virustotal.com/)
* [BlueCoat Site Review](https://sitereview.bluecoat.com/)
* [Zscaler Zulu](https://zulu.zscaler.com/)

### Domain Intelligence

* [DomainTools WHOIS](https://whois.domaintools.com/)

### URL Sandbox Analysis

* [ANY.RUN](https://any.run/)
* [URLScan.io](https://urlscan.io/)

### Phishing Databases

* [URLHaus](https://urlhaus.abuse.ch/)
* [OpenPhish](https://openphish.com/)
* [PhishTank](https://phishtank.org/)

## 🌐 URL Reputation Analysis

### Check Using

* VirusTotal
* BlueCoat Site Review
* Zscaler Zulu

### Review

* Detection Count
* Vendor Classifications
* Website Category
* Reputation Score

## 🏢 Domain Intelligence

### Tool

* DomainTools WHOIS

### Review

* Domain Age
* Registration Date
* Registrar
* Registrant Details
* Historical WHOIS Records

### 🚩 Red Flags

* Newly Registered Domains
* Privacy-Protected Registration
* Typosquatting Domains
* Suspicious Registrars

## 🧪 URL Sandbox Analysis

### Tools

* ANY.RUN
* URLScan.io

### Look For

* Credential Harvesting Pages
* Fake Login Portals
* Redirect Chains
* Obfuscated JavaScript
* Malware Downloads
* Drive-by Downloads

## 🎣 Phishing Database Verification

### Tools

* URLHaus
* OpenPhish
* PhishTank

### Purpose

Determine whether the URL has been previously reported as:

* Phishing
* Malware Delivery
* Credential Theft
* Scam Infrastructure

---

⬆️ [Back to Table of Contents](#-table-of-contents)

---

# 📁 4. File Analysis

## 🎯 Objective

Determine whether an attachment or file is malicious.

## 🛠 Tools Used

| Tool                                      | Purpose                  |
| ----------------------------------------- | ------------------------ |
| [VirusTotal](https://www.virustotal.com/) | File Reputation Analysis |
| [ANY.RUN](https://any.run/)               | Dynamic Analysis         |

## 🔬 File Reputation Analysis

### Tool

* VirusTotal

### Review

* Detection Ratio
* File Type
* Community Comments
* Existing Threat Intelligence

## 🧪 Sandbox Analysis

### Tool

* ANY.RUN

### Check Process Activity

* Parent-Child Process Relationships
* PowerShell Execution
* CMD Execution
* Script Interpreters
* Process Injection Attempts

### Check File Activity

* File Creation
* File Deletion
* Dropped Payloads
* Temporary File Creation

### Check Network Activity

* DNS Requests
* HTTP/HTTPS Traffic
* Command-and-Control (C2) Communications
* Suspicious Domains
* Suspicious IP Addresses

### Check Registry Activity

* Run Keys
* Startup Entries
* Service Creation
* Registry Modifications

### Check Persistence

* Scheduled Tasks
* Services
* Startup Folder Entries

### Check Privilege Escalation

* New User Creation
* Administrative Access Changes
* UAC Bypass Attempts

---

⬆️ [Back to Table of Contents](#-table-of-contents)

---

# 🦠 5. Malware Analysis Resources

## 🛠 Tools Used

| Tool                                           | Purpose                      |
| ---------------------------------------------- | ---------------------------- |
| [VirusTotal](https://www.virustotal.com/)      | Reputation Analysis          |
| [ANY.RUN](https://any.run/)                    | Dynamic Malware Analysis     |
| [URLScan.io](https://urlscan.io/)              | URL Investigation            |
| [CyberChef](https://gchq.github.io/CyberChef/) | IOC Extraction & Decoding    |
| Zelster Malicious Website Lookup               | Malicious Website Validation |
## 🍳 CyberChef

Useful For:

* Base64 Decoding
* URL Decoding
* Hash Generation
* IOC Extraction
* Data Transformation
* Deobfuscation

---

⬆️ [Back to Table of Contents](#-table-of-contents)

---

# 🛠 6. Tools Reference

| Category            | Tool                                                     |
| ------------------- | -------------------------------------------------------- |
| Email Analysis      | [MxToolbox](https://mxtoolbox.com/)                      |
| Email Analysis      | [VirusTotal](https://www.virustotal.com/)                |
| Email Analysis      | [ANY.RUN](https://any.run/)                              |
| IP Analysis         | [MxToolbox](https://mxtoolbox.com/)                      |
| IP Analysis         | [VirusTotal](https://www.virustotal.com/)                |
| IP Analysis         | [AbuseIPDB](https://www.abuseipdb.com/)                  |
| Domain Intelligence | [DomainTools WHOIS](https://whois.domaintools.com/)      |
| URL Reputation      | [VirusTotal](https://www.virustotal.com/)                |
| URL Reputation      | [BlueCoat Site Review](https://sitereview.bluecoat.com/) |
| URL Reputation      | [Zscaler Zulu](https://zulu.zscaler.com/)                |
| URL Sandbox         | [ANY.RUN](https://any.run/)                              |
| URL Sandbox         | [URLScan.io](https://urlscan.io/)                        |
| Phishing Database   | [URLHaus](https://urlhaus.abuse.ch/)                     |
| Phishing Database   | [OpenPhish](https://openphish.com/)                      |
| Phishing Database   | [PhishTank](https://phishtank.org/)                      |
| File Reputation     | [VirusTotal](https://www.virustotal.com/)                |
| Malware Analysis    | [ANY.RUN](https://any.run/)                              |
| Malware Analysis    | Zelster Malicious Website Lookup                         |
| Utility             | [CyberChef](https://gchq.github.io/CyberChef/)           |

---

## 🎯 Recommended Tool Usage

| Investigation Type    | Recommended Tools                  |
| --------------------- | ---------------------------------- |
| Email Analysis        | MxToolbox, VirusTotal              |
| IP Investigation      | MxToolbox, VirusTotal, AbuseIPDB   |
| URL Investigation     | VirusTotal, BlueCoat, Zscaler Zulu |
| Domain Investigation  | DomainTools WHOIS                  |
| URL Behavior Analysis | ANY.RUN, URLScan.io                |
| Phishing Validation   | URLHaus, OpenPhish, PhishTank      |
| File Reputation       | VirusTotal                         |
| Malware Analysis      | ANY.RUN                            |
| IOC Decoding          | CyberChef                          |

---

⬆️ [Back to Table of Contents](#-table-of-contents)

---

# 🔗 7. Correlation and Validation

## 🎯 Objective

Correlate findings across multiple sources to determine whether the activity is benign, suspicious, or malicious.

---

## Correlate Findings Across

* Email
* Domain
* URL
* IP Address
* Attachment

---

## Questions to Answer

### Email

* Is the sender legitimate?
* Did SPF pass?
* Did DKIM pass?
* Did DMARC pass?
* Is the sender domain trusted?

### URL

* Is the URL malicious?
* Is the URL newly registered?
* Does the URL redirect to another website?
* Has the URL been reported previously?

### IP Address

* Is communication expected?
* Is the IP reported as malicious?
* Does the geolocation make sense?

### Attachment

* Is the file malicious?
* Does the file exhibit suspicious behavior?
* Does the file communicate externally?

---

## Important Note

> A clean VirusTotal result alone does **NOT** mean an indicator is safe.
>
> Always correlate findings across multiple sources before making a final determination.

---

## Final Validation Checklist

* [ ] Email Header Reviewed
* [ ] SPF Validated
* [ ] DKIM Validated
* [ ] DMARC Validated
* [ ] URL Reputation Checked
* [ ] Domain Investigated
* [ ] URL Sandbox Analysis Completed
* [ ] IP Reputation Checked
* [ ] Attachment Reputation Checked
* [ ] Attachment Sandbox Analysis Completed
* [ ] Findings Correlated
* [ ] Verdict Determined

---

⬆️ [Back to Table of Contents](#-table-of-contents)

---

# 🚦 8. Incident Classification

## 🟢 Benign

### Characteristics

* Legitimate Sender
* Trusted Domain
* Trusted Infrastructure
* No Malicious Detections
* Expected Business Activity

### Action

* Document Findings
* Close Case

---

## 🟡 Suspicious

### Characteristics

* Limited Reputation Data
* Newly Registered Domain
* Unusual Behavior
* Requires Additional Monitoring

### Action

* Continue Monitoring
* Escalate if Necessary
* Gather Additional Evidence

---

## 🔴 Malicious

### Characteristics

* Confirmed Phishing
* Malware Delivery
* Credential Harvesting
* Known Command-and-Control Activity
* Multiple Reputation Detections

### Action

* Block Indicators
* Quarantine Email
* Isolate Affected Host
* Reset Credentials if Required
* Escalate Incident

---

⬆️ [Back to Table of Contents](#-table-of-contents)

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

## Investigation Flow

```text
Email Received
        ↓
Header Analysis
        ↓
URL Analysis
        ↓
IP Analysis
        ↓
Attachment Analysis
        ↓
Correlation
        ↓
Verdict
        ↓
Response Action
```

---

⬆️ [Back to Table of Contents](#-table-of-contents)

---

# 🛡️ Think Before You Trust

> Trust is earned through verification.

---

## Disclaimer

This playbook is intended for educational purposes and SOC investigation workflows. Always follow your organization's incident response procedures and security policies when handling security incidents.

---

**Built for SOC Analysts, Incident Responders, and Threat Hunters.**
