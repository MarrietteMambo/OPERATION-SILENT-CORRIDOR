# Flag 36 – Exfiltration Confidence Call

## Question
HUNT LEAD: "Before we close, give me your confidence call on the data theft.
Was sensitive data successfully exfiltrated? Rate your confidence and provide three pieces of evidence to support it."


## Answer
HIGH. Sensitive data was successfully exfiltrated. Evidence shows the attacker compressed contents from C:\Engineering\Avionics\A400M_NavSys using Compress-Archive into win_update_kb5034.zip, encoded the archive with certutil into win_update_kb5034.b64, and transmitted it externally through Invoke-WebRequest using an HTTP POST request to cdn-telemetry.cloud-endpoint.net.


## Finding
The Assessment of the intrusion indicates high confidence that sensitive data was successfully exfiltrated. Evidence showed the attacker collected files from C:\Engineering\Avionics\A400M_NavSys, packaged them into win_update_kb5034.zip, encoded the archive using certutil, and transmitted the resulting file to cdn-telemetry.cloud-endpoint.net through a PowerShell HTTP POST request. This sequence demonstrates a complete and successful data collection and exfiltration workflow.


