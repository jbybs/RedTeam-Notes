# Nmap

## 🔗 Online Tools

- [Explainshell for Nmap](https://explainshell.com/explain?cmd=nmap+-sC+-sV+-v+)
- [HighOnCoffee Nmap Cheat Sheet](https://highon.coffee/blog/nmap-cheat-sheet/)

---

## 💣 Common Nmap Commands & Examples

### ✅ Quick service/version detection scan on common ports

```bash
nmap -sC -sV <target>
```

- `-sC`: Runs default scripts (like banner grabbing, vuln checks).
- `-sV`: Enables service and version detection.
- Good first scan for smaller environments or single hosts.

---

### ✅ Full TCP port scan with service detection

```bash
nmap -p 1-65535 -sV -sS -T4 <target>
```

- `-p 1-65535`: Scan all 65,535 TCP ports.
- `-sS`: SYN scan (stealthier than full connect).
- `-T4`: Faster timing template (aggressive but not too noisy).
- `-sV`: Detect services and versions.

⚡ **When to use:** Thorough enumeration on single hosts or hardened servers.

---

### ✅ Host discovery in a subnet (Ping sweep)

```bash
nmap -sn 192.168.1.0/24
```

- `-sn`: Ping scan — disables port scanning, just discovers live hosts.
- Useful for mapping an entire subnet quickly.

---

### ✅ Aggressive scan with OS and script detection

```bash
nmap -A <target>
```

- `-A`: Enables OS detection (`-O`), version detection (`-sV`), script scanning (`-sC`), and traceroute.
- Very noisy — should not be used without permission in real environments.

---

### ✅ UDP scan

```bash
nmap -sU -p 53,67,161 <target>
```

- `-sU`: UDP scan.
- UDP is slower and often filtered, but important for finding DNS, SNMP, DHCP services.

---

### ✅ Top 1000 ports (default)

```bash
nmap <target>
```

- Default scan uses top 1,000 most common ports.

---

## 💬 Flag Breakdown

| Flag         | Description                                                              |
|--------------|--------------------------------------------------------------------------|
| `-sC`        | Runs default scripts (equivalent to `--script=default`)                 |
| `-sV`        | Service/version detection                                               |
| `-A`         | Aggressive scan (OS, version, scripts, traceroute)                      |
| `-sS`        | SYN scan (stealthy TCP connect)                                         |
| `-sT`        | TCP connect scan                                                        |
| `-sU`        | UDP scan                                                                |
| `-p`         | Specify ports                                                           |
| `-T0` to `-T5` | Timing options (0 = slowest/stealthiest, 5 = fastest/aggressive)     |
| `--script`   | Specify NSE scripts (e.g., `--script=http-*`)                           |

---

## ⚡ Example Advanced Script Usage

```bash
nmap --script vuln <target>
```

- Runs scripts from the "vuln" category (e.g., checks for common CVEs).

---

## ⭐ Summary

Nmap is one of the most versatile recon tools. Start simple (`-sC -sV`) to get an overview, and expand to full or specialized scans as needed.
