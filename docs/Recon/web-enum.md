# Web Enumeration

## Tools

```shell
nmap -sC -sV -p- <target>
whatweb http://<target>
nikto -host http://<target>
gobuster dir -u http://<target> -w /usr/share/wordlists/dirb/common.txt
feroxbuster -u http://<target>
```
