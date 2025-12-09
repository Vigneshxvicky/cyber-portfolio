 Fail2ban SSH Brute-Force Detection & Auto-Blocking (SOC Project)
1. Overview

This project demonstrates how Fail2ban automatically detects and blocks SSH brute-force attacks on a Linux system.
Kali A acts as the victim server, Kali B acts as the attacker.

This replicates a real-world SOC scenario.

2. Environment Setup

Victim: Kali Linux (SSH server)

Attacker: Kali Linux (SSH brute-force)

Defense: Fail2ban with systemd backend

3. Attack Simulation

A brute-force attack was executed from Kali B:

for i in {1..10}; do ssh labuser@<victim-ip> <<< "wrong"; done


This generated multiple failed login attempts in quick succession.

4. Fail2ban Detection

Fail2ban monitored authentication logs via systemd:

backend = systemd
maxretry = 3
bantime = 600


After 3 failed attempts, Fail2ban banned the attacker IP.

5. Evidence (Screenshots)

Brute-force attempts captured in logs

Fail2ban reporting banned IP

SSH connection blocked from attacker machine

6. SOC Findings

The attacker repeatedly attempted login with incorrect passwords.

Fail2ban correctly detected the intrusion pattern.

The attacker IP was banned for 600 seconds.

SSH access from the attacker was completely blocked.

Detection was based on the systemd journal logs.

7. Recommendations

Enable Fail2ban on all production Linux servers

Disable password authentication (use SSH keys)

Limit SSH access by IP

Change default SSH port

Deploy real-time alerting (Wazuh/Splunk)

8. Conclusion

This project demonstrates hands-on threat detection and automated response for SSH brute-force attacks.
It replicates real SOC workflows and strengthens cybersecurity defense skills.
