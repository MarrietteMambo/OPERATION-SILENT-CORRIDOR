# MITRE ATT&CK Mapping


This section maps observed GREY VEIL activity to the MITRE ATT&CK framework based on evidence collected from Microsoft Sentinel, KQL hunting, FortiGate VPN telemetry, Microsoft Defender for Endpoint, and Sysmon logs.

| Tactic | Technique | ID | Evidence Observed |
|----------|-------------|------|------------------|
| Initial Access | External Remote Services | T1133 | Compromised VPN account `s.brandt` authenticated through FortiGate SSL VPN infrastructure |
| Initial Access | Valid Accounts | T1078 | Abuse of legitimate credentials belonging to `s.brandt` and `m.richter` |
| Discovery | System Information Discovery | T1082 | `systeminfo.exe` executed on `WS-ENG04` |
| Discovery | Domain Account Discovery | T1087.002 | `net group "Domain Admins" /dom` |
| Discovery | Domain Account Discovery | T1087.002 | `net group "Enterprise Admins" /dom` |
| Discovery | Remote System Discovery | T1018 | Enumeration and interaction with `SRV-DC01` and `SRV-FILES02` |
| Credential Access | OS Credential Dumping | T1003 | `tasklist /fi "imagename eq lsass.exe"` targeting LSASS |
| Credential Access | Security Account Manager | T1003.002 | `reg save HKLM\SAM C:\Windows\Temp\sam.bak` |
| Credential Access | Credentials from Password Stores | T1555 | `cmdkey /list` enumeration |
| Credential Access | NTDS | T1003.003 | `ntdsutil` used to create a copy of `ntds.dit` |
| Lateral Movement | Windows Management Instrumentation | T1047 | `wmic process call create` remote execution |
| Lateral Movement | SMB/Windows Admin Shares | T1021.002 | `net use \\SRV-DC01\C$ /user:m.richter` |
| Collection | Data from Local System | T1005 | Access to `C:\Engineering\Avionics\A400M_NavSys` |
| Collection | Archive Collected Data | T1560.001 | `Compress-Archive` created `win_update_kb5034.zip` |
| Defense Evasion | Masquerading | T1036 | `McAfee_Logs` and `win_update_kb5034.zip` used to blend with legitimate activity |
| Defense Evasion | Indicator Removal on Host | T1070.001 | `wevtutil cl Security` |
| Defense Evasion | File and Directory Removal | T1070.004 | `rmdir /s /q C:\Windows\Temp\McAfee_Logs` |
| Persistence | Proxy: Internal Proxy | T1090 | `netsh interface portproxy add v4tov4` |
| Persistence | Modify Registry | T1112 | PortProxy registry modifications |
| Command and Control | Application Layer Protocol | T1071 | HTTP POST communications |
| Exfiltration | Exfiltration Over Web Services | T1567 | `Invoke-WebRequest` to `cdn-telemetry.cloud-endpoint.net` |
| Exfiltration | Data Encoding | T1132 | `certutil -encode` created `win_update_kb5034.b64` |
| Impact / Anti-Forensics | Clear Windows Event Logs | T1070.001 | Security logs cleared across multiple hosts |

```
# Key Observation

The attacker attempted anti-forensics by clearing Windows Security logs but failed to remove Sysmon telemetry. This allowed investigators to reconstruct credential theft, persistence, lateral movement, and exfiltration activity despite attempts to erase evidence.
