

[logo]: https://github.com/Zer0CodeX/Hack-The-Box/raw/master/Postman/Postman.jpg
![alt text](https://github.com/Zer0CodeX/Hack-The-Box/raw/master/Postman/Postman.jpg "Postman")

## NMAP:
As always we will start with nmap to scan for open ports and services:

```console
root@ip-172-31-36-63:~/HTB/Postman# nmap --top-ports 10000 -sV -sC -O -oN postman_nmap 10.10.10.160

Starting Nmap 7.60 ( https://nmap.org ) at 2020-02-02 12:51 UTC
Nmap scan report for ip-10-10-10-160.us-east-2.compute.internal (10.10.10.160)
Host is up (0.027s latency).
Not shown: 8292 closed ports
PORT      STATE SERVICE VERSION
22/tcp    open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   2048 46:83:4f:f1:38:61:c0:1c:74:cb:b5:d1:4a:68:4d:77 (RSA)
|   256 2d:8d:27:d2:df:15:1a:31:53:05:fb:ff:f0:62:26:89 (ECDSA)
|_  256 ca:7c:82:aa:5a:d3:72:ca:8b:8a:38:3a:80:41:a0:45 (EdDSA)
80/tcp    open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: The Cyber Geek's Personal Website
6379/tcp  open  redis   Redis key-value store 4.0.9
10000/tcp open  http    MiniServ 1.910 (Webmin httpd)
|_http-title: Site doesn't have a title (text/html; Charset=iso-8859-1).
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.60%E=4%D=2/2%OT=22%CT=1%CU=36508%PV=Y%DS=2%DC=I%G=Y%TM=5E36C607
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=108%GCD=1%ISR=10D%TI=Z%CI=Z%II=I%TS=A)SEQ(
OS:SP=108%GCD=1%ISR=10D%TI=Z%CI=Z%TS=A)OPS(O1=M54BST11NW7%O2=M54BST11NW7%O3
OS:=M54BNNT11NW7%O4=M54BST11NW7%O5=M54BST11NW7%O6=M54BST11)WIN(W1=7120%W2=7
OS:120%W3=7120%W4=7120%W5=7120%W6=7120)ECN(R=Y%DF=Y%T=40%W=7210%O=M54BNNSNW
OS:7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF
OS:=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=
OS:%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=
OS:0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RI
OS:PCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Network Distance: 2 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 60.29 seconds


```
We got some useful informations about the box which acting as a Domain controller, 
Computer name: FOREST, 
OS: Windows Server 2016 Standard, 
Domain name: htb.local



## Resources:
[https://gtfobins.github.io/gtfobins/journalctl/](https://gtfobins.github.io/gtfobins/journalctl/)



[![alt text](https://www.hackthebox.eu/badge/image/131282)](https://www.hackthebox.eu/profile/131282 "Zer0Code")


