# Detection Gaps

The investigation identified multiple security and visibility gaps that enabled the attacker to progress through the environment, establish persistence, and successfully exfiltrate sensitive information. While telemetry sources such as Sysmon and Microsoft Defender for Endpoint preserved evidence, several control weaknesses reduced the organization’s ability to detect or prevent malicious activity.

## 1. Inadequate Detection of Suspicious VPN Activity

The compromised account `s.brandt` authenticated through multiple external IP addresses, including anonymization infrastructure and Tor-related activity. Existing controls failed to identify the abnormal login pattern and unusual number of internal systems accessed.

**Gap:** Remote access monitoring lacked behavioral analytics and IP reputation enrichment.

**Impact:** Allowed unauthorized access and initial attacker foothold establishment.

---

## 2. Credential Access Activity Was Not Prevented

The attacker targeted `lsass.exe`, attempted SAM extraction, enumerated stored credentials using `cmdkey /list`, and later obtained additional credentials belonging to `m.richter`.

**Gap:** Credential access behavior was logged but not blocked or escalated.

**Impact:** Enabled privilege escalation and credential reuse across systems.

---

## 3. WMIC Remote Execution Was Not Flagged

The attacker repeatedly used:

```text
wmic process call create
```

to execute commands on remote systems.

**Gap:** Legitimate administrative tools were not monitored for abnormal usage patterns.

**Impact:** Enabled stealthy lateral movement into critical infrastructure systems.

---

## 4. PortProxy Persistence Was Not Detected

Attackers established covert network redirection using:

```text
netsh interface portproxy add v4tov4
```

with persistence stored in:

```text
HKLM\SYSTEM\CurrentControlSet\Services\PortProxy\v4tov4\tcp
```

**Gap:** Registry persistence monitoring was insufficient.

**Impact:** Allowed access paths to survive reboots and credential changes.

---

## 5. Data Collection and Exfiltration Occurred Successfully

Sensitive avionics material was compressed, encoded, and transmitted externally through PowerShell.

Observed tools:

- `Compress-Archive`
- `certutil`
- `Invoke-WebRequest`

**Gap:** Data Loss Prevention (DLP) and outbound traffic inspection controls were ineffective.

**Impact:** Intellectual property was successfully removed from the environment.

---

## 6. Log Clearing Activity Was Not Immediately Escalated

The attacker executed:

```text
wevtutil cl Security
```

across multiple systems and later removed staging artifacts.

**Gap:** Log clearing and anti-forensics activity did not trigger immediate response actions.

**Impact:** Increased risk of evidence destruction and delayed incident visibility.

---

## 7. Endpoint Security Detected but Did Not Prevent Activity

`MsMpEng.exe` interacted with staged credential artifacts including `ntds.dit` and `SYSTEM`; however, no preventative action occurred.

**Gap:** Security tooling observed activity without automated response enforcement.

**Impact:** Credential theft and Active Directory collection continued successfully.


