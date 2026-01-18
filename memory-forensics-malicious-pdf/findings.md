## Key Findings

### Initial Infection
- The initial exploit was traced to **AcroRd32.exe (PID 1752)** following execution of a
  malicious PDF file.
- The PDF was likely downloaded and opened via **firefox.exe (PID 888)**.

### Malicious Processes Identified
- AcroRd32.exe (PID 1752)
- firefox.exe (PID 888)
- svchost.exe (PID 1384)

All three processes:
- Contained injected PE (MZ) executables in memory
- Exhibited Read/Write/Execute permissions
- Were confirmed malicious via VirusTotal

### Network Activity
Suspicious outbound HTTP connections were identified from compromised processes:
- 212.150.164.203 (associated with firefox.exe and AcroRd32.exe)
- 193.104.22.71 (associated with svchost.exe)

### Suspicious URLs
- http://search-network-plus.com/load.php?a=a&st=Internet%20Explorer%206.0&e=2
- http://193.104.22.71/~produkt/983745213424/34650798253
- http://193.104.22.71/~produkt/9j856f_4m9y8urb.php

### Malware Intent
- Behaviour consistent with **banking trojans (Zbot/Zeus)**
- Likely objectives include credential theft, financial fraud, and command-and-control
  communication
- Evidence of process injection and persistence mechanisms
