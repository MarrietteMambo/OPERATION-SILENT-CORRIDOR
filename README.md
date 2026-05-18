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
