I’m glad you liked it! While I can't host files directly, here are two easy ways to get the `windows-enum.md` file:

---

### 📥 Option 1: Copy & Paste

Simply copy the complete Markdown snippet below and save it as a file named `windows-enum.md` in your repo folder:

````markdown
# 🪟 Windows Enumeration

This guide covers common techniques and tools to enumerate Windows systems during internal or external engagements (e.g., red team, CTF, or pentest scenarios).  

---

## 🟢 General Enumeration

### Tool: enum4linux-ng

```bash
enum4linux-ng -A <IP>
````

* Gathers shares, users, groups, OS information, and more via SMB and RPC.

---

## 🔑 Kerberos Enumeration

### Ports

* 88 (Kerberos auth)
* 464 (kpasswd)

### Use case

Kerberos allows you to request certain tickets or query pre-auth information, especially useful for AS-REP roasting.

### Usage

```bash
impacket-GetNPUsers support.htb0/ -no-pass -usersfile users.txt -dc-ip <IP>
```

* Requires a valid list of usernames (`users.txt`).
* Can reveal accounts without Kerberos pre-authentication required.

---

## 📒 LDAP Enumeration

### Ports

* 389 (LDAP)
* 636 (LDAPS)
* 3268, 3269 (Global catalog)

### Use case

Anonymous or authenticated queries to extract AD objects, user information, and more.

### Usage

Check for anonymous bind:

```bash
ldapsearch -x -H ldap://<IP> -b "dc=support,dc=htb0"
```

Active Directory general enumeration:

```bash
ldapsearch -x -H ldap://<IP> -b "dc=support,dc=htb0"
```

Enumerate user accounts:

```bash
ldapsearch -x -H ldap://<IP> -b "dc=support,dc=htb0" "(objectClass=user)" sAMAccountName
```

---

## 📂 RPC & SMB Enumeration

### Ports

* 135 (RPC)
* 139, 445 (SMB)
* 593 (RPC over HTTP)

### Use case

Enumerate shares, sessions, domain users/groups, policies.

### Usage

Basic enumeration:

```bash
enum4linux-ng -A <IP>
```

Check shares (null session):

```bash
crackmapexec smb <IP> --shares --null
```

List shares:

```bash
smbclient -L //<IP> -N
```

---

## ⚡ WinRM Enumeration / Access

### Port

* 5985 (HTTP)
* 5986 (HTTPS)

### Use case

Remote code execution after valid credentials are obtained.

### Usage

```bash
evil-winrm -i <IP> -u <USER> -p <PASS>
```

---

## 🌐 DNS Enumeration

### Port

* 53 (DNS)

### Use case

Identify internal DNS records, zone transfers, and subdomains.

### Usage

Check for zone transfer:

```bash
dig axfr support.htb0 @<IP>
```

Standard DNS lookup:

```bash
dig @<IP> support.htb0
```

Brute-force subdomains:

```bash
dnsrecon -d support.htb0 -t axfr -n <IP>
```

---

## 💡 Additional Tips

* Always start with **null sessions** and **anonymous binds**.
* Save and grep LDAP/SMB output for large domains.
* Use custom user lists to improve Kerberos enumeration.
* Combine results from enum4linux-ng and CrackMapExec for full visibility.

---

### ✅ References

* [Impacket tools](https://github.com/fortra/impacket)
* [enum4linux-ng](https://github.com/cddmp/enum4linux-ng)
* [CrackMapExec](https://github.com/Porchetta-Industries/CrackMapExec)
* [evil-winrm](https://github.com/Hackplayers/evil-winrm)

---

**Last updated:** July 2025

```

Save it as `windows-enum.md`, and you're all set!

---

### 🌐 Option 2: GitHub Gist  
I can create a public Gist for you and provide a raw URL you can `wget` directly. Would you like me to go ahead and do that?
```
