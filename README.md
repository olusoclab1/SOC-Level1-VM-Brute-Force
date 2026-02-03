# 🛡️ SOC-Level1-VM-Brute-Force
This project demonstrates the detection, investigation, and response to brute force login attempts against a Windows virtual machine using Microsoft Defender for Endpoint (MDE), KQL, and Microsoft Sentinel.

---
## Summary

This lab demonstrates how a SOC Level 1 analyst detects, investigates, and responds to brute force login attempts against a Windows endpoint using Microsoft Defender for Endpoint and Microsoft Sentinel

The goal is to simulate a real-world SOC workflow: attack simulation → detection → investigation → alerting → response → MITRE mapping.


# 🎯 Lab Environment

- Azure Windows Virtual Machine
- Microsoft Defender for Endpoint (MDE)
- Microsoft Sentinel
- Log source: DeviceLogonEvents

<img width="700" height="400" alt="5" src="https://github.com/user-attachments/assets/21a40afb-0de3-4d20-895c-82fae9a19626" />


---


# 🎯 Attack Simulation

After onboarding the VM to MDE, I simulated a brute force attack by attempting multiple failed logins using incorrect passwords from two different external IP addresses.

This activity was designed to generate realistic authentication telemetry for detection and investigation.

---


# 🎯 Detections

Repeated failed logon attempts from the same external IP addresses within a short time window were identified using KQL.

Detection evidence:

<img width="700" height="400" alt="4" src="https://github.com/user-attachments/assets/cc5fe517-7273-455e-a5c4-2a9524e91d4e" />


---


# 🎯 Investigation

The following questions were addressed during investigation:

- Were the source IPs internal or external?
-  Did any successful logons occur after failures?
-  Was a specific account targeted?

Authentication logs were reviewed to validate impact.

** Investigation evidence: **

<img width="700" height="700" alt="3" src="https://github.com/user-attachments/assets/bb57081f-95e8-4e2f-b87a-57fa2359fba3" />

--- 


# 🎯 Threat Intelligence

Source IP addresses were enriched using AbuseIPDB and confirmed to have a malicious reputation related to brute force activity.

Threat intelligence evidence:

<img width="650" height="345" alt="2" src="https://github.com/user-attachments/assets/d5791ba7-9eb6-47ca-b09b-d03b32ad15a3" />


---


# 🎯 Investigation Result

No successful logons were identified. The brute force attempt did not result in account compromise.

---


# 🎯 Sentinel Rule Configuration

A Microsoft Sentinel analytics rule was created to alert on brute force authentication patterns.

<img width="700" height="500" alt="1" src="https://github.com/user-attachments/assets/b9d4b90b-4e05-42b3-beb8-cdaf15633454" />


---


# 🎯 🏷️ MITRE ATT&CK Mapping

MITRE ATT&CK Mapping

- T1110 – Brute Force
- T1110.003 – Password Spraying
- T1078 – Valid Accounts (conditional)

--- 


# 🎯 Response Actions

- Block malicious IP addresses (Firewall / NSG)
- Review authentication activity for lateral movement
- Reset or disable targeted accounts if required
- Enforce MFA and account lockout policies


---

# 🎯 Skills Demonstrated

- KQL log analysis
- SOC alert triage
- Threat intelligence enrichment
- MITRE ATT&CK mapping
- Incident response decision-making
