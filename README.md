# ⚔️ Red Team vs Blue Team — Adversarial Operations Reference

> *A practical TTP reference mapped to MITRE ATT&CK — from recon to exfiltration.*

---

## 🗺️ Attack Kill Chain Overview

```
RECON → INITIAL ACCESS → EXECUTION → PERSISTENCE → PRIV-ESC → LATERAL MOVEMENT → EXFILTRATION
```

---

## 🔴 Phase 1 — Reconnaissance

| Side | Technique | Tools | MITRE |
|------|-----------|-------|-------|
| 🔴 Red | OSINT gathering | Maltego · Shodan · theHarvester | T1589 / T1590 |
| 🔴 Red | Network scanning | Nmap · Masscan · Censys | T1046 |
| 🔵 Blue | Attack surface management | Shodan Monitor · GreyNoise | Detect T1590 |
| 🔵 Blue | Honeypot alerting | OpenCanary · Canarytokens | Detect T1046 |

**Red:** Collect org info, emails, subdomains, and exposed assets before touching target infrastructure. Scan open ports, services, and OS fingerprints to build the attack surface map.

**Blue:** Continuously enumerate your own external exposure. Deploy decoy services — any scan that touches a honeypot is an immediate high-fidelity alert.

---

## 🔴 Phase 2 — Initial Access

| Side | Technique | Tools | MITRE |
|------|-----------|-------|-------|
| 🔴 Red | Spear phishing | GoPhish · EvilGinx2 | T1566.001 / T1566.002 |
| 🔴 Red | Exploit public-facing apps | Metasploit · Burp Suite | T1190 |
| 🔵 Blue | Email security gateway | Proofpoint · M365 Defender | Detect T1566 |
| 🔵 Blue | Patch management | Tenable · Qualys | Detect T1190 |

**Red:** Targeted email lures with malicious attachments or credential-harvesting proxy links. Abuse unpatched CVEs in internet-facing services — web apps, VPNs, mail gateways.

**Blue:** URL rewriting, attachment sandboxing, DMARC enforcement. CVE prioritisation with SLAs — close the window between disclosure and exploitation.

---

## 🔴 Phase 3 — Execution

| Side | Technique | Tools | MITRE |
|------|-----------|-------|-------|
| 🔴 Red | Living-off-the-land (LOLBins) | PowerShell · WMI · mshta | T1059 / T1218 |
| 🔴 Red | Macro / script execution | Empire · Sliver · Cobalt Strike | T1059.001 |
| 🔵 Blue | Script block logging + AMSI | Windows Event 4104 · AMSI | Detect T1059 |
| 🔵 Blue | Application allowlisting | AppLocker · WDAC | Detect T1218 |

**Red:** Abuse built-in OS tools to execute payloads — hard to detect, no binary drop required. VBA macros, JScript, or HTA files that download and execute stage-two implants.

**Blue:** Log every PowerShell script block. AMSI sends content to AV/EDR before execution. Allowlist — only signed, approved binaries run. Blocks most LOLBin abuse paths.

---

## 🔴 Phase 4 — Persistence

| Side | Technique | Tools | MITRE |
|------|-----------|-------|-------|
| 🔴 Red | Registry Run keys | Reg.exe · PowerShell | T1547.001 |
| 🔴 Red | Scheduled tasks | schtasks · Cron | T1053 |
| 🔵 Blue | Registry monitoring | Sysmon Event 13 · Sentinel | Detect T1547 |
| 🔵 Blue | Task / cron auditing | Velociraptor · OSQuery | Detect T1053 |

**Red:** Write to HKCU/HKLM Run keys — implant launches on every logon. Create tasks that re-execute C2 implants periodically, surviving reboots and AV kills.

**Blue:** Alert on writes to autorun registry locations. Hunt for tasks whose binary path doesn't match a known-good baseline.

---

## 🔴 Phase 5 — Privilege Escalation

| Side | Technique | Tools | MITRE |
|------|-----------|-------|-------|
| 🔴 Red | Token impersonation | Incognito · Cobalt Strike | T1134 |
| 🔴 Red | Kernel exploit | PrintNightmare · driver CVEs | T1068 |
| 🔵 Blue | Privileged access management | CyberArk · HashiCorp Vault | Detect T1134 |
| 🔵 Blue | EDR kernel protection | CrowdStrike · SentinelOne | Detect T1068 |

**Red:** Steal or duplicate Windows access tokens — elevate from local user to SYSTEM silently. Exploit unpatched kernel/driver vulnerabilities to obtain ring-0 or SYSTEM privileges.

**Blue:** Vault and rotate credentials. Remove standing privilege — JIT access shrinks blast radius. Kernel-mode EDR drivers block exploit attempts and alert on escalation events.

---

## 🔴 Phase 6 — Lateral Movement

| Side | Technique | Tools | MITRE |
|------|-----------|-------|-------|
| 🔴 Red | Pass-the-Hash / Pass-the-Ticket | Mimikatz · Rubeus | T1550.002 |
| 🔴 Red | RDP / SMB pivoting | Impacket · Chisel | T1021.001 |
| 🔵 Blue | Network segmentation | VLAN · Firewall ACLs · Zero Trust | Detect T1021 |
| 🔵 Blue | Credential Guard | Windows Credential Guard | Detect T1550 |

**Red:** Reuse NTLM hashes or Kerberos tickets to authenticate as another user without knowing the password. Hop across hosts using legitimate admin protocols with stolen credentials.

**Blue:** Micro-segment networks. Credential Guard isolates LSASS secrets in a Hyper-V container — Mimikatz can't extract NTLM hashes from memory.

---

## 🔴 Phase 7 — Exfiltration

| Side | Technique | Tools | MITRE |
|------|-----------|-------|-------|
| 🔴 Red | C2 data exfil over DNS | DNScat2 · Cobalt Strike | T1071.004 / T1048 |
| 🔴 Red | Cloud storage abuse | rclone · aws s3 cp | T1567.002 |
| 🔵 Blue | DNS traffic analysis | Zeek · Umbrella · Sentinel | Detect T1071.004 |
| 🔵 Blue | DLP + CASB | Purview · Netskope · ZScaler | Detect T1567 |

**Red:** Encode exfiltrated data in DNS queries — blends with legitimate traffic, bypasses HTTP proxies. Upload data to attacker-controlled cloud buckets via legitimate cloud CLI tools.

**Blue:** Baseline query volume and entropy per host. High-entropy subdomains = likely DNS exfil. Inspect uploads to cloud destinations, classify sensitive content, block unauthorised egress.

---

## 🟣 Purple Team — Overlap Zone

> Where Red and Blue collaborate to close gaps and validate controls.

```
┌─────────────────────────────────────────────────────────────────┐
│  ◆ PURPLE TEAM ACTIVITIES                                       │
├─────────────────────────────────────────────────────────────────┤
│  • Joint adversary simulation exercises                         │
│  • Detection gap analysis (what did Red do that Blue missed?)   │
│  • MITRE ATT&CK mapping of existing controls                    │
│  • Threat hunting based on Red TTP playbooks                    │
│  • SIEM rule and detection signature tuning                     │
│  • Security control validation (do defenses actually fire?)     │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🛠️ Core Tooling Reference

### 🔴 Red Team Stack

```
Reconnaissance    →  Maltego · Shodan · theHarvester · Recon-ng
Initial Access    →  GoPhish · EvilGinx2 · Metasploit · Burp Suite
C2 Frameworks     →  Cobalt Strike · Sliver · Empire · Havoc
Credential Ops    →  Mimikatz · Rubeus · Impacket · CrackMapExec
Persistence       →  SharPersist · PowerSploit
Exfiltration      →  DNScat2 · rclone · Chisel
```

### 🔵 Blue Team Stack

```
SIEM              →  Splunk · Microsoft Sentinel · IBM QRadar
EDR               →  CrowdStrike Falcon · Microsoft Defender for Endpoint
Threat Intel      →  MISP · OpenCTI · YARA
Network Analysis  →  Wireshark · Zeek · Snort/Suricata
Forensics         →  Velociraptor · Volatility · OSQuery
VAPT / Scanning   →  Nessus · OpenVAS · Qualys
Email Security    →  Proofpoint · M365 Defender
PAM               →  CyberArk · HashiCorp Vault
DLP / CASB        →  Microsoft Purview · Netskope · ZScaler
```

---

## 📊 MITRE ATT&CK Coverage

| Tactic | ID | Red Technique | Blue Control |
|--------|----|---------------|--------------|
| Reconnaissance | T1589 / T1590 | OSINT / scanning | ASM · honeypots |
| Initial Access | T1566 / T1190 | Phishing · CVE exploit | Email GW · patching |
| Execution | T1059 / T1218 | LOLBins · macros | AMSI · AppLocker |
| Persistence | T1547 / T1053 | Registry · tasks | Sysmon · OSQuery |
| Privilege Escalation | T1134 / T1068 | Token theft · kernel | PAM · EDR |
| Lateral Movement | T1550 / T1021 | PtH · RDP pivot | Segmentation · Cred Guard |
| Exfiltration | T1048 / T1567 | DNS C2 · cloud upload | DLP · DNS analysis |

---

## 💡 Key Mindset

```
Red Team  →  "How would an adversary get in and achieve their objective?"
Blue Team →  "How do we detect, contain, and eradicate the threat?"
Purple    →  "Did our defenses actually catch what Red did — if not, why?"
```

---

*Mapped to MITRE ATT&CK Framework · Updated for current threat landscape*
*Tools listed for educational and authorized security testing purposes only*
