🖥️ Windows Forensics Investigation Project (CTF-Based)
📌 Project Overview

This project demonstrates a practical Windows Digital Forensics investigation performed in a CTF (Capture The Flag) style environment.
The goal is to analyze a compromised Windows system and extract forensic artefacts related to user activity, persistence mechanisms, suspicious files, execution traces, and potential malicious behavior.

This project focuses on hands-on forensic analysis, not just theory, and simulates how a SOC Analyst / Digital Forensics Investigator would approach a real incident.

🎯 Objectives
Perform forensic analysis on a Windows system
Identify suspicious activity and attacker traces
Analyze registry, file system, execution artifacts
Extract evidence for incident reporting
Strengthen practical DFIR skills for real-world scenarios

🧰 Tools & Environment Used
🔹 Operating System
Windows 10 (Victim Machine)
Kali Linux / Ubuntu (Analysis Machine – optional)

🔹 Forensic Tools
Autopsy |
FTK Imager|
Registry Explorer|
PEStudio|
Event Viewer|
Strings / Hashing tools|
DB Browser for SQLite|
PowerShell|
Volatility (optional – memory analysis)

📂 Evidence Collected
Evidence Type	Description
Disk Image	Windows forensic image (.E01 / raw)
Registry Hives	SAM, SYSTEM, SOFTWARE, NTUSER.DAT
Event Logs	Security, System, Application
Prefetch Files	Program execution traces
Browser Data	History, downloads, cache
SQLite DBs	Application & message databases
Suspicious Files	Executables, scripts
🧠 Investigation Methodology
1️⃣ Evidence Acquisition

Disk image created using FTK Imager
Hashes (MD5/SHA256) calculated to maintain integrity

Read-only analysis to preserve evidence

2️⃣ File System Analysis
Identified suspicious files in:
Downloads
AppData
Temp
Startup folders
Checked timestamps:
Created
Modified
Accessed

Compared file hashes with VirusTotal

3️⃣ Registry Analysis

Analyzed key registry locations:

HKCU\Software\Microsoft\Windows\CurrentVersion\Run |
HKLM\Software\Microsoft\Windows\CurrentVersion\Run |
HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer


✔ Found evidence of persistence mechanisms
✔ Identified suspicious startup entries

4️⃣ Program Execution Evidence
Analyzed:
Prefetch files (C:\Windows\Prefetch)
RecentDocs
UserAssist keys

Findings:
Evidence of suspicious executable execution
Repeated execution timestamps indicating persistence

5️⃣ Event Log Analysis
Reviewed:
Logon events
Privilege escalation attempts
Application crashes
Security policy changes

Key Event IDs:
4624 – Successful logon
4625 – Failed logon
4688 – Process creation

6️⃣ Browser & Application Analysis
Extracted browsing history
Downloaded malicious files
Analyzed SQLite databases for:
Messages
Accounts
Synchronization data

7️⃣ Suspicious Activity Findings

✔ Unauthorized file execution
✔ Registry persistence
✔ Suspicious communication patterns
✔ Possible insider involvement
✔ Evidence of planned malicious activity (CTF narrative)

📊 Key Findings Summary
Category	Finding
Persistence	Registry Run Keys
Malware	Suspicious executable
User Activity	Malicious browsing & downloads
Communication	Suspicious SMS / messages
Insider Threat	Evidence of planning
📝 Final Conclusion

The investigation confirmed that the system was compromised, and the attacker established persistence using registry keys. Multiple forensic artefacts indicate intentional malicious activity, including suspicious communications and execution of unauthorized binaries.

This project demonstrates end-to-end Windows forensic analysis aligned with real-world DFIR workflows.

📁 Project Structure
Windows-Forensics-Project/
│
├── Evidence/
│   ├── DiskImage.E01
│   ├── RegistryHives/
│
├── Analysis/
│   ├── Prefetch/
│   ├── Registry/
│   ├── EventLogs/
│
├── Screenshots/
│
├── Findings/
│   ├── Report.pdf
│
└── README.md

🧪 Skills Demonstrated (CV-Ready)

Windows Digital Forensics

Incident Response

Registry Analysis

Evidence Handling

Malware Triage

Timeline Analysis

SQLite Database Analysis

OSINT Correlation

Report Writing

📌 How This Helps My Career

This project strengthens my understanding of:

SOC & DFIR workflows

Real-world attack investigation

Evidence-based decision making

It also reflects hands-on forensic capability, not just theoretical knowledge.

🔒 Disclaimer

This project is created strictly for educational and learning purposes.
All data used is part of a CTF / lab environment.

⭐ Next Enhancements (Optional)

Add memory forensics using Volatility

Automate artefact extraction

Create timeline visualization

Integrate YARA rules
