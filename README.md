<div align="center">

```
██████╗ ███████╗██████╗     ██╗    ██████╗ ██╗     ██╗   ██╗███████╗
██╔══██╗██╔════╝██╔══██╗   ██╔╝    ██╔══██╗██║     ██║   ██║██╔════╝
██████╔╝█████╗  ██║  ██║  ██╔╝     ██████╔╝██║     ██║   ██║█████╗  
██╔══██╗██╔══╝  ██║  ██║ ██╔╝      ██╔══██╗██║     ██║   ██║██╔══╝  
██║  ██║███████╗██████╔╝██╔╝       ██████╔╝███████╗╚██████╔╝███████╗
╚═╝  ╚═╝╚══════╝╚═════╝ ╚═╝        ╚═════╝ ╚══════╝ ╚═════╝ ╚══════╝
```

# Faisal Mehmood · `cipheread`
### Security Operations Engineer · Red Teamer · Blue Teamer · Incident Responder

*"I attack like a Red Teamer. I defend like a Blue Teamer. I think like both."*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/faisalmehmood111)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:cipheread@gmail.com)
[![TryHackMe](https://img.shields.io/badge/TryHackMe-212C42?style=flat-square&logo=tryhackme&logoColor=white)](https://tryhackme.com/p/cipheread)
[![HackTheBox](https://img.shields.io/badge/HackTheBox-9FEF00?style=flat-square&logo=hackthebox&logoColor=black)](https://app.hackthebox.com/profile/cipheread)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/cipheread)

</div>

---

## $ whoami --full

```yaml
name:         Faisal Mehmood
alias:        cipheread
role:         Security Operations Engineer
speciality:   Red + Blue Team Operations · DevSecOps · Incident Response
mindset:      Adversary-informed defense — I break things to learn how to fix them
current:      Enhancing detection logic, SIEM use cases, and VAPT lifecycles
learning:     Adversary emulation (MITRE ATT&CK), purple teaming, CI/CD security
```

I operate on both sides of the security divide — running offensive assessments as a Red Teamer to uncover real attack paths, then switching context to Blue Team operations to build the detections that catch them. My SOC work is shaped by attacker thinking: every alert I tune, every SIEM rule I write, every incident I respond to is informed by how an adversary would actually behave in the environment.

---

## $ cat /etc/operator-profile

<table>
<tr>
<td width="50%" valign="top">

### 🔴 Red Team Operations

```
Role        Offensive Security Analyst
Mindset     Assume breach · think like the adversary
Focus       VAPT · adversary simulation · TTPs
Framework   MITRE ATT&CK · PTES · OWASP
```

**What I do on the Red side:**
- Conduct full-scope VAPT engagements (network, web, AD)
- Simulate real-world adversary TTPs against live environments
- Develop custom payloads and evasion techniques
- Exploit misconfigurations across cloud and on-prem infra
- Document attack paths for remediation and purple team handoff

</td>
<td width="50%" valign="top">

### 🔵 Blue Team Operations

```
Role        SOC / Detection Engineer · IR Lead
Mindset     Detect early · contain fast · learn always
Focus       SIEM · EDR · log analysis · incident response
Framework   NIST · MITRE D3FEND · Cyber Kill Chain
```

**What I do on the Blue side:**
- Build and tune SIEM detection use cases (Splunk · Sentinel · QRadar)
- Lead incident response and digital forensics investigations
- Analyse logs, artefacts, and IOCs to reconstruct attack timelines
- Develop threat hunting playbooks from Red Team findings
- Harden environments based on real adversary behaviour

</td>
</tr>
</table>

---

## $ sudo run-operation --phase all

### 🔴 RECON  `[Red]`  →  🔵 DETECT  `[Blue]`

```
RED  ──┬── OSINT gathering          [ Maltego · Shodan · theHarvester ]   T1589/T1590
       └── Network scanning         [ Nmap · Masscan · Censys ]            T1046

BLUE ──┬── Attack surface mgmt      [ Shodan Monitor · GreyNoise ]         Detect T1590
       └── Honeypot alerting        [ OpenCanary · Canarytokens ]          Detect T1046
```

---

### 🔴 INITIAL ACCESS  `[Red]`  →  🔵 BLOCK  `[Blue]`

```
RED  ──┬── Spear phishing           [ GoPhish · EvilGinx2 ]                T1566.001/002
       └── Exploit public apps      [ Metasploit · Burp Suite ]            T1190

BLUE ──┬── Email security gateway   [ Proofpoint · M365 Defender ]         Detect T1566
       └── Patch management         [ Tenable · Qualys ]                   Detect T1190
```

---

### 🔴 EXECUTION  `[Red]`  →  🔵 CONTAIN  `[Blue]`

```
RED  ──┬── Living-off-the-land      [ PowerShell · WMI · mshta ]           T1059/T1218
       └── Macro / script exec      [ Empire · Sliver · Cobalt Strike ]    T1059.001

BLUE ──┬── Script block logging     [ Windows Event 4104 · AMSI ]          Detect T1059
       └── Application allowlist    [ AppLocker · WDAC ]                   Detect T1218
```

---

### 🔴 PERSISTENCE  `[Red]`  →  🔵 HUNT  `[Blue]`

```
RED  ──┬── Registry Run keys        [ Reg.exe · PowerShell ]                T1547.001
       └── Scheduled tasks          [ schtasks · Cron ]                     T1053

BLUE ──┬── Registry monitoring      [ Sysmon Event 13 · Sentinel ]          Detect T1547
       └── Task / cron auditing     [ Velociraptor · OSQuery ]              Detect T1053
```

---

### 🔴 PRIVILEGE ESCALATION  `[Red]`  →  🔵 HARDEN  `[Blue]`

```
RED  ──┬── Token impersonation      [ Incognito · Cobalt Strike ]           T1134
       └── Kernel exploitation      [ PrintNightmare · CVE drivers ]        T1068

BLUE ──┬── Privileged access mgmt   [ CyberArk · HashiCorp Vault ]          Detect T1134
       └── EDR kernel protection    [ CrowdStrike · SentinelOne ]           Detect T1068
```

---

### 🔴 LATERAL MOVEMENT  `[Red]`  →  🔵 SEGMENT  `[Blue]`

```
RED  ──┬── Pass-the-Hash/Ticket     [ Mimikatz · Rubeus · Impacket ]        T1550.002
       └── RDP / SMB pivoting       [ Impacket · Chisel ]                   T1021.001

BLUE ──┬── Network segmentation     [ VLAN · Firewall ACLs · Zero Trust ]   Detect T1021
       └── Credential Guard         [ Windows Credential Guard ]            Detect T1550
```

---

### 🔴 EXFILTRATION  `[Red]`  →  🔵 RESPOND  `[Blue]`

```
RED  ──┬── C2 exfil over DNS        [ DNScat2 · Cobalt Strike ]             T1071.004/T1048
       └── Cloud storage abuse      [ rclone · aws s3 cp ]                  T1567.002

BLUE ──┬── DNS traffic analysis     [ Zeek · Umbrella · Sentinel ]          Detect T1071.004
       └── DLP + CASB               [ Purview · Netskope · ZScaler ]        Detect T1567
```

---

## $ ls -la /tools/

<table>
<tr>
<td width="50%" valign="top">

### 🔴 Offensive Arsenal

| Category | Tools |
|----------|-------|
| **Recon** | Maltego · Shodan · theHarvester · Recon-ng |
| **Web** | Burp Suite · OWASP ZAP · SQLmap |
| **Exploitation** | Metasploit · Impacket · CrackMapExec |
| **C2 Frameworks** | Cobalt Strike · Sliver · Empire |
| **AD Attacks** | Mimikatz · Rubeus · BloodHound |
| **Phishing** | GoPhish · EvilGinx2 |

</td>
<td width="50%" valign="top">

### 🔵 Defensive Stack

| Category | Tools |
|----------|-------|
| **SIEM** | Splunk · Microsoft Sentinel · QRadar |
| **EDR** | CrowdStrike Falcon · MS Defender for Endpoint |
| **Network** | Wireshark · Zeek · Snort · Suricata |
| **Threat Intel** | MISP · OpenCTI · YARA |
| **Forensics** | Velociraptor · Volatility · OSQuery |
| **VAPT** | Nessus · OpenVAS · Qualys |

</td>
</tr>
</table>

---

## $ cat /etc/purple-team.conf

```
╔══════════════════════════════════════════════════════════════════╗
║              🟣  PURPLE TEAM — WHERE I BRIDGE BOTH              ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  Red findings    ──►  Blue detection rules                       ║
║  Attack paths    ──►  Threat hunt playbooks                      ║
║  TTP simulation  ──►  SIEM use case development                  ║
║  Evasion tests   ──►  EDR tuning and gap closure                 ║
║  MITRE ATT&CK    ──►  Control validation mapping                 ║
║                                                                  ║
║  "If Red did it and Blue didn't catch it — I fix both sides."    ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

**Purple Team activities I run:**
- Joint adversary simulation with detection feedback loops
- MITRE ATT&CK coverage mapping against existing controls
- Detection gap analysis post-Red Team engagement
- SIEM rule tuning based on attacker evasion techniques observed in the field
- Threat hunting from Red Team TTP playbooks

---

## $ ls -la ./certifications/

```
drwxr-xr-x  OFFENSIVE
├── [CEH]    Certified Ethical Hacker                    — EC-Council
└── [CRTA]   Certified Red Team Analyst                  — TCM Security

drwxr-xr-x  DEFENSIVE
├── [SOC101] SOC Fundamentals                            — TCM Security
├── [SOC202] Intermediate SOC Analysis                   — TCM Security
├── [PWF]    Practical Windows Forensics                  — TCM Security
└── [CPPS]   Certified Phishing Prevention Specialist    — TCM Security

drwxr-xr-x  CLOUD & IT
├── [AWS]    AWS Builders Online Series                   — Amazon Web Services
└── [GITS]   Google IT Support Specialization            — Coursera / Google
```

---

## $ cat /proc/languages

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=flat-square&logo=powershell&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnu-bash&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=flat-square&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=c%2B%2B&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=flat-square&logo=csharp&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)

---

## $ uptime --stats

<div align="center">

<img src="https://github-readme-streak-stats.herokuapp.com/?user=cipheread&theme=dark&hide_border=true&background=0D1117&ring=E24B4A&fire=E24B4A&currStreakLabel=378ADD" width="55%" />

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=cipheread&theme=dark&hide_border=true&bg_color=0D1117&layout=compact" width="42%" />

</div>

---

## $ ping --platforms

| Platform | Handle |
|----------|--------|
| 💼 LinkedIn | [faisalmehmood111](https://linkedin.com/in/faisalmehmood111) |
| 🐙 GitHub | [cipheread](https://github.com/cipheread) |
| 📧 Email | [cipheread@gmail.com](mailto:cipheread@gmail.com) |
| 🔐 TryHackMe | cipheread |
| 🏴 Hack The Box | cipheread |

---

<div align="center">

```
[ 🔴 ATTACKING · 🔵 DEFENDING · 🟣 BRIDGING THE GAP ]
```

*"Every log tells a story — I help you read between the lines."*

</div>
