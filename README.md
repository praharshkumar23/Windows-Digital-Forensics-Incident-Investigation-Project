# Windows Forensics Investigation Project (CTF-Based)

This project is a practical Windows Digital Forensics investigation performed in a CTF-style environment. It simulates how a SOC Analyst / DFIR Investigator analyzes a compromised Windows system, finds attacker activity, and documents evidence for an incident report.[1]

## Project Overview

- Analyze a compromised Windows 10 system in a controlled lab / CTF environment.[2]
- Collect and examine forensic artefacts such as registry hives, event logs, prefetch files, browser data, and suspicious executables.[2]
- Focus on **hands-on** investigation steps instead of only theory, so students can practice real-world DFIR workflows.[3]

## Objectives

- Perform forensic analysis on a Windows system.[1]
- Identify suspicious activity and attacker traces.[2]
- Analyze registry, file system and execution artefacts (prefetch, logs, browser data, SQLite, etc.).[4]
- Extract clear evidence to support an incident report.[5]
- Strengthen practical DFIR skills for real-world SOC and incident response roles.[6]

## Tools and Environment

**Operating Systems**

- Windows 10 – Victim / target machine (image under analysis).[1]
- Kali Linux / Ubuntu – Optional analysis machine for extra tools and scripting.[6]

**Forensic Tools**

- Autopsy – GUI forensic suite for disk, files and artefact analysis.[1]
- FTK Imager – Disk imaging and evidence acquisition.[1]
- Registry Explorer – Deep registry hive analysis.[7]
- PEStudio – Static analysis of suspicious executables.[2]
- Event Viewer – Native Windows event log viewer.[2]
- Strings and hashing tools – Extract strings and compute hashes for integrity and malware checks.[5]
- DB Browser for SQLite – Inspect application and browser databases.[4]
- PowerShell – Quick triage and scripting support.[1]
- Volatility (optional) – Memory forensics and RAM artefact analysis.[8]

## Evidence Collected

- **Disk Image**: Windows forensic image (.E01 / raw) of the victim machine.[1]
- **Registry Hives**: SAM, SYSTEM, SOFTWARE, NTUSER.DAT and related hives.[7]
- **Event Logs**: Security, System, Application logs.[2]
- **Prefetch Files**: Program execution traces from `C:\Windows\Prefetch`.[4]
- **Browser Data**: History, downloads, cache from common browsers.[2]
- **SQLite Databases**: Application and message databases (chats, accounts, sync).[4]
- **Suspicious Files**: Executables and scripts related to the attack scenario.[9]

## Investigation Methodology

### 1. Evidence Acquisition

- Created a full disk image of the victim system using FTK Imager.[1]
- Calculated hashes (MD5/SHA256) to maintain evidence integrity and chain of custody.[5]
- Performed read-only analysis to avoid modifying original evidence.[5]

### 2. File System Analysis

- Searched for suspicious files and artefacts in `Downloads`, `AppData`, `Temp`, and Startup folders.[1]
- Reviewed file timestamps (Created / Modified / Accessed) to build a basic timeline.[5]
- Compared hashes of suspicious files with VirusTotal to check for known malware.[9]

### 3. Registry Analysis

- Analyzed common persistence and startup locations, including:  
  - `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`  
  - `HKLM\Software\Microsoft\Windows\CurrentVersion\Run`  
  - `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer`[7]
- Found evidence of registry-based persistence mechanisms and suspicious startup entries.[7]

### 4. Program Execution Artefacts

- Examined Prefetch files from `C:\Windows\Prefetch` to identify executed programs and run counts.[4]
- Looked at RecentDocs and UserAssist keys to track recently opened files and applications.[7]
- Identified suspicious executables and repeated execution patterns indicating persistence.[4]

### 5. Event Log Analysis

- Reviewed Security, System and Application logs for:  
  - Logon events  
  - Privilege escalation attempts  
  - Application crashes  
  - Security policy changes[2]
- Focused on key Windows Event IDs such as:  
  - 4624 – Successful logon  
  - 4625 – Failed logon  
  - 4688 – Process creation[2]

### 6. Browser and Application Analysis

- Extracted browsing history to identify malicious websites and download sources.[2]
- Traced downloads related to suspicious executables or tools.[1]
- Analyzed SQLite databases for messages, accounts and synchronization data to reveal communication patterns.[4]

### 7. Suspicious Activity and Findings

- Unauthorized execution of suspicious binaries on the system.[9]
- Registry Run keys used to maintain persistence across reboots.[7]
- Malicious browsing and downloads linked to the attack timeline.[2]
- Suspicious communication patterns suggesting possible insider involvement (CTF narrative).[9]
- Evidence of planned malicious activity consistent with a training / CTF scenario.[3]

## Key Findings Summary

| Category        | Finding                                      |
|----------------|----------------------------------------------|
| Persistence    | Registry Run keys used as startup entries. [7] |
| Malware        | Suspicious executable identified and analyzed. [9] |
| User Activity  | Malicious browsing and file downloads. [2] |
| Communication  | Suspicious messages / accounts in SQLite data. [4] |
| Insider Threat | Artefacts pointing to deliberate planning. [3] |

## Project Structure

```text
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
```

- `Evidence/` – Disk image and registry hives used in the lab (CTF data only).[3]
- `Analysis/` – Extracted artefacts (prefetch, registry exports, event log exports).[1]
- `Screenshots/` – Key screenshots showing tools and important findings.[10]
- `Findings/Report.pdf` – Final incident report summarizing methodology and evidence.[11]
- `README.md` – Overview and instructions for students using this project.[12]

## Skills Demonstrated

- Windows Digital Forensics and Incident Response (DFIR).[1]
- Evidence acquisition and integrity (hashing, read-only analysis).[5]
- Registry analysis and persistence detection.[7]
- File system and program execution artefact analysis (Prefetch, UserAssist, RecentDocs).[4]
- Event log analysis and timeline building.[2]
- SQLite database analysis for application and communication artefacts.[4]
- Report writing and documentation of forensic findings.[11]

## How This Helps My Career

- Builds practical experience with real DFIR workflows used by SOC and incident response teams.[6]
- Shows ability to move from raw artefacts (logs, registry, images) to a clear, evidence-based incident story.[5]
- Demonstrates hands-on skills that are valuable for internships and entry-level roles in cyber security and digital forensics.[10]

## How Students Can Use This Lab

- Clone or download the repository and review the README and report.[13]
- Open the evidence in the same tools (Autopsy, FTK Imager, Registry Explorer, etc.) and attempt the investigation.[3]
- Try to answer questions such as:  
  - What is the persistence mechanism?  
  - Which executable is malicious and how was it launched?  
  - When did the attacker first gain access?  
  - What user actions helped the attack succeed?[14]

## Next Possible Enhancements

- Add memory forensics using Volatility to analyze processes, DLLs and network connections in RAM.[8]
- Automate artefact extraction and parsing with scripts or open-source triage tools.[15]
- Create a visual timeline of events to show the attack flow more clearly.[16]
- Integrate YARA rules to scan suspicious files and memory for known patterns.[15]

## Disclaimer

This project is  for educational and learning purposes. All data used is part of a CTF / lab environment .[9]

***

You can copy this into your `README.md` and adjust small details (like filenames or tools) to match your exact lab.

[1](https://www.infosecinstitute.com/resources/digital-forensics/forensic-investigation-windows-machines/)
[2](https://www.geeksforgeeks.org/blogs/windows-forensic-analysis/)
[3](https://github.com/frankwxu/digital-forensics-lab)
[4](https://levelblue.com/blogs/spiderlabs-blog/windows-search-index-the-forensic-artifact-youve-been-searching-for/)
[5](https://nvlpubs.nist.gov/nistpubs/ir/2022/NIST.IR.8428.pdf)
[6](https://tryhackme.com/resources/blog/virtual-labs-for-learning-digital-forensics-where-to-start)
[7](https://www.cybertriage.com/blog/windows-registry-forensics-2025/)
[8](https://github.com/stuxnet999/MemLabs)
[9](https://belkasoft.com/belkactf6-writeup)
[10](https://github.com/mikeroyal/Digital-Forensics-Guide/blob/main/README.md)
[11](https://binste.github.io/basic_reproducibility_guide/sharing_your_work/readme_file)
[12](https://www.freecodecamp.org/news/how-to-write-a-good-readme-file/)
[13](https://github.blog/developer-skills/github/beginners-guide-to-github-repositories-how-to-create-your-first-repo/)
[14](https://trailofbits.github.io/ctf/forensics/)
[15](https://github.com/WithSecureLabs/chainsaw)
[16](http://www.diva-portal.org/smash/get/diva2:1976997/FULLTEXT01.pdf)
