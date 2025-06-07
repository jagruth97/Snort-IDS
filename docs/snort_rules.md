# 🧠 Snort Custom Rules Overview

This file documents the logic behind each Snort rule created in `local.rules`.

---


```snort

# Port Scan
alert tcp any any -> $HOME_NET 1:1024 (msg:"[ALERT] Port scan detected"; flags:S; threshold:type threshold, track by_src, count 20, seconds 10; sid:1000001; rev:1;)

# ICMP Flood
alert icmp any any -> $HOME_NET any (msg:"[ALERT] ICMP Flood"; dsize: >100; sid:1000002; rev:1;)

# SSH Brute Force
alert tcp any any -> $HOME_NET 22 (msg:"[ALERT] SSH brute force detected"; flags:S; threshold:type threshold, track by_src, count 5, seconds 60; sid:1000005; rev:1;)

# SQL injection
alert tcp any any -> $HOME_NET 80 (msg:"[ALERT] SQL Injection attempt"; content:"' or 1=1"; nocase; sid:1000004; rev:1;)

# FTP Brute Force
alert tcp any any -> $HOME_NET 21 (msg:"[ALERT] FTP brute force detected"; flags:S; threshold:type threshold, track by_src, count 5, seconds 60; sid:1000005; rev:1;)

