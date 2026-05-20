# Flag 14 – First Lateral Pivot

## Question
HUNT LEAD: "They have credentials. They have targets.
Reconstruct the first pivot. The originating tunnel address, the host they reached, and the account they used."

## Answer
10.1.96.114/SRV-DC01/user:m.richter 

## Finding
Analysis of VPN and process execution telemetry reconstructed the attacker’s first confirmed lateral movement activity following compromise of the beachhead workstation WS-ENG04. Review of FortiGateVPN logs identified the tunnel IP address 10.1.96.114 as the active internal VPN-assigned address associated with the malicious session during the attack window. Correlation of this activity with process execution logs showed the attacker subsequently pivoted to the domain controller SRV-DC01 using the credentials of m.richter. The activity was observed through administrative access commands including: net use \\SRV-DC01\C$ /user:m.richter Haldric2025SecIT. This sequence demonstrates that the attacker progressed beyond initial VPN access and successfully leveraged additional credentials to move laterally toward high-value infrastructure. The use of an administrative share (C$) and alternate credentials indicates credential theft and unauthorized privilege expansion, consistent with tactics used by advanced persistent threat actors to establish deeper access and position themselves for credential harvesting and data theft.

