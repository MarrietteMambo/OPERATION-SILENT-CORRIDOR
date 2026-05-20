# Flag 12 – Stored Credential Source

## Question
HUNT LEAD: "Memory wasn't their only target. What else did they go after on this host?"

## Answer
SAM


## Finding
The attacker attempted to export the SAM registry hive on WS-ENG04 using a registry save command. This indicates credential access activity because the SAM hive stores local account password hashes, which attackers may try to extract and crack offline.

