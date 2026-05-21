# Flag 38 – CISO Brief

## Question
HUNT LEAD: "Hunt's over. Hofmann needs your findings before the board meeting.
Your brief must name:
-	Both compromised user accounts
-	The compromised hosts (at least one by name)
-	The data targeted and how it left the network
-	The persistence mechanism that survives credential resets
-	One immediate containment action
Write it up."

## Answer
The investigation confirmed compromise of the user accounts s.brandt and m.richter, which were used to conduct credential theft and lateral movement activity. The attacker established a beachhead on WS-ENG04 and later pivoted to critical systems including SRV-DC01 and SRV-FILES02. Sensitive avionics data from C:\Engineering\Avionics\A400M_NavSys was collected, compressed into win_update_kb5034.zip, encoded with certutil, and exfiltrated via PowerShell Invoke-WebRequest to cdn-telemetry.cloud-endpoint.net. Persistence was maintained through netsh interface portproxy configurations stored in the Windows PortProxy registry path, allowing access to survive even after credential resets. An immediate containment action should include isolating WS-ENG04, removing all PortProxy configurations, and disabling the compromised accounts to stop further attacker activity.


