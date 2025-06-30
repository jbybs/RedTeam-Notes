# Linux Privilege Escalation

## Recon

```shell
id
cat /etc/issue
uname -a
```

## SUID Files

```shell
find / -perm -u=s -type f 2>/dev/null
```
