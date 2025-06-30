# Tools & General Commands

## CrackMapExec

```shell
crackmapexec smb <IP> -u user -p 'password' --shares
```

## Impacket

```shell
impacket-psexec -hashes <LM>:<NTLM> user@target
```

## Hydra

```shell
hydra -l user -P /usr/share/wordlists/rockyou.txt ssh://<target>
```
