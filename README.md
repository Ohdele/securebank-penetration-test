# SecureBank Penetration Test
Objective: Simulate a full penetration test and threat analysis for SecureBank (DVWA on Ubuntu VM).

## Status: Steps 1-4 Complete (Discovery & Confirmation)

### 1. Setup & Asset Discovery
-   **Target IP:** 192.168.56.103
-   **OS/Web Server:** Ubuntu / Apache 2.4.52 (Ubuntu)
-   **Database:** MariaDB 10.6.22 (DB Name: dvwa)
-   **Open Ports:** 80/tcp (http), 2222/tcp (ssh)

### 2. Vulnerability Confirmation
-   **Confirmed Findings:**
    * **A03: Injection** (SQL Injection, Command Injection)
    * **A04: Insecure Design** (Unrestricted File Upload)
    * **A05: Security Misconfiguration** (CSRF)

## Terminal Documentation
All Setup, Discovery, and Confirmation terminal outputs are captured here:
[View Output in outputs/proof_log.txt](outputs/proof_log.txt)

### Next Step: Exploitation
(Paused until ready.)
