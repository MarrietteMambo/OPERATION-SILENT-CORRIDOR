# Flag 28 – Compression Method

## Question
HUNT LEAD: "How was it created?"

## Answer
Compress-Archive


## Finding
The investigation revealed that the attacker targeted the C:\Engineering\Avionics\A400M_NavSys directory and used the PowerShell Compress-Archive cmdlet to package its contents into win_update_kb5034.zip, a filename disguised to appear as a legitimate Windows update file. The archive was later encoded and cleaned up, indicating a deliberate process of staging sensitive avionics data for potential exfiltration. This activity aligns with GREY VEIL’s objective of intellectual property theft and demonstrates a clear attempt to collect and prepare classified engineering material for removal from the environment.



