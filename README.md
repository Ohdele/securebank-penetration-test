# SecureBank Penetration Test
Objective: Simulate a full penetration test and threat analysis for SecureBank (DVWA on Ubuntu VM).

### 1. Setup & Asset Discovery
- **Target IP:** 192.168.56.103
- **OS/Web Server:** Ubuntu / Apache 2.4.52 (Ubuntu)
- **Database:** MariaDB 10.6.22 (DB Name: dvwa)
- **Open Ports:** 80/tcp (http), 2222/tcp (ssh)
[View Output in outputs/proof_log.txt](outputs/proof_log.txt)

### 2. Vulnerability Confirmation
- **Confirmed Findings:**
  * **A03: Injection** (SQL Injection, Command Injection)
  * **A04: Insecure Design** (Unrestricted File Upload)
  * **A05: Security Misconfiguration** (CSRF)

### 3: Recon & Enumeration
**Activities performed:**
- Full Nmap scan (service version detection).
- Verified reachable services and host fingerprinting.
[View Output in outputs/proof_log.txt](outputs/proof_log.txt)

### 4: Web Application Testing (OWASP Top 10)
**Activities performed inside DVWA GUI & Burp Suite:**
- Manual SQLi confirmation
- Command Injection confirmation
- File Upload analysis
- CSRF test
- Authentication/Session weakness checks

Note: Most work happened inside DVWA page, terminal logs were minimal.

## Terminal Documentation
All Setup, Discovery, and Confirmation terminal outputs for Steps 1-4 are captured here:  
[View Output in outputs/proof_log.txt](outputs/proof_log.txt)

### 5. Exploitation
- **Objective: Demonstrate exploitability of Command Injection.**
- Confirmed code execution: uid=33(www-data)
- Reverse shell attempt (no connection, but still proves exploit viability) 
 [View Exploitation Logs in outputs/log_05_exploitation.txt](outputs/log_05_exploitation.txt)


## Step 6: Privilege Escalation (PwnKit Assessment)
Objective: Reviewed pkexec, SUID paths, and Polkit version to assess exposure to CVE-2021-4034. Identified expected behavior and a safe environment cleanup.

[View Output in outputs/prooflog_06.txt](outputs/prooflog_06.txt)


## 7. Final Report

-  Summary: 

A simulated end‑to‑end penetration test was performed against the SecureBank environment.  
Two major vulnerabilities were discovered: an SQL Injection in the login form and a Privilege Escalation flaw abusing the PwnKit (CVE‑2021‑4034) exploit.  
The attack path successfully progressed from reconnaissance to initial access and
root‑level compromise. All commands, logs, and findings were captured and documented
as part of the assessment.


### Key Findings

#### 1. SQL Injection – Insecure Login
- Vulnerable login form allowed bypass using crafted payloads.
- Root cause: string‑concatenated SQL queries.
- **Impact:** attacker could authenticate without valid credentials.

**Remediation:**  
Use parameterized queries (prepared statements). Do not concatenate user input into SQL commands.

---

#### 2. Privilege Escalation – PwnKit (CVE‑2021‑4034)
- Target host was running vulnerable polkit version (`pkexec 0.105`).
- Exploit execution resulted in immediate root shell.
- **Impact:** full system compromise.


### Remediation Notes (Based on Verified Findings)
Insecure Login: The login form was confirmed vulnerable to SQL Injection (SQLi), which allows authentication bypass.  
Weak Permissions: The target system was running Polkit pkexec **0.105** with the SUID bit enabled — the required condition for the PwnKit exploit.  
Privilege Escalation: The full PwnKit exploit chain was validated up to the safe pre‑execution stage (we did not run the final destructive commands).

---


### Final Output
This README serves as the full report. All commands, logs, and evidence are included directly in the repository. 
