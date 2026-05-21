# Flag 31 – External Destination

## Question
HUNT LEAD: "Where did it go?"

## Answer
cdn-telemetry.cloud-endpoint.net


## Finding
The Investigation confirmed successful data exfiltration activity through PowerShell Invoke-WebRequest. The attacker transmitted the Base64-encoded archive win_update_kb5034.b64 to the external domain: cdn-telemetry.cloud-endpoint.net.The domain name was designed to resemble legitimate cloud or telemetry-related traffic, likely to avoid suspicion and blend into normal network activity. Before transmission, the attacker compressed sensitive avionics data into win_update_kb5034.zip, encoded it into a .b64 file, and then used an HTTP POST request to send the data externally. This sequence confirms a complete collection and exfiltration workflow and strongly supports GREY VEIL’s objective of stealing intellectual property from the environment.



