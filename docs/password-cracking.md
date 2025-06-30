# Password Cracking & Hash Attacks

## John the Ripper

```shell
john --wordlist=/usr/share/wordlists/rockyou.txt hashfile
```

## Hashcat

```shell
hashcat -m 1000 hash.txt /usr/share/wordlists/rockyou.txt
```
