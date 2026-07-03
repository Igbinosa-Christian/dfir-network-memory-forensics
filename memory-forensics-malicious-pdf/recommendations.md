# Recommendations – Malicious PDF / Zeus Banking Trojan

## Immediate Containment
- Isolate the infected host (192.168.0.176) from the network immediately to prevent further C2 communication and lateral movement.
- Block outbound connections to 212.150.164.203 and 193.104.22.71 at the perimeter firewall.
- Terminate and quarantine AcroRd32.exe (PID 1752), firefox.exe (PID 888), and svchost.exe (PID 1384).

## What to Block
- IP addresses: 212.150.164.203, 193.104.22.71
- Domains: search-network-plus.com
- URLs containing `/~produkt/` path pattern — consistent with known Zeus C2 directory structure

## Credential Reset
- Reset passwords for all accounts on the infected host, starting with the Administrator account.
- Assume banking credentials accessed by the compromised user (smalls.hammish) are compromised — notify relevant financial institutions.

## What to Hunt For
- Other hosts in the environment with outbound connections to 212.150.164.203 or 193.104.22.71
- Processes with RWX memory regions spawned by browser or document reader processes (malfind pattern)
- svchost.exe instances with unusual parent processes or start times out of sync with system boot

## Remediation
- Reimage the affected host — memory injection at this level cannot be safely cleaned.
- Update Adobe Reader and Firefox to current versions to close the exploit vector.
- Deploy email and web filtering rules to block malicious PDF delivery via browser downloads.

## MITRE ATT&CK Coverage Gaps
- T1566.001 (Phishing): Implement attachment sandboxing at the email gateway.
- T1055 (Process Injection): Deploy EDR with memory scanning capability to detect RWX injection patterns at runtime.
- T1071.001 (C2 over HTTP): Implement SSL inspection and anomalous outbound traffic alerting on the SIEM.
