# Flag 35 – Surviving Log Source

## Question
HUNT LEAD: "They wiped logs on every host we've investigated. And yet we're still here.
Why? What did they miss?"


## Answer
Sysmon


## Finding
The Investigation determined that although the attacker cleared Windows Security logs across compromised hosts using wevtutil cl Security, they failed to remove Sysmon telemetry. Because Sysmon continued recording detailed endpoint activity—including process execution, file operations, registry changes, and network behavior—investigators retained visibility into the attack lifecycle. This oversight allowed reconstruction of credential theft, lateral movement, persistence, and data exfiltration activities despite the attacker’s anti-forensics efforts.


