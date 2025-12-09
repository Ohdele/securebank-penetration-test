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

[View Output in outputs/prooflog_06.txt]
