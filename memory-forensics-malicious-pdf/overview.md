## Memory Forensics – Malicious PDF Banking Malware Case

This investigation analysed a Windows memory image following the execution of a
malicious PDF file that resulted in suspicious banking activity.

### Attack Vector
- Malicious PDF opened via Adobe Reader (AcroRd32.exe)
- PDF likely downloaded through a web browser (firefox.exe)

### Forensic Approach
- Memory analysis performed using Volatility2
- Operating system profile identified as WinXPSP2x86
- Focus on running processes, injected code, network connections, and credential artefacts

### Tools Used
- Volatility2 (pslist, malfind, connscan, memdump, hashdump)
- Linux command-line utilities (strings, grep)
- VirusTotal and IP intelligence services
