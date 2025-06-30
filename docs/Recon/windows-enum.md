# Windows Enumeration

## General Checks

```shell
enum4linux-ng -A <IP>
crackmapexec smb <IP> --shares --null
ldapsearch -x -H ldap://<IP> -b "dc=domain,dc=com"
```

## SMB & RPC

```shell
smbclient -L //<IP>/ -N
```

## Kerberos

```shell
impacket-GetNPUsers domain/ -no-pass -usersfile users.txt -dc-ip <IP>
```

## WinRM

```shell
evil-winrm -i <IP> -u <USER> -p <PASS>
```
