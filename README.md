![Snort IDS Banner](https://img.shields.io/badge/Snort-Intrusion%20Detection-blueviolet?style=for-the-badge&logo=snort&logoColor=white)

# 🛡️ Network Intrusion Detection with Snort

![Platform](https://img.shields.io/badge/Platform-Ubuntu--Kali--Metasploitable-blue?style=flat-square)
![Snort Version](https://img.shields.io/badge/Snort-Tested%20v2.9.x-brightgreen?style=flat-square)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-T1046,T1078,T1071.001-informational?style=flat-square)

This project demonstrates the use of **Snort** as a network-based IDS to detect multiple types of attacks in a controlled lab environment.

## 🖥️ Lab Architecture

| VM | Role | Details |
|----|------|---------|
| Ubuntu | IDS | Snort installed (interface: ens33) |
| Kali | Attacker | Nmap, Hydra, SQLmap, curl |
| Metasploitable | Victim | Vulnerable services: FTP, DVWA, Mutillidae |

<pre>
┌────────────┐
│    Kali    │
│ (Attacker) │
└─────┬──────┘
      │
      │ Simulated Attacks (Nmap, Hydra, hping3, curl)
      ▼
┌─────────────────────┐
│  Metasploitable VM  │
│ (Vulnerable Target) │
└─────────┬───────────┘
          │
          ▼
 Monitored via ens33
          │
          ▼
┌──────────────┐
│  Ubuntu VM   │
│  (Snort IDS) │
└──────────────┘
</pre>


## Project Structure
<pre>
snort-ids-project/
├── docs/
│   ├── Snort_IDS_Report_Jagruth.docx
│   └── Snort_IDS_Report_Jagruth.pdf
├── screenshots/
│   └── *.png
├── README.md
├── attack_simulations.md
├── snort_rules.md
</pre>

## 🚨 Detected Attacks

| Attack Type | Tool | Target Service | Rule SID |
|-------------|------|----------------|----------|
| Port Scan | Nmap | TCP (1–1024) | 1000001 |
| ICMP Flood | hping3 | ICMP | 1000002 |
| FTP Brute Force | Hydra | vsftpd (21) | 1000005 |
| SQL Injection | curl/sqlmap | HTTP (port 80) | 1000004 |

> ❗ Due to modern OpenSSH restrictions, SSH brute force was replaced with **FTP brute force**, which is functionally equivalent for Snort rule demonstration.

## 🔧 Setup

See [`docs/snort_setup.md`](docs/snort_setup.md) for full installation and config steps.

## 📜 Rules

Snort rules used are in [`rules/local.rules`](rules/local.rules)  
See [`docs/snort_rules.md`](docs/snort_rules.md) for rule logic and SID descriptions.

## 🧪 Attack Simulations

Each attack is documented in [`docs/attack_simulations.md`](docs/attack_simulations.md), including:
- Command used from Kali
- Screenshot of Snort alert from Ubuntu
- Explanation of how the detection worked

## 📸 Screenshots

Found under `screenshots/` folder.

## 📄 Full Report

Final project report in `report.docx`.

---

