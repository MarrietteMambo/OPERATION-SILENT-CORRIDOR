# Flag 22 – RDP Scope

## Question
HUNT LEAD: "That command wasn't their only way in. Pull the full picture from the attacker's tunnel.
Which hosts did they reach via that tunnel?"


## Answer
SRV-DC01, SRV-FILES02, WS-ENG04

## Finding
Investigation of VPN and endpoint activity confirmed that the attacker accessed multiple systems through the compromised tunnel session, including WS-ENG04, SRV-DC01, and SRV-FILES02. This activity demonstrates successful lateral movement from the initial beachhead workstation to high-value infrastructure systems, indicating expansion of access and progression of the compromise within the environment.



