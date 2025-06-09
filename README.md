# MapNet: Introduction to Nmap for Cybersecurity Professionals
## Nmap - Cybersecurity Tool

![Nmap Official Logo](https://m.media-amazon.com/images/I/81qOGh5yCSL._AC_UF350,350_QL50_.jpg)

**Nmap (Network Mapper)** It is an open-source tool used for network discovery and security auditing, and used by many people, including students, administrators, engineers, and especially cybersecurity professionals.

Nmap has many functions such as:

- **Host Discovery**: Identify live hosts on a network.
- **Port Scanning**: Detect open ports and services running on a target system.
- **Service Version Detection**: Determine the version of applications or services running on open ports.
- **OS Detection**: Guess the operating system and hardware characteristics of network devices.
- **Firewall Evasion**: Bypass or test firewall and intrusion detection system (IDS) rules.
- **Network Mapping**: Create a map of the network topology.
- **Vulnerability Scanning**: Detect common vulnerabilities using Nmap scripts (NSE - Nmap Scripting Engine).
- **Inventory and Monitoring**: Keep track of devices, hosts, and services in a network.
- **Security Auditing**: Perform security assessments on networks and systems.

> Nmap is a versatile tool used in both offensive and defensive security strategies.

### Prerequisites

Kali Linux, being designed for cybersecurity, usually comes with Nmap preinstalled. However, if for some reason it's not installed or you want to update it, follow these steps (In the terminal, type the following commands):

```bash
nmap --version  # to see if you really have it or not
sudo apt update
sudo apt install nmap -y
nmap --version  # again
```

#### Basic Commands

Next we will do a sample of some basic Nmap commands, these are strictly related to the function of the tool.

Simple scan of a host:
```bash
nmap 192.168.x.x # a private or public IP
```

The range of IPs that can be detected on the local network:
```bash
nmap 192.168.x.x/24
```

Scanning specific ports:
```bash
nmap -p 22,80,443 192.168.x.x  # it can be any port
```

Scanning common ports:
```bash
nmap -F 192.168.x.x
```

#### Advanced Scans

OS detection:
```bash
sudo nmap -O 192.168.x.x
```

Service version detection:
```bash
nmap -sV 192.168.x.x
```

Full host scan (slower but more detailed):
```bash
nmap -A 192.168.x.x
```

Stealth Scanning:
```bash
sudo nmap -sS 192.168.x.x
```

Scanning without ping:
```bash
nmap -Pn 192.168.x.x
```

**Obviously there are more commands and types of scans in Nmap, the ones I mentioned are some of the most important ones**

### Save Results

If you want to keep a register of the scan results, you have some options:

```bash
nmap -oN result.txt 192.168.x.x  # Normal format
nmap -oX result.xml 192.168.x.x  # XML format
nmap -oA full_scan 192.168.x.x  # All formats
```

### Most Common Ports

These are some of the most common and well-known ports that you can identify when performing scans in Nmap.

| Port | Service | Common Use                        |
|------|---------|---------------------------------|
| 21   | FTP     | File Transfer                   |
| 22   | SSH     | Secure Remote Access            |
| 25   | SMTP    | Sending Mail                   |
| 53   | DNS     | Name Resolution (Domains)       |
| 80   | HTTP    | Insecure Web                   |
| 110  | POP3    | Receiving Mail                 |
| 139  | SMB     | File Sharing on Windows (NetBIOS) |
| 443  | HTTPS   | Secure Web (SSL/TLS)           |
| 445  | SMB     | File Sharing Modern Windows (Direct) |
| 3389 | RDP     | Remote Desktop Windows          |

These are just a few examples, Nmap detects thousands of services by scanning well-known and custom ports.

*Nmap is an essential tool in every cybersecurity toolkit, enabling users to understand, map, and secure networks effectively. Its versatility supports both offensive and defensive operations, but remember: always scan responsibly and with proper authorization.*

**Disclaimer:** Use Nmap responsibly. Unauthorized scanning of networks may be considered illegal or unethical. Always have explicit permission when performing security assessments.

for more information:[Nmap official site](https://nmap.org)