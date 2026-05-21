# OPERATION-SILENT-CORRIDOR
Threat hunting case study using Microsoft Sentinel, KQL, and MITRE ATT&amp;CK.
# Executive Summary

This threat hunt investigated suspected GREY VEIL activity targeting Haldric Aerospace using Microsoft Sentinel, KQL, FortiGate VPN logs, Microsoft Defender for Endpoint, and Sysmon telemetry. Analysis identified compromise of the s.brandt and m.richter accounts, leading to lateral movement from WS-ENG04 to critical systems including SRV-DC01 and SRV-FILES02. The attacker conducted credential theft, established persistence using netsh interface portproxy, and targeted sensitive avionics data from C:\Engineering\Avionics\A400M_NavSys. Data was compressed, encoded, and exfiltrated to cdn-telemetry.cloud-endpoint.net. Despite log clearing attempts, Sysmon telemetry preserved visibility and enabled reconstruction of the complete attack lifecycle.
## Hunt Objectives

- Identify compromised user accounts and affected systems  
- Investigate suspicious VPN and remote access activity  
- Reconstruct attacker behavior and attack timeline  
- Detect credential theft and lateral movement techniques  
- Identify persistence and anti-forensics mechanisms  
- Determine whether sensitive data was successfully exfiltrated  
- Map attacker activity to MITRE ATT&CK techniques  
- Identify detection gaps and provide security recommendations

## Overview
This project documents a threat hunting investigation involving GREY VEIL activity against Haldric Aerospace. The investigation used Microsoft Sentinel, KQL, Sysmon, Microsoft Defender for Endpoint telemetry, and FortiGate VPN logs.

## Compromised Accounts
- s.brandt
- m.richter

## Compromised Hosts
- WS-ENG04
- SRV-DC01
- SRV-FILES02

## Key Findings
- VPN account compromise
- Credential theft
- WMIC lateral movement
- PortProxy persistence
- Sensitive avionics data exfiltration
- Log clearing and anti-forensics

## Tools and Data Sources
- Microsoft Sentinel
- KQL
- Sysmon
- FortiGateVPN
- DeviceProcessEvents
- DeviceFileEvents
- DeviceRegistryEvents
- DeviceNetworkEvents

## Investigation Sections
- [Flag-by-Flag Investigation](Flags/README.md)
- [MITRE ATT&CK Mapping](MITRE/README.md)
- [NIST-800-61-Application](NIST-800-61-Application.md)
- [Detection Gaps](Detection-Gaps/README.md)
- [Recommendations](Recommendations.md)

## Lessons Learned

This investigation demonstrated how attackers can successfully chain together credential theft, reconnaissance, lateral movement, persistence, and exfiltration techniques while attempting to remove evidence through anti-forensics actions. Although Windows Security logs were cleared, Sysmon telemetry and centralized logging preserved critical visibility and enabled complete reconstruction of the attack lifecycle. The hunt highlighted the importance of layered detection strategies, behavioral analytics, and monitoring of legitimate administrative tools abused for malicious purposes. Future improvements should focus on strengthening identity protection, detecting persistence mechanisms, and improving response automation to reduce dwell time and prevent successful data theft.

