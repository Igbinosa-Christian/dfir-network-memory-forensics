# Recommendations – TrickBot Network Forensics

## Immediate Containment
- Block all outbound traffic to identified C2 servers at the perimeter firewall:
  - 196.45.140.146 (TCP/449)
  - 118.69.133.4 (TCP/447)
  - 23.160.192.125 (TCP/447)
- Block the payload delivery domain: cahrhomeopathy.com (43.240.64.184)
- Isolate the infected host (10.12.19.104 / DESKTOP-3kI6Y6G) immediately.

## What to Block
- SHA256 hash of TrickBot payload: `da1ae69acf1b97bfac587addc9266155342bf8f2a7a80e0d09df9a577c39f7f9`
- Outbound TLS connections to non-standard ports (447, 449) from workstations
- TLS certificates with issuer "Internet Widgits Pty Ltd" — known TrickBot default certificate pattern

## What to Hunt For
- Other hosts in the environment with TLS handshakes to port 447 or 449
- HTTP GET requests for files with image extensions (.png, .jpg) that return PE32 executables
- TLS certificates with generic or randomised issuer organisation names across the environment

## Remediation
- Reimage the affected host — TrickBot achieves deep persistence and cannot be safely cleaned.
- Reset credentials for user smalls.hammish across all systems.
- Review IDS/IPS rules to alert on TrickBot certificate fingerprints and non-standard TLS ports.

## MITRE ATT&CK Coverage Gaps
- T1071.001 (C2 over HTTP/S): Deploy SIEM rules to alert on anomalous outbound HTTP from workstations outside business hours.
- T1036.005 (Masquerading): Implement file type validation at the proxy — block executables served with image MIME types.
- T1573.001 (Encrypted C2): Enable SSL inspection on outbound traffic and alert on TLS to non-standard ports from endpoints.
