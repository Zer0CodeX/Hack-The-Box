
<div align="center"><font size="4">If you want to support me doing more writeups&nbsp;&nbsp;</font><style>.bmc-button img{height: 34px !important;width: 35px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{padding: 7px 10px 7px 10px !important;line-height: 35px !important;height:51px !important;min-width:217px !important;text-decoration: none !important;display:inline-flex !important;color:#FFFFFF !important;background-color:#FF813F !important;border-radius: 5px !important;border: 1px solid transparent !important;padding: 7px 10px 7px 10px !important;font-size: 22px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#FFFFFF !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/Zer0Code"><img src="https://cdn.buymeacoffee.com/buttons/bmc-new-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:15px;font-size:28px !important;">Buy me a coffee</span></a></div>


---

<div align="center">
<a href="https://www.hackthebox.eu/profile/131282" title="Zer0Code"><img src="https://www.hackthebox.eu/badge/image/131282" alt="alt text" /></a></div>


---

[logo]: Mango.jpg
![alt text](Mango.jpg "Mango")

## NMAP:
As always we will start with NMAP to scan for open ports and services:

```console
# Nmap 7.80 scan initiated Thu Mar  5 18:06:00 2020 as: nmap -p- -sV -sC -O -oN mango_nmap -v 10.10.10.162
RTTVAR has grown to over 2.3 seconds, decreasing to 2.0
Nmap scan report for 10.10.10.162 (10.10.10.162)
Host is up (0.34s latency).
Not shown: 65532 closed ports
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 a8:8f:d9:6f:a6:e4:ee:56:e3:ef:54:54:6d:56:0c:f5 (RSA)
|   256 6a:1c:ba:89:1e:b0:57:2f:fe:63:e1:61:72:89:b4:cf (ECDSA)
|_  256 90:70:fb:6f:38:ae:dc:3b:0b:31:68:64:b0:4e:7d:c9 (ED25519)
80/tcp  open  http     Apache httpd 2.4.29 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: 403 Forbidden
443/tcp open  ssl/http Apache httpd 2.4.29 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: 400 Bad Request
| ssl-cert: Subject: commonName=staging-order.mango.htb/organizationName=Mango Prv Ltd./stateOrProvinceName=None/countryName=IN
| Issuer: commonName=staging-order.mango.htb/organizationName=Mango Prv Ltd./stateOrProvinceName=None/countryName=IN
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2019-09-27T14:21:19
| Not valid after:  2020-09-26T14:21:19
| MD5:   b797 d14d 485f eac3 5cc6 2fed bb7a 2ce6
|_SHA-1: b329 9eca 2892 af1b 5895 053b f30e 861f 1c03 db95
|_ssl-date: TLS randomness does not represent time
| tls-alpn: 
|_  http/1.1
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.80%E=4%D=3/5%OT=22%CT=1%CU=30717%PV=Y%DS=2%DC=I%G=Y%TM=5E612B18
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=101%GCD=1%ISR=10D%TI=Z%CI=Z%II=I%TS=A)SEQ(
OS:SP=101%GCD=1%ISR=10D%TI=Z%CI=Z%TS=A)OPS(O1=M54BST11NW7%O2=M54BST11NW7%O3
OS:=M54BNNT11NW7%O4=M54BST11NW7%O5=M54BST11NW7%O6=M54BST11)WIN(W1=7120%W2=7
OS:120%W3=7120%W4=7120%W5=7120%W6=7120)ECN(R=Y%DF=Y%T=40%W=7210%O=M54BNNSNW
OS:7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF
OS:=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=
OS:%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=
OS:0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RI
OS:PCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 33.798 days (since Fri Jan 31 23:29:32 2020)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=257 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Thu Mar  5 18:38:48 2020 -- 1 IP address (1 host up) scanned in 1967.78 seconds
```
## HTTP (80) :
* First we checked HTTP service on port 80 and we got forbidden ,also we tried bruteforcing but we got nothing

![alt text](01.png "Mango")

---
## HTTPS (443) :

* We checked HTTPS service and got the same CN that we got with NMAP "staging-order.mango.htb"

![alt text](02.png "Mango")

* so we added “staging-order.mango.htb” to /etc/hosts file and now we got a login page.

![alt text](03.png "Mango")

![alt text](04.png "Mango")

![alt text](05.png "Mango")

* After many trials of login bypass we figured out the meaning of box name hint "Mango" ,so we tried MangoDB Nosql authentication bypass 

![alt text](06.png "Mango")
![alt text](07.png "Mango")

* it worked but nothing interested there

![alt text](08.png "Mango")

* We thought about extracting usernames and passwords from database ,so we used that python script in resources from github

![alt text](09.png "Mango")

* We got two usernames and two passwords

![alt text](10.png "Mango")
![alt text](11.png "Mango")
![alt text](12.png "Mango")

* lets use hydra this time to try creds on SSH and find correct pair 

![alt text](13.png "Mango")

---
## User :

* We used Mango user for connecting to the machine with SSH

![alt text](14.png "Mango")

* User flag with owned by admin ,so we tried to switch to admin user using the other password and it worked 

![alt text](15.png "Mango")

---
## Root :

* First we used simple http server python module to copy linpeas to the machine

![alt text](16.png "Mango")
![alt text](17.png "Mango")

* We found good PE vector using Java jjs 

![alt text](18.png "Mango")

* Using was very clear on gtfobin to read the root flag

![alt text](19.png "Mango")
![alt text](20.png "Mango")

---

## Root Shell :

* For getting root shell we copied our SSH key to authorized keys on the machine using jjs

![alt text](21.png "Mango")

* Now we can connect to the machine using SSH as root

![alt text](22.png "Mango")
















## Resources:

[https://github.com/Zer0CodeX/Nosql-MongoDB-injection-username-password-enumeration](https://github.com/Zer0CodeX/Nosql-MongoDB-injection-username-password-enumeration)

[https://gtfobins.github.io/gtfobins/jjs](https://gtfobins.github.io/gtfobins/jjs)

