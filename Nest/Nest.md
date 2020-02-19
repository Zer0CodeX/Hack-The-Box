

[logo]: https://github.com/Zer0CodeX/Hack-The-Box/raw/master/Nest/Nest.jpg
![alt text](https://github.com/Zer0CodeX/Hack-The-Box/raw/master/Forest/Forest.png "Forest")

---
## NMAP:
As always we will start with nmap to scan for open ports and services:

```console

# Nmap 7.80 scan initiated Fri Feb 14 18:07:26 2020 as: nmap -sV -sT -sC -p 1-10000 -O -oN nest_nmap 10.10.10.178
Nmap scan report for 10.10.10.178 (10.10.10.178)
Host is up (0.38s latency).
Not shown: 9998 filtered ports
PORT     STATE SERVICE       VERSION
445/tcp  open  microsoft-ds?
4386/tcp open  unknown
| fingerprint-strings: 
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, Kerberos, LANDesk-RC, LDAPBindReq, LDAPSearchReq, LPDString, NULL, RPCCheck, SMBProgNeg, SSLSessionReq, TLSSessionReq, TerminalServer, TerminalServerCookie, X11Probe: 
|     Reporting Service V1.2
|   FourOhFourRequest, GenericLines, GetRequest, HTTPOptions, RTSPRequest, SIPOptions: 
|     Reporting Service V1.2
|     Unrecognised command
|   Help: 
|     Reporting Service V1.2
|     This service allows users to run queries against databases using the legacy HQK format
|     AVAILABLE COMMANDS ---
|     LIST
|     SETDIR <Directory_Name>
|     RUNQUERY <Query_ID>
|     DEBUG <Password>
|_    HELP <Command>
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port4386-TCP:V=7.80%I=7%D=2/14%Time=5E46C658%P=x86_64-pc-linux-gnu%r(NU
SF:LL,21,"\r\nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>")%r(GenericLin
SF:es,3A,"\r\nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>\r\nUnrecognise
SF:d\x20command\r\n>")%r(GetRequest,3A,"\r\nHQK\x20Reporting\x20Service\x2
SF:0V1\.2\r\n\r\n>\r\nUnrecognised\x20command\r\n>")%r(HTTPOptions,3A,"\r\
SF:nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>\r\nUnrecognised\x20comma
SF:nd\r\n>")%r(RTSPRequest,3A,"\r\nHQK\x20Reporting\x20Service\x20V1\.2\r\
SF:n\r\n>\r\nUnrecognised\x20command\r\n>")%r(RPCCheck,21,"\r\nHQK\x20Repo
SF:rting\x20Service\x20V1\.2\r\n\r\n>")%r(DNSVersionBindReqTCP,21,"\r\nHQK
SF:\x20Reporting\x20Service\x20V1\.2\r\n\r\n>")%r(DNSStatusRequestTCP,21,"
SF:\r\nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>")%r(Help,F2,"\r\nHQK\
SF:x20Reporting\x20Service\x20V1\.2\r\n\r\n>\r\nThis\x20service\x20allows\
SF:x20users\x20to\x20run\x20queries\x20against\x20databases\x20using\x20th
SF:e\x20legacy\x20HQK\x20format\r\n\r\n---\x20AVAILABLE\x20COMMANDS\x20---
SF:\r\n\r\nLIST\r\nSETDIR\x20<Directory_Name>\r\nRUNQUERY\x20<Query_ID>\r\
SF:nDEBUG\x20<Password>\r\nHELP\x20<Command>\r\n>")%r(SSLSessionReq,21,"\r
SF:\nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>")%r(TerminalServerCooki
SF:e,21,"\r\nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>")%r(TLSSessionR
SF:eq,21,"\r\nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>")%r(Kerberos,2
SF:1,"\r\nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>")%r(SMBProgNeg,21,
SF:"\r\nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>")%r(X11Probe,21,"\r\
SF:nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>")%r(FourOhFourRequest,3A
SF:,"\r\nHQK\x20Reporting\x20Service\x20V1\.2\r\n\r\n>\r\nUnrecognised\x20
SF:command\r\n>")%r(LPDString,21,"\r\nHQK\x20Reporting\x20Service\x20V1\.2
SF:\r\n\r\n>")%r(LDAPSearchReq,21,"\r\nHQK\x20Reporting\x20Service\x20V1\.
SF:2\r\n\r\n>")%r(LDAPBindReq,21,"\r\nHQK\x20Reporting\x20Service\x20V1\.2
SF:\r\n\r\n>")%r(SIPOptions,3A,"\r\nHQK\x20Reporting\x20Service\x20V1\.2\r
SF:\n\r\n>\r\nUnrecognised\x20command\r\n>")%r(LANDesk-RC,21,"\r\nHQK\x20R
SF:eporting\x20Service\x20V1\.2\r\n\r\n>")%r(TerminalServer,21,"\r\nHQK\x2
SF:0Reporting\x20Service\x20V1\.2\r\n\r\n>");
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: specialized|general purpose|phone
Running (JUST GUESSING): Microsoft Windows 7|2008|Vista|Phone|8.1 (91%)
OS CPE: cpe:/o:microsoft:windows_7 cpe:/o:microsoft:windows_server_2008 cpe:/o:microsoft:windows_vista::sp2 cpe:/o:microsoft:windows_7::sp1 cpe:/o:microsoft:windows_8 cpe:/o:microsoft:windows cpe:/o:microsoft:windows_8.1
Aggressive OS guesses: Microsoft Windows Embedded Standard 7 (91%), Microsoft Windows Server 2008 (90%), Microsoft Windows Server 2008 R2 SP1 (90%), Microsoft Windows Vista SP2, Windows 7 SP1, or Windows Server 2008 (90%), Microsoft Windows Server 2008 R2 (90%), Microsoft Windows 7 (89%), Microsoft Windows 8.1 Update 1 (87%), Microsoft Windows Phone 7.5 or 8.0 (87%), Microsoft Windows 7 or Windows Server 2008 R2 (87%), Microsoft Windows Server 2008 R2 or Windows 8.1 (87%)
No exact OS matches for host (test conditions non-ideal).

Host script results:
|_clock-skew: 1m21s
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2020-02-14T16:14:18
|_  start_date: 2020-02-14T15:05:07

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Feb 14 18:13:36 2020 -- 1 IP address (1 host up) scanned in 370.91 seconds

```
* From NMAP results we can see that SMB is enabled (Port 445/TCP) and there is unknown service is running on port 4386/TCP
---

## SMBMAP :
We started with smbmap to enumerate smb shares as anonymous
```console
root@Kali:~# smbmap -H 10.10.10.178 -u anonymous                                                                                                  
[+] Finding open SMB ports....                                                                                                                                      
[+] Guest SMB session established on 10.10.10.178...                                                                                                                
[+] IP: 10.10.10.178:445        Name: 10.10.10.178                                                                                                                  
        Disk                                                    Permissions     Comment                                                                             
        ----                                                    -----------     -------
        ADMIN$                                                  NO ACCESS       Remote Admin
        C$                                                      NO ACCESS       Default share
        .                                                  
        dr--r--r--                0 Thu Aug  8 00:53:46 2019    .
        dr--r--r--                0 Thu Aug  8 00:53:46 2019    ..
        dr--r--r--                0 Thu Aug  8 00:58:07 2019    IT
        dr--r--r--                0 Mon Aug  5 23:53:41 2019    Production
        dr--r--r--                0 Mon Aug  5 23:53:50 2019    Reports
        dr--r--r--                0 Wed Aug  7 21:07:51 2019    Shared
        Data                                                    READ ONLY
        IPC$                                                    NO ACCESS       Remote IPC
        Secure$                                                 NO ACCESS
        .                                                  
        dr--r--r--                0 Sun Jan 26 01:04:21 2020    .
        dr--r--r--                0 Sun Jan 26 01:04:21 2020    ..
        dr--r--r--                0 Fri Aug  9 17:08:23 2019    Administrator
        dr--r--r--                0 Sun Jan 26 09:21:44 2020    C.Smith
        dr--r--r--                0 Thu Aug  8 19:03:29 2019    L.Frost
        dr--r--r--                0 Thu Aug  8 19:02:56 2019    R.Thompson
        dr--r--r--                0 Thu Aug  8 00:56:02 2019    TempUser
        Users                                                   READ ONLY

```
We got some vaild users on the machine and some shared folders that we can read

---
##SMBCLIENT :
We can use smbclient to access those share folders 
```console
root@Kali:~/HTB/Nest# smbclient -0 //10.10.10.178/data/
Enter WORKGROUP\root's password: 
Try "help" to get a list of possible commands.
smb: \> dir
  .                                   D        0  Thu Aug  8 00:53:46 2019
  ..                                  D        0  Thu Aug  8 00:53:46 2019
  IT                                  D        0  Thu Aug  8 00:58:07 2019
  Production                          D        0  Mon Aug  5 23:53:38 2019
  Reports                             D        0  Mon Aug  5 23:53:44 2019
  Shared                              D        0  Wed Aug  7 21:07:51 2019

                10485247 blocks of size 4096. 6544162 blocks available

smb: \> cd Shared
smb: \Shared\> dir
  .                                   D        0  Wed Aug  7 21:07:51 2019
  ..                                  D        0  Wed Aug  7 21:07:51 2019
  Maintenance                         D        0  Wed Aug  7 21:07:32 2019
  Templates                           D        0  Wed Aug  7 21:08:07 2019

                10485247 blocks of size 4096. 6544162 blocks available
smb: \Shared\> cd Templates\
smb: \Shared\Templates\> dir
  .                                   D        0  Wed Aug  7 21:08:07 2019
  ..                                  D        0  Wed Aug  7 21:08:07 2019
  HR                                  D        0  Wed Aug  7 21:08:01 2019
  Marketing                           D        0  Wed Aug  7 21:08:06 2019

                10485247 blocks of size 4096. 6544162 blocks available
smb: \Shared\Templates\> cd HR\
smb: \Shared\Templates\HR\> dir
  .                                   D        0  Wed Aug  7 21:08:01 2019
  ..                                  D        0  Wed Aug  7 21:08:01 2019
  Welcome Email.txt                   A      425  Thu Aug  8 00:55:36 2019

                10485247 blocks of size 4096. 6544162 blocks available

smb: \Shared\Templates\HR\> get "Welcome Email.txt"
getting file \Shared\Templates\HR\Welcome Email.txt of size 425 as Welcome Email.txt (0.5 KiloBytes/sec) (average 0.5 KiloBytes/sec)

```
* We found that interesting "Welcome Email.txt" file

```console
We would like to extend a warm welcome to our newest member of staff, <FIRSTNAME> <SURNAME>

You will find your home folder in the following location: 
\\HTB-NEST\Users\<USERNAME>

If you have any issues accessing specific services or workstations, please inform the 
IT department and use the credentials below until all systems have been set up for you.

Username: TempUser
Password: welcome2019


Thank you
HR
```
We got valid credentials on the machine as TempUser , Lets use it to access more files on smb

```console
root@Kali:~/HTB/Nest# smbclient -0 //10.10.10.178/data -U TempUser
Enter WORKGROUP\TempUser's password: 
Try "help" to get a list of possible commands.
smb: \> dir
  .                                   D        0  Thu Aug  8 00:53:46 2019
  ..                                  D        0  Thu Aug  8 00:53:46 2019
  IT                                  D        0  Thu Aug  8 00:58:07 2019
  Production                          D        0  Mon Aug  5 23:53:38 2019
  Reports                             D        0  Mon Aug  5 23:53:44 2019
  Shared                              D        0  Wed Aug  7 21:07:51 2019

                10485247 blocks of size 4096. 6544162 blocks available
smb: \> cd IT
smb: \IT\> dir
  .                                   D        0  Thu Aug  8 00:58:07 2019
  ..                                  D        0  Thu Aug  8 00:58:07 2019
  Archive                             D        0  Tue Aug  6 00:33:58 2019
  Configs                             D        0  Thu Aug  8 00:59:34 2019
  Installs                            D        0  Thu Aug  8 00:08:30 2019
  Reports                             D        0  Sun Jan 26 02:09:13 2020
  Tools                               D        0  Tue Aug  6 00:33:43 2019

                10485247 blocks of size 4096. 6544162 blocks available
smb: \IT\> cd Configs\
smb: \IT\Configs\> dir
  .                                   D        0  Thu Aug  8 00:59:34 2019
  ..                                  D        0  Thu Aug  8 00:59:34 2019
  Adobe                               D        0  Wed Aug  7 21:20:09 2019
  Atlas                               D        0  Tue Aug  6 13:16:18 2019
  DLink                               D        0  Tue Aug  6 15:25:27 2019
  Microsoft                           D        0  Wed Aug  7 21:23:26 2019
  NotepadPlusPlus                     D        0  Wed Aug  7 21:31:37 2019
  RU Scanner                          D        0  Wed Aug  7 22:01:13 2019
  Server Manager                      D        0  Tue Aug  6 15:25:19 2019

                10485247 blocks of size 4096. 6544162 blocks available
smb: \IT\Configs\> cd "RU Scanner"
smb: \IT\Configs\RU Scanner\> dir
  .                                   D        0  Wed Aug  7 22:01:13 2019
  ..                                  D        0  Wed Aug  7 22:01:13 2019
  RU_config.xml                       A      270  Thu Aug  8 21:49:37 2019

                10485247 blocks of size 4096. 6544162 blocks available
smb: \IT\Configs\RU Scanner\> get RU_config.xml 
getting file \IT\Configs\RU Scanner\RU_config.xml of size 270 as RU_config.xml (0.9 KiloBytes/sec) (average 0.9 KiloBytes/sec)

```
another interesting file contains credentials for c.smith but the password is encrypted but its not gerneral base64 encryption .

```console
<?xml version="1.0"?>
<ConfigFile xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <Port>389</Port>
  <Username>c.smith</Username>
  <Password>fTEzAfYDoz1YzkqhQkH6GQFYKp1XY5hm7bjOP86yYxE=</Password>
</ConfigFile>
```


So lets try to find more informations .

```console
smb: \IT\Configs\NotepadPlusPlus\> dir
  .                                   D        0  Wed Aug  7 21:31:37 2019
  ..                                  D        0  Wed Aug  7 21:31:37 2019
  config.xml                          A     6451  Thu Aug  8 01:01:25 2019
  shortcuts.xml                       A     2108  Wed Aug  7 21:30:27 2019

                10485247 blocks of size 4096. 6544146 blocks available
smb: \IT\Configs\NotepadPlusPlus\> get config.xml 
getting file \IT\Configs\NotepadPlusPlus\config.xml of size 6451 as config.xml (6.5 KiloBytes/sec) (average 6.5 KiloBytes/sec)
```
We found notpad config file that contains history of opened files list and interesting path "\\\HTB-NEST\Secure$\IT\Carl\"

```console
<!-- The History of opened files list -->
    <FindHistory nbMaxFindHistoryPath="10" nbMaxFindHistoryFilter="10" nbMaxFindHistoryFind="10" nbMaxFindHistoryReplace="10" matchWord="no" matchCase="no" wrap="yes" directionDown="yes" fifRecuisive="yes" fifInHiddenFolder="no" dlgAlwaysVisible="no" fifFilterFollowsDoc="no" fifFolderFollowsDoc="no" searchMode="0" transparencyMode="0" transparency="150">
        <Find name="text" />
        <Find name="txt" />
        <Find name="itx" />
        <Find name="iTe" />
        <Find name="IEND" />
        <Find name="redeem" />
        <Find name="activa" />
        <Find name="activate" />
        <Find name="redeem on" />
        <Find name="192" />
        <Replace name="C_addEvent" />
    </FindHistory>
    <History nbMaxFile="15" inSubMenu="no" customLength="-1">
        <File filename="C:\windows\System32\drivers\etc\hosts" />
        <File filename="\\HTB-NEST\Secure$\IT\Carl\Temp.txt" />
        <File filename="C:\Users\C.Smith\Desktop\todo.txt" />
    </History>
</NotepadPlus>
```
Lets find out if its accessable

```console
smb: \IT\carl\VB Projects\WIP\RU\> dir
  .                                   D        0  Fri Aug  9 17:36:45 2019
  ..                                  D        0  Fri Aug  9 17:36:45 2019
  RUScanner                           D        0  Thu Aug  8 00:05:54 2019
  RUScanner.sln                       A      871  Tue Aug  6 16:45:36 2019

                10485247 blocks of size 4096. 6544146 blocks available

```
We found RUScanner source code




## Resources:
[https://www.dotnetperls.com/console-vbnet](https://www.dotnetperls.com/console-vbnet)
[https://www.howtogeek.com/howto/windows-vista/stupid-geek-tricks-hide-data-in-a-secret-text-file-compartment/](https://www.howtogeek.com/howto/windows-vista/stupid-geek-tricks-hide-data-in-a-secret-text-file-compartment/)





[![alt text](https://www.hackthebox.eu/badge/image/131282)](https://www.hackthebox.eu/profile/131282 "Zer0Code")


