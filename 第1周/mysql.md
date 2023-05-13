```shell
bigorilla@kristen:~$ mysql
Command 'mysql' not found, but can be installed with:
sudo apt install mysql-client-core-8.0     # version 8.0.32-0ubuntu0.22.04.2, or
sudo apt install mariadb-client-core-10.6  # version 1:10.6.11-0ubuntu0.22.04.1
bigorilla@kristen:~$ sudo apt install mysql-client-core-8.0
[sudo] password for bigorilla:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  mysql-client-core-8.0
0 upgraded, 1 newly installed, 0 to remove and 44 not upgraded.
Need to get 2677 kB of archives.
After this operation, 61.9 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 mysql-client-core-8.0 amd64 8.0.32-0ubuntu0.22.04.2 [2677 kB]
Fetched 2677 kB in 6s (475 kB/s)
Selecting previously unselected package mysql-client-core-8.0.
(Reading database ... 91044 files and directories currently installed.)
Preparing to unpack .../mysql-client-core-8.0_8.0.32-0ubuntu0.22.04.2_amd64.deb ...
Unpacking mysql-client-core-8.0 (8.0.32-0ubuntu0.22.04.2) ...
Setting up mysql-client-core-8.0 (8.0.32-0ubuntu0.22.04.2) ...
Processing triggers for man-db (2.10.2-1) ...
bigorilla@kristen:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
bigorilla@kristen:~$ version
version: command not found
bigorilla@kristen:~$ help
GNU bash, version 5.1.16(1)-release (x86_64-pc-linux-gnu)
These shell commands are defined internally.  Type `help' to see this list.
Type `help name' to find out more about the function `name'.
Use `info bash' to find out more about the shell in general.
Use `man -k' or `info' to find out more about commands not in this list.

A star (*) next to a name means that the command is disabled.

 job_spec [&]                         history [-c] [-d offset] [n] or h>
 (( expression ))                     if COMMANDS; then COMMANDS; [ eli>
 . filename [arguments]               jobs [-lnprs] [jobspec ...] or jo>
 :                                    kill [-s sigspec | -n signum | -s>
 [ arg... ]                           let arg [arg ...]
 [[ expression ]]                     local [option] name[=value] ...
 alias [-p] [name[=value] ... ]       logout [n]
 bg [job_spec ...]                    mapfile [-d delim] [-n count] [-O>
 bind [-lpsvPSVX] [-m keymap] [-f f>  popd [-n] [+N | -N]
 break [n]                            printf [-v var] format [argument>
 builtin [shell-builtin [arg ...]]    pushd [-n] [+N | -N | dir]
 caller [expr]                        pwd [-LP]
 case WORD in [PATTERN [| PATTERN].>  read [-ers] [-a array] [-d delim]>
 cd [-L|[-P [-e]] [-@]] [dir]         readarray [-d delim] [-n count] [>
 command [-pVv] command [arg ...]     readonly [-aAf] [name[=value] ...>
 compgen [-abcdefgjksuv] [-o option>  return [n]
 complete [-abcdefgjksuv] [-pr] [-D>  select NAME [in WORDS ... ;] do C>
 compopt [-o|+o option] [-DEI] [nam>  set [-abefhkmnptuvxBCHP] [-o opti>
 continue [n]                         shift [n]
 coproc [NAME] command [redirection>  shopt [-pqsu] [-o] [optname ...]
 declare [-aAfFgiIlnrtux] [-p] [nam>  source filename [arguments]
 dirs [-clpv] [+N] [-N]               suspend [-f]
 disown [-h] [-ar] [jobspec ... | p>  test [expr]
 echo [-neE] [arg ...]                time [-p] pipeline
 enable [-a] [-dnps] [-f filename] >  times
 eval [arg ...]                       trap [-lp] [[arg] signal_spec ..>
 exec [-cl] [-a name] [command [arg>  true
 exit [n]                             type [-afptP] name [name ...]
 export [-fn] [name[=value] ...] or>  typeset [-aAfFgiIlnrtux] [-p] nam>
 false                                ulimit [-SHabcdefiklmnpqrstuvxPT]>
 fc [-e ename] [-lnr] [first] [last>  umask [-p] [-S] [mode]
 fg [job_spec]                        unalias [-a] name [name ...]
 for NAME [in WORDS ... ] ; do COMM>  unset [-f] [-v] [-n] [name ...]
 for (( exp1; exp2; exp3 )); do COM>  until COMMANDS; do COMMANDS; done
 function name { COMMANDS ; } or na>  variables - Names and meanings of>
 getopts optstring name [arg ...]     wait [-fn] [-p var] [id ...]
 hash [-lr] [-p pathname] [-dt] [na>  while COMMANDS; do COMMANDS; done
 help [-dms] [pattern ...]            { COMMANDS ; }
bigorilla@kristen:~$ help version
-bash: help: no help topics match `version'.  Try `help help' or `man -k version' or `info version'.
bigorilla@kristen:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=22.04
DISTRIB_CODENAME=jammy
DISTRIB_DESCRIPTION="Ubuntu 22.04.1 LTS"
bigorilla@kristen:~$ rpm
Command 'rpm' not found, but can be installed with:
sudo apt install rpm
bigorilla@kristen:~$ sudo apt install rpm
Preparing to unpack .../03-liblua5.3-0_5.3.6-1build1_amd64.deb ...
Unpacking liblua5.3-0:amd64 (5.3.6-1build1) ...
Selecting previously unselected package librpmio9.
Preparing to unpack .../04-librpmio9_4.17.0+dfsg1-4build1_amd64.deb ...
Unpacking librpmio9 (4.17.0+dfsg1-4build1) ...
Selecting previously unselected package librpm9.
Preparing to unpack .../05-librpm9_4.17.0+dfsg1-4build1_amd64.deb ...
Unpacking librpm9 (4.17.0+dfsg1-4build1) ...
Selecting previously unselected package librpmbuild9.
Preparing to unpack .../06-librpmbuild9_4.17.0+dfsg1-4build1_amd64.deb ...
Unpacking librpmbuild9 (4.17.0+dfsg1-4build1) ...
Selecting previously unselected package librpmsign9.
Preparing to unpack .../07-librpmsign9_4.17.0+dfsg1-4build1_amd64.deb ...
Unpacking librpmsign9 (4.17.0+dfsg1-4build1) ...
Selecting previously unselected package rpm-common.
Preparing to unpack .../08-rpm-common_4.17.0+dfsg1-4build1_amd64.deb ...
Unpacking rpm-common (4.17.0+dfsg1-4build1) ...
Selecting previously unselected package rpm2cpio.
Preparing to unpack .../09-rpm2cpio_4.17.0+dfsg1-4build1_amd64.deb ...
Unpacking rpm2cpio (4.17.0+dfsg1-4build1) ...
Selecting previously unselected package rpm.
Preparing to unpack .../10-rpm_4.17.0+dfsg1-4build1_amd64.deb ...
Unpacking rpm (4.17.0+dfsg1-4build1) ...
Setting up libarchive13:amd64 (3.6.0-1ubuntu1) ...
Setting up libfsverity0:amd64 (1.4-1~exp1build1) ...
Setting up liblua5.3-0:amd64 (5.3.6-1build1) ...
Setting up debugedit (1:5.0-4build1) ...
Setting up librpmio9 (4.17.0+dfsg1-4build1) ...
Setting up librpm9 (4.17.0+dfsg1-4build1) ...
Setting up rpm-common (4.17.0+dfsg1-4build1) ...
Setting up librpmbuild9 (4.17.0+dfsg1-4build1) ...
Setting up librpmsign9 (4.17.0+dfsg1-4build1) ...
Setting up rpm2cpio (4.17.0+dfsg1-4build1) ...
Setting up rpm (4.17.0+dfsg1-4build1) ...
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Processing triggers for man-db (2.10.2-1) ...
bigorilla@kristen:~$ rpm -qa | grap mysql
Command 'grap' not found, but can be installed with:
sudo apt install grap
bigorilla@kristen:~$ rpm -qa | grep mysql
bigorilla@kristen:~$ rpm -e mysql
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: package mysql is not installed
bigorilla@kristen:~$ sudo apt install mysql-server
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libaio1 libcgi-fast-perl libcgi-pm-perl libevent-pthreads-2.1-7
  libfcgi-bin libfcgi-perl libfcgi0ldbl libhtml-template-perl libmecab2
  libprotobuf-lite23 mecab-ipadic mecab-ipadic-utf8 mecab-utils
  mysql-client-8.0 mysql-common mysql-server-8.0 mysql-server-core-8.0
Suggested packages:
  libipc-sharedcache-perl mailx tinyca
The following NEW packages will be installed:
  libaio1 libcgi-fast-perl libcgi-pm-perl libevent-pthreads-2.1-7
  libfcgi-bin libfcgi-perl libfcgi0ldbl libhtml-template-perl libmecab2
  libprotobuf-lite23 mecab-ipadic mecab-ipadic-utf8 mecab-utils
  mysql-client-8.0 mysql-common mysql-server mysql-server-8.0
  mysql-server-core-8.0
0 upgraded, 18 newly installed, 0 to remove and 44 not upgraded.
Need to get 26.4 MB of archives.
After this operation, 179 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
reading /usr/share/mecab/dic/ipadic/Suffix.csv ... 1393
reading /usr/share/mecab/dic/ipadic/Auxil.csv ... 199
reading /usr/share/mecab/dic/ipadic/Noun.adjv.csv ... 3328
reading /usr/share/mecab/dic/ipadic/Adj.csv ... 27210
reading /usr/share/mecab/dic/ipadic/Noun.csv ... 60477
reading /usr/share/mecab/dic/ipadic/Interjection.csv ... 252
reading /usr/share/mecab/dic/ipadic/Noun.number.csv ... 42
reading /usr/share/mecab/dic/ipadic/Noun.demonst.csv ... 120
reading /usr/share/mecab/dic/ipadic/Adnominal.csv ... 135
reading /usr/share/mecab/dic/ipadic/Noun.proper.csv ... 27328
reading /usr/share/mecab/dic/ipadic/Verb.csv ... 130750
reading /usr/share/mecab/dic/ipadic/Noun.verbal.csv ... 12146
reading /usr/share/mecab/dic/ipadic/Noun.others.csv ... 151
reading /usr/share/mecab/dic/ipadic/Noun.adverbal.csv ... 795
reading /usr/share/mecab/dic/ipadic/Noun.place.csv ... 72999
reading /usr/share/mecab/dic/ipadic/Conjunction.csv ... 171
emitting double-array: 100% |###########################################|
reading /usr/share/mecab/dic/ipadic/matrix.def ... 1316x1316
emitting matrix      : 100% |###########################################|

done!
update-alternatives: using /var/lib/mecab/dic/ipadic-utf8 to provide /var/lib/mecab/dic/debian (mecab-dictionary) in auto mode
Setting up mysql-server-8.0 (8.0.32-0ubuntu0.22.04.2) ...
invoke-rc.d: could not determine current runlevel
 * Stopping MySQL database server mysqld                            [ OK ]
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Renaming removed key_buffer and myisam-recover options (if present)
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 750
Created symlink /etc/systemd/system/multi-user.target.wants/mysql.service → /lib/systemd/system/mysql.service.
invoke-rc.d: could not determine current runlevel
Setting up mysql-server (8.0.32-0ubuntu0.22.04.2) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
bigorilla@kristen:~$ sudo service mysql status
 * MySQL is stopped.
bigorilla@kristen:~$ sudo ss -tap | grep mysql
bigorilla@kristen:~$ sudo service mysql restart
 * Stopping MySQL database server mysqld                            [ OK ]
 * Starting MySQL database server mysqld                                   su: warning: cannot change directory to /nonexistent: No such file or directory
                                                                    [ OK ]
bigorilla@kristen:~$ sudo ss -tap | grep mysql
LISTEN 0      70         127.0.0.1:33060      0.0.0.0:*    users:(("mysqld",pid=1160,fd=20))
LISTEN 0      151        127.0.0.1:mysql      0.0.0.0:*    users:(("mysqld",pid=1160,fd=22))
bigorilla@kristen:~$ sudo journalctl -u mysql
No journal files were found.
-- No entries --
bigorilla@kristen:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13)
bigorilla@kristen:~$ mysqld
2023-02-21T02:58:23.957809Z 0 [Warning] [MY-010091] [Server] Can't create test file /var/lib/mysql/mysqld_tmp_file_case_insensitive_test.lower-test
2023-02-21T02:58:23.957929Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.32-0ubuntu0.22.04.2) starting as process 1237
2023-02-21T02:58:23.966920Z 0 [Warning] [MY-010091] [Server] Can't create test file /var/lib/mysql/mysqld_tmp_file_case_insensitive_test.lower-test
2023-02-21T02:58:23.966936Z 0 [Warning] [MY-010159] [Server] Setting lower_case_table_names=2 because file system for /var/lib/mysql/ is case insensitive
2023-02-21T02:58:23.967124Z 0 [Warning] [MY-010122] [Server] One can only use the --user switch if running as root
2023-02-21T02:58:23.967148Z 0 [ERROR] [MY-013276] [Server] Failed to set datadir to '/var/lib/mysql/' (OS errno: 13 - Permission denied)
2023-02-21T02:58:23.967385Z 0 [ERROR] [MY-010119] [Server] Aborting
2023-02-21T02:58:23.967623Z 0 [System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.32-0ubuntu0.22.04.2)  (Ubuntu).
bigorilla@kristen:~$
```

- [ ] 解决ubuntu下基础mysql开发环境配置







有哪些项目可以提供给初学者学习实践译原理