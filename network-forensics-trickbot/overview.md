## Network Forensics – TrickBot Malware Investigation

This investigation analysed a packet capture file following an IDS alert to identify
malware activity, determine the malware family, and uncover command-and-control (C2)
infrastructure.

### Scope
- Analysis limited to a provided PCAP file
- Focus on malware delivery, post-infection communication, and attribution

### Tools Used
- Wireshark (traffic filtering, object extraction, TLS analysis)
- NetworkMiner (host and user identification)
- Kali Linux command-line utilities
- VirusTotal and Malware Bazaar

### Summary of Findings
- A Windows host (10.12.19.104) downloaded a malicious payload disguised as a PNG file
- The payload was identified as **TrickBot (Trojan family)**
- Multiple C2 servers were identified through TLS certificate analysis
- Communication patterns were consistent with known TrickBot behaviour
