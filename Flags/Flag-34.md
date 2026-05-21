# Flag 34 – Clearing Method Analysis

## Question
HUNT LEAD: "They cleared logs on every host. But not all the same way.
Which host had logs cleared from the console, and which had them cleared remotely?"

## Answer
WS-ENG04/SRV-DC01,SRV-FILES02

## Screenshot

![Flag 34 Clearing Method Analysis](../Screenshots/Flag-34-Clearing-Method-Analysis.pn)

## Finding
The investigation of log-clearing activity showed that WS-ENG04 had its Security logs cleared directly from the local console, while SRV-DC01 and SRV-FILES02 had logs cleared remotely through WMIC execution from the compromised beachhead host. This demonstrates coordinated anti-forensics activity across multiple systems intended to remove evidence and reduce visibility into attacker actions.
