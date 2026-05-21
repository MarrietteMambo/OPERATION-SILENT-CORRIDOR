# Flag 32 – Reentry Window

## Question
HUNT LEAD: "There's activity from the same account on the beachhead after the exfil date. They came back.
How long did they wait?"

## Answer
2 days

## Screenshot
![Flag 32 Reentry window](../Screenshot/Flag-32-Reentry-Window.png)


## Finding
The Timeline analysis identified additional activity associated with the compromised account s.brandt on the beachhead workstation WS-ENG04 following the initial exfiltration event. After successfully collecting and transmitting sensitive avionics data on 2026-02-28, the attacker returned and resumed activity on 2026-03-02, indicating a delay of 2 days between operations. This gap suggests the attacker maintained access and intentionally paused activity before re-engaging the environment..



