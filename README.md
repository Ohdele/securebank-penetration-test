# SecureBank Penetration Test
Objective: Demonstrate core skills in web application testing, privilege escalation assessment, and professional documentation on a vulnerable VM (DVWA).

## Section 1. Setup & Asset Discovery
* **Target IP:** 192.168.56.103
* **Services:** Apache/2.4.52, OpenSSH 8.9p1, MariaDB 10.6.22

[**View Output in proof_log.txt**](outputs/proof_log.txt)

---

## Sections 2-4. Web Application Vulnerability Confirmation
* **Activities:** Manual testing and Burp Suite were used inside the DVWA interface.
* **Confirmed VULNERABILITIES:**
    * **SQL Injection (A03):** Confirmed input validation failure on the login page.
    * **Command Injection (A03):** Confirmed successful command execution (`uid=33(www-data)`).
    * **Insecure Design (A04):** Confirmed Unrestricted File Upload vulnerability.

[**View Output in proof_log.txt**](outputs/proof_log.txt)

---

## Section 5. Exploitation & Foothold
* **Objective:** Achieve initial access via Command Injection.
* **Result:** Confirmed code execution as `www-data` user via `curl` command.

[**View Exploitation Logs in log_05_exploitation.txt**](outputs/log_05_exploitation.txt)

---

## Section 6. Privilege Escalation Assessment
* **Objective:** Assess vulnerability to local privilege escalation (LPE).
* **Findings (Hands-On):**
    * **Vulnerability:** Target is running Polkit `pkexec` version **0.105**.
    * **Conditions:** The SUID bit is active (`-rwsr-xr-x`), confirming exposure to **PwnKit (CVE-2021-4034)**.
    * **Action:** The full exploit chain was documented, but the final, destructive exploit was **NOT** executed.

[**View Assessment Logs in prooflog_06.txt**](outputs/prooflog_06.txt)

---

## Final Output
This project demonstrates expertise in: vulnerability confirmation, initial access, LPE assessment, evidence capture, and documentation.
* **Full Report/Evidence:** The entire report structure, commands, logs, findings, and final documentation are contained directly in this repository's files.
