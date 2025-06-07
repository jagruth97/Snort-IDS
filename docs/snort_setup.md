## Install Snort (Ubuntu)
```bash
sudo apt update
sudo apt install snort -y

```
### During install:
Interface: Choose your main network interface (e.g., ens33, eth0)
HOME_NET: Enter your subnet (e.g., 192.168.1.0/24)

## Test Snort
```bash
snort -V
```

# KEY PATHS
| Purpose                           | Path                           |
| --------------------------------- | ------------------------------ |
| Main config file                  | `/etc/snort/snort.conf`        |
| Rule file you'll edit             | `/etc/snort/rules/local.rules` |
| Log folder                        | `/var/log/snort/`              |
| Interface config (Debian systems) | `/etc/snort/snort.debian.conf` |

### Test Config file
sudo snort -T -c /etc/snort/snort.conf -i ens33

## Confirm Ubuntu(Snort IDS) able to contact other VMs
```bash
ping <Metasploitable_IP>
ping <Kali_IP>