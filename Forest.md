## NMAP:

```markdown
root@test:~/HTB/Forest# nmap --top-ports 10000 -sV -sC -O -oN forest_nmap 10.10.10.161
Starting Nmap 7.80 ( https://nmap.org ) at 2020-01-23 08:37 EET
Nmap scan report for FOREST.htb.local (10.10.10.161)
Host is up (0.36s latency).
Not shown: 8306 closed ports
PORT      STATE SERVICE      VERSION
53/tcp    open  domain?
| fingerprint-strings: 
|   DNSVersionBindReqTCP: 
|     version
|_    bind
88/tcp    open  kerberos-sec Microsoft Windows Kerberos (server time: 2020-01-23 06:48:39Z)
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
389/tcp   open  ldap         Microsoft Windows Active Directory LDAP (Domain: htb.local, Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds Windows Server 2016 Standard 14393 microsoft-ds (workgroup: HTB)
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http   Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped
3268/tcp  open  ldap         Microsoft Windows Active Directory LDAP (Domain: htb.local, Site: Default-First-Site-Name)
3269/tcp  open  tcpwrapped
5985/tcp  open  http         Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
9389/tcp  open  mc-nmf       .NET Message Framing
47001/tcp open  http         Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port53-TCP:V=7.80%I=7%D=1/23%Time=5E293FE8%P=x86_64-pc-linux-gnu%r(DNSV
SF:ersionBindReqTCP,20,"\0\x1e\0\x06\x81\x04\0\x01\0\0\0\0\0\0\x07version\
SF:x04bind\0\0\x10\0\x03");
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.80%E=4%D=1/23%OT=53%CT=1%CU=40345%PV=Y%DS=2%DC=I%G=Y%TM=5E29410
OS:F%P=x86_64-pc-linux-gnu)SEQ(SP=102%GCD=1%ISR=109%CI=RD%II=I%TS=A)SEQ(SP=
OS:102%GCD=1%ISR=109%TI=RD%II=I%TS=B)SEQ(SP=102%GCD=1%ISR=109%TI=RD%CI=RD%I
OS:I=I%TS=A)OPS(O1=M54BNW8ST11%O2=M54BNW8ST11%O3=M54BNW8NNT11%O4=M54BNW8ST1
OS:1%O5=M54BNW8ST11%O6=M54BST11)WIN(W1=2000%W2=2000%W3=2000%W4=2000%W5=2000
OS:%W6=2000)ECN(R=Y%DF=Y%T=80%W=2000%O=M54BNW8NNS%CC=Y%Q=)T1(R=Y%DF=Y%T=80%
OS:S=O%A=S+%F=AS%RD=0%Q=)T2(R=Y%DF=Y%T=80%W=0%S=Z%A=S%F=AR%O=%RD=0%Q=)T3(R=
OS:Y%DF=Y%T=80%W=0%S=Z%A=O%F=AR%O=%RD=0%Q=)T4(R=Y%DF=Y%T=80%W=0%S=A%A=O%F=R
OS:%O=%RD=0%Q=)T5(R=Y%DF=Y%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=
OS:80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0
OS:%Q=)U1(R=Y%DF=N%T=80%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R
OS:=Y%DFI=N%T=80%CD=Z)

Network Distance: 2 hops
Service Info: Host: FOREST; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: 2h48m05s, deviation: 4h37m11s, median: 8m03s
| smb-os-discovery: 
|   OS: Windows Server 2016 Standard 14393 (Windows Server 2016 Standard 6.3)
|   Computer name: FOREST
|   NetBIOS computer name: FOREST\x00
|   Domain name: htb.local
|   Forest name: htb.local
|   FQDN: FOREST.htb.local
|_  System time: 2020-01-22T22:51:26-08:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: required
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2020-01-23T06:51:24
|_  start_date: 2020-01-23T05:20:10

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 500.27 seconds
```
## impacket GetADUsers.py
```markdown
root@test:~/tools/Windows/impacket/examples# python GetADUsers.py -all -dc-ip 10.10.10.161 htb.local/
Impacket v0.9.21-dev - Copyright 2019 SecureAuth Corporation

[*] Querying 10.10.10.161 for information about domain.
Name                  Email                           PasswordLastSet      LastLogon           
--------------------  ------------------------------  -------------------  -------------------
Administrator         Administrator@htb.local         2019-09-18 19:09:08.342879  2019-10-07 12:57:07.299606 
Guest                                                 <never>              <never>             
DefaultAccount                                        <never>              <never>             
krbtgt                                                2019-09-18 12:53:23.467452  <never>             
$331000-VK4ADACQNUCA                                  <never>              <never>             
SM_2c8eef0a09b545acb  SystemMailbox{1f05a927-89c0-4725-adca-4527114196a1}@htb.local  <never>              <never>             
SM_ca8c2ed5bdab4dc9b  SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}@htb.local  <never>              <never>             
SM_75a538d3025e4db9a  SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}@htb.local  <never>              <never>             
SM_681f53d4942840e18  DiscoverySearchMailbox{D919BA05-46A6-415f-80AD-7E09334BB852}@htb.local  <never>              <never>             
SM_1b41c9286325456bb  Migration.8f3e7716-2011-43e4-96b1-aba62d229136@htb.local  <never>              <never>             
SM_9b69f1b9d2cc45549  FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042@htb.local  <never>              <never>             
SM_7c96b981967141ebb  SystemMailbox{D0E409A0-AF9B-4720-92FE-AAC869B0D201}@htb.local  <never>              <never>             
SM_c75ee099d0a64c91b  SystemMailbox{2CE34405-31BE-455D-89D7-A7C7DA7A0DAA}@htb.local  <never>              <never>             
SM_1ffab36a2f5f479cb  SystemMailbox{8cc370d3-822a-4ab8-a926-bb94bd0641a9}@htb.local  <never>              <never>             
HealthMailboxc3d7722  HealthMailboxc3d7722415ad41a5b19e3e00e165edbe@htb.local  2019-09-24 00:51:31.892097  2019-09-24 00:57:12.361516 
HealthMailboxfc9daad  HealthMailboxfc9daad117b84fe08b081886bd8a5a50@htb.local  2019-09-24 00:51:35.267114  2019-09-24 00:52:05.736012 
HealthMailboxc0a90c9  HealthMailboxc0a90c97d4994429b15003d6a518f3f5@htb.local  2019-09-19 13:56:35.206329  <never>             
HealthMailbox670628e  HealthMailbox670628ec4dd64321acfdf6e67db3a2d8@htb.local  2019-09-19 13:56:45.643993  <never>             
HealthMailbox968e74d  HealthMailbox968e74dd3edb414cb4018376e7dd95ba@htb.local  2019-09-19 13:56:56.143969  <never>             
HealthMailbox6ded678  HealthMailbox6ded67848a234577a1756e072081d01f@htb.local  2019-09-19 13:57:06.597012  <never>             
HealthMailbox83d6781  HealthMailbox83d6781be36b4bbf8893b03c2ee379ab@htb.local  2019-09-19 13:57:17.065809  <never>             
HealthMailboxfd87238  HealthMailboxfd87238e536e49e08738480d300e3772@htb.local  2019-09-19 13:57:27.487679  <never>             
HealthMailboxb01ac64  HealthMailboxb01ac647a64648d2a5fa21df27058a24@htb.local  2019-09-19 13:57:37.878559  <never>             
HealthMailbox7108a4e  HealthMailbox7108a4e350f84b32a7a90d8e718f78cf@htb.local  2019-09-19 13:57:48.253341  <never>             
HealthMailbox0659cc1  HealthMailbox0659cc188f4c4f9f978f6c2142c4181e@htb.local  2019-09-19 13:57:58.643994  <never>             
sebastien                                             2019-09-20 02:29:59.544725  2019-09-23 00:29:29.586227 
lucinda                                               2019-09-20 02:44:13.233891  <never>             
svc-alfresco                                          2020-01-23 10:09:38.897050  2019-09-23 13:09:47.931194 
andy                                                  2019-09-23 00:44:16.291082  <never>             
mark                                                  2019-09-21 00:57:30.243568  <never>             
santi                                                 2019-09-21 01:02:55.134828  <never>             
jan                                                   2020-01-23 09:30:57.924703  <never>
```
## Resources:

https://securityonline.info/aclpwn/
