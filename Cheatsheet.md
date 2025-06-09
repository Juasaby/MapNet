# More Nmap Commands #
### Cheatsheet ###

This document provides a quick reference and explanation of essential Nmap commands.
Use it as a cheatsheet to quickly recall syntax, options, and typical use cases.

#### Basic Commands ####

```bash
nmap <IP>  # Basic scanning of an IP.
nmap <range>  # Scan a range of IPs, e.g. nmap 192.168.1.0/24
nmap <IP1> <IP2>  # Scan multiple targets.
nmap -iL <file>  # Load targets from a file.
```

#### Scan Types ####

```bash
nmap -sS  # Quick and sneaky scan that tries to avoid detection.
nmap -sT  # Normal scan that fully connects to the target (more obvious).
nmap -sU  # Checks if UDP ports (used por special services) are open.
nmap -sA  # Tests if a firewall is blocking or allowing connections.
nmap -sW  # Another way to check if ports are open by looking at responses.
nmap -sM  # A less common scan type with special techniques.
nmap -sN  # Sends empty packets to see if ports respond or not.
nmap -sF  # Sends a specific packet to test if a port is open or closed.
nmap -sX  # Sends a special packet with multiple flags to check ports quietly.
```

#### OS and Version Detection ####

```bash
nmap -O  # Detect operating system.
nmap -sV  # Detect service versions.
nmap --version-intensity <0-9>  # Set version detection intensity.
nmap --osscan-guess  # Force OS guess even if uncertain.
```

#### Aggressive and Smart Scans ####

```bash
nmap -A  # Aggressive scan: OS, versions, traceroute, NSE scripts.
nmap -T<0-5>  # Timing template (0 = paranoid, 5 = insane).
nmap --top-ports <n>  # Scan the top N most common ports.
nmap --reason  # Show the reason Nmap gives for port state.
```

#### Port Management ####

```bash
nmap -p <port>  # Scan specific port (e.g. -p 80).
nmap -p-  # Scan all 65535 TCP ports.
nmap --exclude-ports <ports>  # Exclude specific ports.
```

#### Firewall Evasion and Spoofing ####

```bash
nmap -f  # Fragment packets (evade some firewalls).
nmap --data-length <n>  # Append random data to packets.
nmap --source-port <n>  # Set source port (can bypass filters).
nmap -D <decoy1,decoy2,...>  # Use decoys to mask your IP.
nmap --spoof-mac <MAC>  # Spoof your MAC address.
```

#### NSE (Nmap Scripting Engine)

```bash
nmap -sC  # Run default scripts.
nmap --script=<script>  # Run a specific script.
nmap --script-args=<args>  # Provide arguments to scripts.
nmap --script-help <script>  # Get help for a specific script.
nmap --script <category>  # Run scripts by category (e.g., auth, vuln).
```

**View available scripts with:**

```bash
ls /usr/share/nmap/scripts/
```
#### Output and Reporting ####

```bash
nmap -oN <file>	 # Normal output (human-readable).
nmap -oX <file>	 # XML output.
nmap -oG <file>	 # Greppable output.
nmap -oA <basename>	 # Output in all formats (adds .nmap, .xml, .gnmap).
nmap -v	 # Increase verbosity.
nmap -d	 # Debug mode (very verbose).
```

#### Advanced Network Scanning ####

```bash
nmap -Pn  # Skip host discovery (treat all hosts as online).
nmap -n	 # Disable DNS resolution.
nmap -R	 # Enable reverse DNS resolution.
nmap --traceroute  # Trace network path to target.
nmap --badsum  # Send packets with bad checksums.
nmap --max-retries <n>  # Set max number of retries per port.
```

### Practical Examples ###

```bash
# Fast and stealthy scan:
nmap -sS -T4 -Pn 192.168.x.x

# Full scan with OS and service detection:
nmap -A 192.168.x.x

# Scan all ports:
nmap -p- 192.168.x.x

# Run vulnerability scripts:
nmap --script vuln 192.168.x.x
```