# NIST SP 800-61 Application

The GREY VEIL investigation closely aligns with the incident response lifecycle outlined in NIST SP 800-61 (Computer Security Incident Handling Guide). The framework organizes response activities into Preparation, Detection and Analysis, Containment/Eradication/Recovery, and Post-Incident Activity.

| NIST Phase | Application to Investigation |
|---|---|
| Preparation | Microsoft Sentinel, Sysmon, FortiGate VPN logs, and Microsoft Defender for Endpoint telemetry were configured and available before the incident, enabling visibility and investigation capabilities. |
| Detection and Analysis | Threat hunting activities identified suspicious VPN activity involving `s.brandt`, anomalous IP usage, credential theft behavior, lateral movement, persistence mechanisms, and exfiltration activity. KQL queries and telemetry correlation were used to reconstruct the attack timeline. |
| Containment, Eradication, and Recovery | Recommended actions included isolating `WS-ENG04`, `SRV-DC01`, and `SRV-FILES02`, disabling compromised accounts `s.brandt` and `m.richter`, removing PortProxy persistence, blocking external communication, and rebuilding affected systems where necessary. |
| Post-Incident Activity | Detection gaps were identified, including insufficient monitoring of WMIC, PortProxy persistence, and exfiltration activity. Lessons learned emphasized centralized telemetry, Sysmon logging, stronger authentication controls, and improved detection engineering. |

The investigation demonstrated the importance of layered visibility and centralized logging. Although the attacker attempted anti-forensics actions by clearing Windows Security logs, Sysmon telemetry preserved evidence and enabled complete reconstruction of the attack lifecycle.
