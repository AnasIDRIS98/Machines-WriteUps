<div align="center">

# HTB Writeups

مجموعة تغطي كل الأجهزة (Machines) التي تم اختراقها بنجاح على Hack The Box، مع شرح مختصر لسلسلة الاختراق الكاملة وربطها بإطار MITRE ATT&CK.

[![HTB Profile](https://img.shields.io/badge/HTB-0xt1tan-9FEF00?style=flat-square&logo=hackthebox&logoColor=white)](https://app.hackthebox.com/profile/0xt1tan)
![Machines](https://img.shields.io/badge/Machines-7-2ea44f?style=flat-square)
![License](https://img.shields.io/badge/License-Educational-blue?style=flat-square)

</div>

---

## نظرة عامة

كل جهاز له مجلد خاص يحتوي على README يوثّق: الاستطلاع، نقطة الدخول (Foothold)، تصعيد الصلاحيات (Privilege Escalation)، وتعيين التقنيات المستخدمة على MITRE ATT&CK. الهدف من هذا المستودع هو توثيق منهجية العمل وليس نسخ محتوى الجهاز نفسه، احترامًا لقواعد HTB.

## قائمة الأجهزة

| الجهاز | النظام | الصعوبة | التصنيف | التقنية الأساسية |
|---|---|---|---|---|
| [Sequel](machines/Sequel/README.md) | Linux | Very Easy | Starting Point | MySQL root بدون كلمة مرور |
| [Crocodile](machines/Crocodile/README.md) | Linux | Very Easy | Starting Point | تسريب بيانات عبر FTP مجهول + تجاوز تسجيل دخول |
| [Paper](machines/Paper/README.md) | Linux | Easy | Machine | WordPress info disclosure + Polkit privesc |
| [MetaTwo](machines/MetaTwo/README.md) | Linux | Easy | Machine | SQLi + XXE + Passpie GPG privesc |
| [Remote](machines/Remote/README.md) | Windows | Easy | Machine | Umbraco RCE + مسارين لتصعيد الصلاحيات |
| [Knife](machines/Knife/README.md) | Linux | Easy | Machine | PHP dev backdoor RCE + sudo knife privesc |
| [Timelapse](machines/Timelapse/README.md) | Windows (AD) | Easy | Machine | كسر شهادة PFX + LAPS abuse إلى Domain Admin |

## خريطة MITRE ATT&CK المجمّعة

<details>
<summary>عرض التكتيكات والتقنيات المستخدمة عبر جميع الأجهزة</summary>

| Tactic | Technique | ID | مثال جهاز |
|---|---|---|---|
| Reconnaissance | Active Scanning | T1595 | جميع الأجهزة |
| Initial Access | Exploit Public-Facing Application | T1190 | Paper, MetaTwo, Remote, Knife |
| Credential Access | Unsecured Credentials | T1552 | Crocodile, Remote, Timelapse |
| Credential Access | Brute Force (Hash Cracking) | T1110 | Remote, Timelapse |
| Execution | Command and Scripting Interpreter | T1059 | Knife, Remote |
| Privilege Escalation | Exploitation for Privilege Escalation | T1068 | Paper, MetaTwo |
| Privilege Escalation | Abuse Elevation Control Mechanism (sudo) | T1548.003 | Knife |
| Privilege Escalation | Valid Accounts (credential reuse) | T1078 | Remote |
| Lateral Movement / Escalation | LAPS Abuse | T1552.006 | Timelapse |

</details>

## أدوات مستخدمة بشكل متكرر

`nmap` `gobuster` `Evil-WinRM` `Metasploit` `hashcat` / `john` `BloodHound` `Chisel`

## عن الكاتب

متخصص أمن سيبراني في بداية مساره المهني، يعمل على بناء مسار SOC Analyst ← SOC Manager، مع تدريب عملي مستمر على Hack The Box (تقريبًا جهازين أو Sherlock أسبوعيًا، بالتناوب بين الهجوم والتحليل الجنائي الرقمي).
