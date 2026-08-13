HTB Writeups

<p align="center">
  <img src="https://raw.githubusercontent.com/hackthebox/brand-assets/master/Logos/HTB%20Logo/PNG/HTB_logo.png" width="220">
</p>
<p align="center">
  <strong>Documenting my Hack The Box journey through methodology, attack chains, and MITRE ATT&CK mapping.</strong>
</p>
<p align="center">
  <a href="https://app.hackthebox.com/">
    <img src="https://img.shields.io/badge/Hack%20The%20Box-Profile-9FEF00?style=for-the-badge&logo=hackthebox&logoColor=black">
  </a>
  <img src="https://img.shields.io/badge/Writeups-7-success?style=for-the-badge">
  <img src="https://img.shields.io/badge/MITRE-ATT%26CK-red?style=for-the-badge">
  <img src="https://img.shields.io/badge/Status-Active-blue?style=for-the-badge">
</p>

⸻

Overview

This repository contains concise writeups for every Hack The Box Machine I have successfully completed.

Rather than reproducing the original machine content, each writeup focuses on the methodology, attack path, and decision-making process behind the compromise while respecting the Hack The Box content policy.

Each machine includes:

* Network Enumeration
* Service Analysis
* Initial Foothold
* Privilege Escalation
* Indicators of Compromise (where applicable)
* MITRE ATT&CK Mapping
* Lessons Learned

The objective is to build a practical knowledge base that reflects real penetration testing methodology instead of exploit copy-pasting.

⸻

Repository Structure

HTB-Writeups/
│
├── Sequel/
│   └── README.md
│
├── Crocodile/
│   └── README.md
│
├── Paper/
│   └── README.md
│
├── MetaTwo/
│   └── README.md
│
├── Remote/
│   └── README.md
│
├── Knife/
│   └── README.md
│
└── Timelapse/
    └── README.md

⸻

Completed Machines

Machine	OS	Difficulty	Category	Primary Technique
Sequel	Linux	Very Easy	Starting Point	MySQL Root Login (No Password)
Crocodile	Linux	Very Easy	Starting Point	Anonymous FTP → Credential Reuse
Paper	Linux	Easy	Machine	WordPress Information Disclosure → Polkit
MetaTwo	Linux	Easy	Machine	SQLi → XXE → Passpie GPG
Remote	Windows	Easy	Machine	Umbraco CMS RCE
Knife	Linux	Easy	Machine	PHP Backdoor → sudo Knife
Timelapse	Windows AD	Easy	Machine	Cracked PFX → LAPS Abuse

⸻

MITRE ATT&CK Coverage

This repository maps every machine against the MITRE ATT&CK framework to better understand attacker behavior beyond individual exploits.

Tactic	Examples
Initial Access	Valid Accounts, Exploiting Public Applications
Execution	Command Shell, PHP Execution
Persistence	Valid Accounts
Privilege Escalation	Sudo Abuse, Polkit, LAPS
Credential Access	Password Cracking, Credential Dumping
Discovery	Service Enumeration, Account Discovery
Lateral Movement	SMB, WinRM
Collection	File Discovery
Command & Control	Reverse Shells
Impact	Administrative Access

⸻

Frequently Used Tools

<p align="center">
<img src="https://skillicons.dev/icons?i=linux,bash,git,docker"/>
</p>

Enumeration	Exploitation	Post Exploitation
Nmap	Metasploit	Evil-WinRM
Gobuster	SQLmap	BloodHound
NetExec	Burp Suite	Chisel
Feroxbuster	curl	LinPEAS
Enum4linux	Hydra	WinPEAS
FTP	CrackMapExec	John / Hashcat

⸻

Writeup Philosophy

Every writeup answers four questions:

* How was the target enumerated?
* Why did the attack work?
* How was privilege escalation achieved?
* Which MITRE ATT&CK techniques describe the attack?

The focus is on understanding why something works—not simply following exploitation steps.

⸻

HTB License Notice

These writeups are original summaries created for educational purposes.

They intentionally avoid reproducing proprietary Hack The Box content, official walkthroughs, flags, or machine-specific solutions.

All rights related to the original machine content remain the property of Hack The Box.

⸻

About Me

Cybersecurity professional specializing in Blue Team operations with a growing focus on offensive security to better understand attacker tradecraft.

Current roadmap:

SOC Analyst
      │
      ▼
Detection Engineer
      │
      ▼
Threat Hunter
      │
      ▼
SOC Manager

Hands-on practice is primarily conducted through:

* Hack The Box Machines
* Hack The Box Sherlocks
* Digital Forensics
* Incident Response
* Detection Engineering

⸻

<p align="center">
  <strong>If you find this repository useful, consider giving it a ⭐.</strong>
</p>
