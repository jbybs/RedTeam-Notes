# SSH Tunneling & Port Forwarding

## SSH Local Forward

```shell
ssh -L 8000:target:8000 user@host
```

## SSH Dynamic Proxy

```shell
ssh -D 9999 user@host
```

## Remote Forward

```shell
ssh -R 9999:target:22 user@host
```
