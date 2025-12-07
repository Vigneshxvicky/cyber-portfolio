---

## Project 3 : SSH Brute Force Incident Response (Home Lab)

### 🔍 Project Overview
In this project, I simulated a brute-force attack on a Linux server to understand the "Blue Team" perspective of detection and analysis. I utilized a Kali Linux attacker machine to target a victim instance, then switched roles to investigate the logs and document the incident.

* **Tools Used:** `journalctl`, `grep`, SSH, Kali Linux.
* **Skills Demonstrated:** Log Analysis, Incident Documentation (NIST), Linux Hardening.

### 🕵️‍♂️ Investigation & Analysis
Using the command `sudo journalctl | grep "Failed password"`, I identified a high volume of failed login attempts targeting the user `labuser`.

**Key Findings from Log Analysis:**
* **Attacker IP:** `192.168.31.235` (Internal Network)
* **Target:** `labuser` on Port 22
* **Outcome:** The logs revealed a successful compromise at **18:18:10** where the "Accepted password" log appeared immediately after a sequence of failures.

### 📸 Evidence
*Figure 1: System logs showing repeated authentication failures followed by a successful login event.*

![SSH Brute Force Logs](Evidence-1.jpg)

### 📂 Deliverables
* [View Full Incident Response Report (PDF)](SSH_Brute_Force_Report.pdf)
