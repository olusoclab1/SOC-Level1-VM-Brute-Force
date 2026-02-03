# SOC-Level1-VM-Brute-Force
A hands-on SOC project focused on identifying and remediating brute-force authentication attacks on virtual machines using security logs and incident response procedures.

---


# 🎯 Lab Environment

    Azure Windows Virtual Machine
    Microsoft Defender for Endpoint (MDE)
    Microsoft Sentinel
    Log source: DeviceLogonEvents

image

---


# 🎯 Attack Simulation

After onboarding the VM to MDE, I simulated a brute force attack by attempting multiple failed logins using incorrect passwords from two different external IP addresses.

This activity was designed to generate realistic authentication telemetry for detection and investigation.

---


# 🎯 Detections

Repeated failed logon attempts from the same external IP addresses within a short time window were identified using KQL.

Detection evidence:
image


---


# 🎯 Investigation

The following questions were addressed during investigation:

    Were the source IPs internal or external?
    Did any successful logons occur after failures?
    Was a specific account targeted?

Authentication logs were reviewed to validate impact.

** Investigation evidence: **
image

--- 


#🎯 Threat Intelligence

Source IP addresses were enriched using AbuseIPDB and confirmed to have a malicious reputation related to brute force activity.

Threat intelligence evidence:
Screenshot 2026-01-27 at 4 27 09 PM

---


# 🎯 Investigation Result

No successful logons were identified. The brute force attempt did not result in account compromise.

---


# 🎯 Sentinel Rule Configuration

A Microsoft Sentinel analytics rule was created to alert on brute force authentication patterns.
image

---


# 🎯 🏷️ MITRE ATT&CK Mapping

MITRE ATT&CK Mapping

    T1110 – Brute Force
    T1110.003 – Password Spraying
    T1078 – Valid Accounts (conditional)

--- 


# 🎯 Response Actions

    Block malicious IP addresses (Firewall / NSG)
    Review authentication activity for lateral movement
    Reset or disable targeted accounts if required
    Enforce MFA and account lockout policies


---

# 🎯 Skills Demonstrated

    KQL log analysis
    SOC alert triage
    Threat intelligence enrichment
    MITRE ATT&CK mapping
    Incident response decision-making
