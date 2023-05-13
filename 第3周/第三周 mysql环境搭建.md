第三周 mysql环境搭建

想证明docker是搭建mysql开发环境的环境之一

`site:bilibili.com win mysql docker`

> 不打算在线安装mysql了
>
> 直接用官网给的一个zip文件来下载

为啥好多视频教程教的都是直接下载一个.msi文件来配置环境

很少直接使用.zip来配置环境的



`sc delete mysql` 

> 指令执行之后没有提示
>
> 解释指令本身



![image-20230308095041437](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308095041437.png)



![image-20230308100732724](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308100732724.png)

> 之前下载的是debug-test.zip
>
> 和弹幕说的不一致
>
> bin目录下的基础文件都没有
>
> 所以怀疑自己理解错了
>
> 以为两个安装包之间的关系是包含的



设置mysql系统环境变量的时候 直接设置在管理员下面了

- 解释说数据库的各种操作时在管理员权限下生成的
- 减少出现其他乱七八糟错误的可能



my.ini file content of mysql-8.0.32

The exact content of the `my.ini` file for `mysql-8.0.32` can vary depending on the specific installation and configuration options chosen during installation. However, below is an example of what the `my.ini` file might look like:

```makefile
# MySQL Server Instance Configuration File
# ----------------------------------------

# CLIENT SECTION
[client]
port=3306

# The MySQL server
[mysqld]
port=3306
basedir="C:/Program Files/MySQL/MySQL Server 8.0/"
datadir="C:/ProgramData/MySQL/MySQL Server 8.0/Data/"
default_authentication_plugin=mysql_native_password
character-set-server=utf8mb4
collation-server=utf8mb4_unicode_ci

# The minimum and maximum size of the temporary tablespace
tmp_table_size=64M
max_heap_table_size=64M

# The maximum allowed packet size
max_allowed_packet=256M

# The default storage engine
default_storage_engine=INNODB

# The innodb_buffer_pool_size sets the size of the buffer pool
innodb_buffer_pool_size=8G

# The innodb_log_file_size sets the size of the log files in MB
innodb_log_file_size=2G

# The innodb_flush_log_at_trx_commit setting controls the frequency of flushing the log buffer
innodb_flush_log_at_trx_commit=1

# The bind-address setting restricts connections to the specified IP address
bind-address=0.0.0.0

# The skip-name-resolve setting can improve performance by skipping DNS lookups
skip-name-resolve

# The log-error setting specifies the error log file path
log-error="C:/ProgramData/MySQL/MySQL Server 8.0/Logs/Error.log"

# The log-output setting controls the destination of log output
log-output=file

```

```makefile
# MySQL Server Instance Configuration File
# ----------------------------------------

# CLIENT SECTION
[client]
port=3306

# The MySQL server
[mysqld]
port=3306
basedir="F:/Software/MySQL/mysql-8.0.32-winx64"
datadir="F:/Software/MySQL/mysql-8.0.32-winx64/Data/"
default_authentication_plugin=mysql_native_password
character-set-server=utf8mb4
collation-server=utf8mb4_unicode_ci

# The minimum and maximum size of the temporary tablespace
tmp_table_size=64M
max_heap_table_size=64M

# The maximum allowed packet size
max_allowed_packet=256M

# The default storage engine
default_storage_engine=INNODB

# The innodb_buffer_pool_size sets the size of the buffer pool
innodb_buffer_pool_size=8G

# The innodb_log_file_size sets the size of the log files in MB
innodb_log_file_size=2G

# The innodb_flush_log_at_trx_commit setting controls the frequency of flushing the log buffer
innodb_flush_log_at_trx_commit=1

# The bind-address setting restricts connections to the specified IP address
bind-address=0.0.0.0

# The skip-name-resolve setting can improve performance by skipping DNS lookups
skip-name-resolve

# The log-error setting specifies the error log file path
log-error="F:/Software/MySQL/mysql-8.0.32-winx64/Logs/Error.log"

# The log-output setting controls the destination of log output
log-output=file

#skip safety check 配置好之后需要删除
skip-grant-tables

```



![image-20230308104154978](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308104154978.png)





```makefile
Microsoft Windows [版本 10.0.19044.2604]
(c) Microsoft Corporation。保留所有权利。

C:\WINDOWS\system32>cd /F F:\Software\MySQL\mysql-8.0.32-winx64\bin
文件名、目录名或卷标语法不正确。

C:\WINDOWS\system32>F:\Software\MySQL\mysql-8.0.32-winx64\bin
'F:\Software\MySQL\mysql-8.0.32-winx64\bin' 不是内部或外部命令，也不是可运行的程序
或批处理文件。

C:\WINDOWS\system32>cd /F F:\Software\MySQL\mysql-8.0.32-winx64\bin
文件名、目录名或卷标语法不正确。

C:\WINDOWS\system32>cd/F F:\Software\MySQL\mysql-8.0.32-winx64\bin
文件名、目录名或卷标语法不正确。

C:\WINDOWS\system32>F:

F:\>cd F:\Software\MySQL\mysql-8.0.32-winx64\bin

F:\Software\MySQL\mysql-8.0.32-winx64\bin>
```

> win的管理员权限下的操作很麻烦

```makefile
mysqld: Can't get stat of 'C:\Users\Public\Documents\Wondershare\CreatorTemp' (OS errno 2 - No such file or directory)
2023-03-08T02:51:43.081715Z 0 [ERROR] [MY-010187] [Server] Could not open file 'F:\Software\MySQL\mysql-8.0.32-winx64\Logs\Error.log' for error logging: Permission denied
2023-03-08T02:51:43.082686Z 0 [ERROR] [MY-013236] [Server] The designated data directory F:\Software\MySQL\mysql-8.0.32-winx64\Data\ is unusable. You can remove all files that the server added to it.
2023-03-08T02:51:43.083755Z 0 [ERROR] [MY-010119] [Server] Aborting
```

> 还是自己之前误删系统文件的原因



![image-20230308111921938](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308111921938.png)





how to deal with this problem MySQL needs a place to write temp files, found it had no access to C:\Users\Public\Documents\Wondershare\CreatorTemp\ib9E78.tmp What is the content of the environment var TEMP? It's usually something like ... TEMP=C:\Users\USERNAME\AppData\Local\Temp ... where USERNAME is your Windows login. Has "Wondershare" software hijacked that setting?



The error message indicates that MySQL is attempting to write temporary files to a directory where it ==does not have sufficient access==, which could be due to a permissions issue or because the directory does not exist.

To resolve this issue, you can try the following steps:

1. Check the value of the TEMP environment variable by opening a command prompt and typing `echo %TEMP%`. This should return the path to the temporary directory that Windows uses.

2. Make sure that the directory specified in the error message (C:\Users\Public\Documents\Wondershare\CreatorTemp) exists and that MySQL has sufficient permissions to write to it. You may need to adjust the permissions on the directory or create it if it does not exist.

3. ==Check if the "Wondershare" software is running and if it has hijacked the TEMP environment variable==. If this is the case, you may need to uninstall or disable the software, or adjust its settings to use a different temporary directory.

   ![image-20230308123123399](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308123123399.png)

4. If none of the above steps work, you can ==try setting the TEMP environment variable to a different directory that MySQL can access==. You can do this by opening the System Properties dialog, selecting the Advanced tab, clicking the Environment Variables button, and then adding or modifying the TEMP variable in the User Variables section.

   ![image-20230308123505266](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308123505266.png)

After making any changes, you may need to restart your computer or MySQL server for them to take effect.





```makefile
F:\Software\MySQL\mysql-8.0.32-winx64\bin>mysqld --initialize-insecure --user=mysql
2023-03-08T04:40:19.092734Z 0 [Warning] [MY-010918] [Server] 'default_authentication_plugin' is deprecated and will be removed in a future release. Please use authentication_policy instead.
2023-03-08T04:40:19.093355Z 0 [System] [MY-013169] [Server] F:\Software\MySQL\mysql-8.0.32-winx64\bin\mysqld.exe (mysqld 8.0.32) initializing of server in progress as process 1396
2023-03-08T04:40:19.144066Z 0 [ERROR] [MY-010187] [Server] Could not open file 'F:\Software\MySQL\mysql-8.0.32-winx64\Logs\Error.log' for error logging: Permission denied
2023-03-08T04:40:19.146556Z 0 [ERROR] [MY-013455] [Server] The newly created data directory F:\Software\MySQL\mysql-8.0.32-winx64\Data\ by --initialize is unusable. You can remove it.
2023-03-08T04:40:19.146717Z 0 [ERROR] [MY-010119] [Server] Aborting
2023-03-08T04:40:19.147438Z 0 [System] [MY-010910] [Server] F:\Software\MySQL\mysql-8.0.32-winx64\bin\mysqld.exe: Shutdown complete (mysqld 8.0.32)  MySQL Community Server - GPL.

F:\Software\MySQL\mysql-8.0.32-winx64\bin>

```

![image-20230308124743539](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308124743539.png)

![image-20230308124821424](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308124821424.png)

how to deal with this problem [Server] Could not open file 'F:\Software\MySQL\mysql-8.0.32-winx64\Logs\Error.log' for error logging: Permission denied

The error message you're seeing suggests that the MySQL server process does not have the necessary permissions to write to the `Error.log` file. Here are a few steps you can take to try and resolve the issue:

1. ==**Check file permissions**==: Verify that the user running the MySQL server process has the necessary permissions to write to the `Error.log` file. You can check this by right-clicking on the file, selecting ==Properties==, and then looking at the Security tab. Make sure that the user running the MySQL server process has the "Write" permission enabled.
2. ==**Restart MySQL service**==: Try restarting the MySQL service. Sometimes, a service restart can help clear up any permissions-related issues that may be causing problems.
3. Run MySQL service with administrator privileges: Try running the MySQL service with administrator privileges. To do this, right-click on the MySQL service in the Services control panel, select Properties, and then go to the Log On tab. Select "This account" and enter the credentials of an account with administrator privileges.
4. Check antivirus software: Sometimes, antivirus software can interfere with file access permissions. Check to see if your antivirus software is blocking MySQL from accessing the `Error.log` file. You may need to configure your antivirus software to allow MySQL to access the file.
5. ==**Use a different log file location**==: If none of the above steps work, you could try changing the location of the `Error.log` file to a location where the MySQL server process has the necessary permissions to write. You can do this by modifying the `log-error` option in the MySQL configuration file.

一些讲师在讲一些命令执行的时候并不会说明某条命令的作用是什么





F:\Software\MySQL\mysql-8.0.32-winx64\bin>



> 没必要装在本地，直接装在docker 里面



win 命令行修改 文件夹读写权限

How to change folder read/write permissions on windows using command line

To change the folder read/write permissions on Windows using the command line, follow these steps:

1. Open the command prompt as an administrator by pressing the Windows key + X and selecting "Command Prompt (Admin)" from the menu.
2. Navigate to the folder whose permissions you want to change using the "cd" command.
3. To view the current permissions of the folder, use the following command:

```php
icacls <folder name>
```

4. To grant write permission to a user or group, use the following command:

```
icacls <folder name> /grant <user or group name>:W
```

For example, to grant write permission to the "Administrators" group, use the following command:

```
icacls C:\folder /grant Administrators:W
```

5. To grant read permission to a user or group, use the following command:

```
icacls <folder name> /grant <user or group name>:R
```

For example, to grant read permission to the "Users" group, use the following command:

```
icacls C:\folder /grant Users:R
```

For example, to revoke permissions from the "Guest" user, use the following command:

```
icacls C:\folder /remove Guest
```

Note: Replace "<folder name>", "<user or group name>" and "C:\folder" with the actual name and path of the folder and the user or group you want to grant or revoke permissions to.





```makefile
PS F:\Software\MySQL\mysql-8.0.32-winx64> cd ../
PS F:\Software\MySQL> icacls mysql-8.0.32-winx64
mysql-8.0.32-winx64 BUILTIN\Administrators:(I)(F)
                    BUILTIN\Administrators:(I)(OI)(CI)(IO)(F)
                    NT AUTHORITY\SYSTEM:(I)(F)
                    NT AUTHORITY\SYSTEM:(I)(OI)(CI)(IO)(F)
                    NT AUTHORITY\Authenticated Users:(I)(M)
                    NT AUTHORITY\Authenticated Users:(I)(OI)(CI)(IO)(M)
                    BUILTIN\Users:(I)(RX)
                    BUILTIN\Users:(I)(OI)(CI)(IO)(GR,GE)

Successfully processed 1 files; Failed processing 0 files
```



![image-20230308141052840](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308141052840.png)

权限啥的都没问题了



Open all permissions for a folder using command line in windows

To open all permissions for a folder in Windows using the command line, you can use the `icacls` command. Here's an example command that grants full control to all users:

```
icacls "C:\path\to\folder" /grant:r "Users:(OI)(CI)F"
```

Here's what each part of the command means:

- `icacls`: This is the command for modifying the security settings of files and folders using the command line.
- `"C:\path\to\folder"`: This is the path to the folder that you want to modify. Replace this with the actual path to your folder.
- `/grant:r`: This is the command that grants permissions. The `:r` switch replaces any existing permissions with the new ones.
- `"Users:(OI)(CI)F"`: This is the permission that you want to grant. In this case, you're granting full control (`F`) to all users (`Users`). The `(OI)` and `(CI)` flags indicate that the permission applies to both the folder itself (`OI`) and its contents (`CI`).

After running this command, all users will have full control over the specified folder and its contents. Note that you'll need to run this command as an administrator.



https://www.runoob.com/mysql/mysql-install.html

```makefile
[client]
# 设置mysql客户端默认字符集
default-character-set=utf8
 
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=C:\\web\\mysql-8.0.11
# 设置 mysql数据库的数据的存放目录，MySQL 8+ 不需要以下配置，系统自己生成即可，否则有可能报错
# datadir=C:\\web\\sqldata
# 允许最大连接数
max_connections=20
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
```

> 参照这个注释掉了在ini文件中的相关目录





```mkfile
C:\WINDOWS\system32>net start mysql
The MySQL service is starting.
The MySQL service was started successfully.


C:\WINDOWS\system32>mysql
ERROR 2003 (HY000): Can't connect to MySQL server on 'localhost:3306' (10061)
```

好奇怪



![image-20230308142735892](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308142735892.png)

> 应该是之前的一个服务 
>
> 没有删除干净
>
> 因为这里这个服务重新打开之后会自动停掉



![image-20230308143253844](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308143253844.png)

> 为什么命令行显示的服务信息和UI界面显示的信息完全不同

![image-20230308144200629](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308144200629.png)

![image-20230308144410541](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308144410541.png)

为啥打开之后立马就关掉了



I didn't delete mysql software completely when I deleted it before, in this case how to delete myql service in the command line of win



If you want to remove MySQL service from the command line on Windows, you can use the `sc` (Service Control) command. Here are the steps to remove the MySQL service:

1. Open the command prompt with administrator privileges.
2. Type the following command to see a list of all installed services:

```graphql
sc query
```

3. Find the MySQL service in the list, and note down its service name. The service name should be something like `mysql` or `mysql56`.

4. Type the following command to stop the MySQL service:

```vbnet
sc stop service_name
```

Replace `service_name` with the actual service name you noted down in the previous step.

5. Type the following command to delete the MySQL service:

```
sc delete service_name
```

Again, replace `service_name` with the actual service name.

6. Verify that the service has been removed by typing the `sc query` command again and checking if the MySQL service is no longer listed.

Note that deleting the MySQL service does not delete the MySQL software itself. You will need to uninstall the MySQL software separately if you want to completely remove it from your system.





Why after opening a service in windows system, the service immediately stopped automatically, how to solve this problem?

There could be several reasons why a Windows service stops immediately after starting. Here are some possible causes and solutions:

1. Dependencies: Some services require other services to be running before they can start. If these dependencies are not met, the service may stop immediately. Make sure that all the required services are running before starting the problematic service.
2. Permissions: The service may be configured to run under a specific user account that does not have the necessary permissions to start. Check the service properties and make sure that the account has the appropriate permissions.
3. Error in service code: There may be an error in the service code that is causing it to stop. Check the event logs for any error messages related to the service and try to fix the underlying problem.
4. Conflicting services: There may be another service running on the system that is conflicting with the problematic service. Try stopping all other services and see if the problematic service starts correctly.
5. Corrupted system files: If the service is critical to the operating system, there may be corrupted system files that are preventing it from starting. Try running a system file checker (SFC) scan to repair any damaged files.
6. Antivirus or firewall: It is possible that an antivirus or firewall is blocking the service from starting. Temporarily disable any antivirus or firewall software and see if the service starts correctly.
7. Restarting the system: Sometimes simply restarting the system can resolve the issue.

If none of the above solutions work, you may need to consult with a Windows system administrator or seek professional technical support.





![image-20230308145334293](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308145334293.png)

> 没有发生端口占用



Show process information on windows using command line

To show process information on Windows using the command line, you can use the following commands:

1. Tasklist command: The `tasklist` command is used to display a list of all running processes and their details such as process ID, memory usage, and process name.

Syntax: `tasklist`

Example:

```
C:\>tasklist

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
System Idle Process              0 Services                   0         24 K
System                           4 Services                   0      1,428 K
smss.exe                       308 Services                   0      1,056 K
```

2. Task Manager: You can also use the Task Manager utility to view process information. To open Task Manager, press `Ctrl+Shift+Esc` or right-click on the taskbar and select `Task Manager`.

In Task Manager, you can see the list of running processes, CPU usage, memory usage, and other details.

3. PowerShell command: You can also use the PowerShell command `Get-Process` to get a list of running processes and their details.

Syntax: `Get-Process`

Example:

```
PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    586      52     9372      16628       0.34   3392   1 ApplicationFrameHost
    569      31     4732      11816       0.09   2176   1 audiodg
    214      10     3128      10308       0.03   3792   1 conhost
```

These are some of the ways to show process information on Windows using the command line.



![image-20230308151249445](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308151249445.png)

> 难道是之前没有这个版本python?

![image-20230308151321669](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308151321669.png)

![image-20230308151419078](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308151419078.png)

![image-20230308151610786](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308151610786.png)

![image-20230308151855926](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308151855926.png)

![image-20230308152018576](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308152018576.png)

```
Action 15:14:56: INSTALL. 
1: MySQL Server 8.0 2: {11CF35A6-DF56-426A-8FEF-BAA039D8FF31} 
Action 15:14:56: FindRelatedProducts. Searching for related applications
Action 15:14:56: AppSearch. Searching for installed applications
Action 15:14:56: LaunchConditions. Evaluating launch conditions
Action 15:14:56: ValidateProductID. 
Action 15:14:56: CostInitialize. Computing space requirements
Action 15:14:56: FileCost. Computing space requirements
Action 15:14:56: CostFinalize. Computing space requirements
Action 15:14:56: MigrateFeatureStates. Migrating feature states from related applications
Action 15:14:56: InstallValidate. Validating install
Min: 0 Max: 3933
Position: 25
Position: 50
Position: 75
Position: 100
Position: 125
Position: 150
Position: 175
Position: 200
Position: 225
Position: 250
Position: 275
Position: 300
Position: 325
Position: 350
Position: 375
Position: 400
Position: 425
Position: 450
Position: 475
Position: 500
Position: 525
Position: 550
Position: 575
Position: 600
Position: 625
Position: 650
Position: 675
Position: 700
Position: 725
Position: 750
Position: 775
Position: 800
Position: 825
Position: 850
Position: 875
Position: 900
Position: 925
Position: 950
Position: 975
Position: 1000
Position: 1025
Position: 1050
Position: 1075
Position: 1100
Position: 1125
Position: 1150
Position: 1175
Position: 1200
Position: 1225
Position: 1250
Position: 1275
Position: 1300
Position: 1325
Position: 1350
Position: 1375
Position: 1400
Position: 1425
Position: 1450
Position: 1475
Position: 1500
Position: 1525
Position: 1550
Position: 1575
Position: 1600
Position: 1625
Position: 1650
Position: 1675
Position: 1700
Position: 1725
Position: 1750
Position: 1775
Position: 1800
Position: 1825
Position: 1850
Position: 1875
Position: 1900
Position: 1925
Position: 1950
Position: 1975
Position: 2000
Position: 2025
Position: 2050
Position: 2075
Position: 2100
Position: 2125
Position: 2150
Position: 2175
Position: 2200
Position: 2225
Position: 2250
Position: 2275
Position: 2300
Position: 2325
Position: 2350
Position: 2375
Position: 2400
Position: 2425
Position: 2450
Position: 2475
Position: 2500
Position: 2525
Position: 2550
Position: 2575
Position: 2600
Position: 2625
Position: 2650
Position: 2675
Position: 2700
Position: 2725
Position: 2750
Position: 2775
Position: 2800
Position: 2825
Position: 2850
Position: 2875
Position: 2900
Position: 2925
Position: 2950
Position: 2975
Position: 3000
Position: 3025
Position: 3050
Position: 3075
Position: 3100
Position: 3125
Position: 3150
Position: 3175
Position: 3175
Position: 3175
Action 15:14:57: SaveTargetDir. 
Action 15:14:57: InstallInitialize. 
Action 15:14:57: RemoveExistingProducts. Removing applications
Action 15:14:57: ProcessComponents. Updating component registration
Position: 3175
Action 15:14:57: GenerateScript. Generating script operations for action:
Position: 3176
Position: 3177
Updating component registration
DoStep
Position: 3178
Position: 3179
Position: 3180
Position: 3181
Position: 3182
Position: 3183
Position: 3184
Position: 3185
Position: 3186
Position: 3187
Position: 3188
Position: 3189
Position: 3190
Position: 3191
Position: 3192
Position: 3193
Position: 3194
Position: 3195
Position: 3196
Position: 3197
Position: 3198
Position: 3199
Position: 3200
Position: 3201
Position: 3202
Position: 3203
Position: 3204
Position: 3205
Position: 3206
Position: 3207
Position: 3208
Position: 3209
Position: 3210
Position: 3211
Position: 3212
Position: 3213
Position: 3214
Position: 3215
Position: 3216
Position: 3217
Position: 3218
Position: 3219
Position: 3220
Position: 3221
Position: 3222
Position: 3223
Position: 3224
Position: 3225
Position: 3226
Position: 3227
Position: 3228
Position: 3229
Position: 3230
Position: 3231
Position: 3232
Position: 3233
Position: 3234
Position: 3235
Position: 3236
Position: 3237
Position: 3238
Position: 3239
Position: 3240
Position: 3241
Position: 3242
Position: 3243
Position: 3244
Position: 3245
Position: 3246
Position: 3247
Position: 3248
Position: 3249
Position: 3250
Position: 3251
Position: 3252
Position: 3253
Position: 3254
Position: 3255
Position: 3256
Position: 3257
Position: 3258
Position: 3259
Position: 3260
Position: 3261
Position: 3262
Position: 3263
Position: 3264
Position: 3265
Position: 3266
Position: 3267
Position: 3268
Position: 3269
Position: 3270
Position: 3271
Position: 3272
Position: 3273
Position: 3274
Position: 3275
Position: 3276
Position: 3277
Position: 3278
Position: 3279
Position: 3280
Position: 3281
Position: 3282
Position: 3283
Position: 3284
Position: 3285
Position: 3286
Position: 3287
Position: 3288
Position: 3289
Position: 3290
Position: 3291
Position: 3292
Position: 3293
Position: 3294
Position: 3295
Position: 3296
Position: 3297
Position: 3298
Position: 3299
Position: 3300
Position: 3301
Position: 3302
Position: 3303
Position: 3304
Position: 3305
Position: 3306
Position: 3307
Position: 3308
Action 15:14:58: UnpublishFeatures. Unpublishing Product Features
Action 15:14:58: SchedSecureObjectsRollback. 
Action 15:14:59: RemoveRegistryValues. Removing system registry values
Action 15:14:59: RemoveShortcuts. Removing shortcuts
Action 15:14:59: RemoveFiles. Removing files
Action 15:14:59: RemoveFolders. Removing folders
Action 15:14:59: CreateFolders. Creating folders
Folder: Creating folders
DoStep
Position: 3309
Position: 3310
Position: 3311
Position: 3312
Position: 3313
Position: 3314
Action 15:14:59: InstallFiles. Copying new files
File: Copying new files,  Directory: ,  Size: 
DoStep
Position: 3315
Position: 3316
Position: 3317
Position: 3318
Position: 3319
Position: 3320
Position: 3321
Position: 3322
Position: 3323
Position: 3324
Position: 3325
Position: 3326
Position: 3327
Position: 3328
Position: 3329
Position: 3330
Position: 3331
Position: 3332
Position: 3333
Position: 3334
Position: 3335
Position: 3336
Position: 3337
Position: 3338
Position: 3339
Position: 3340
Position: 3341
Position: 3342
Position: 3343
Position: 3344
Position: 3345
Position: 3346
Position: 3347
Position: 3348
Position: 3349
Position: 3350
Position: 3351
Position: 3352
Position: 3353
Position: 3354
Position: 3355
Position: 3356
Position: 3357
Position: 3358
Position: 3359
Position: 3360
Position: 3361
Position: 3362
Position: 3363
Position: 3364
Position: 3365
Position: 3366
Position: 3367
Position: 3368
Position: 3369
Position: 3370
Position: 3371
Position: 3372
Position: 3373
Position: 3374
Position: 3375
Position: 3376
Position: 3377
Position: 3378
Position: 3379
Position: 3380
Position: 3381
Position: 3382
Position: 3383
Position: 3384
Position: 3385
Position: 3386
Position: 3387
Position: 3388
Position: 3389
Position: 3390
Position: 3391
Position: 3392
Position: 3393
Position: 3394
Position: 3395
Position: 3396
Position: 3397
Position: 3398
Position: 3399
Position: 3400
Position: 3401
Position: 3402
Position: 3403
Position: 3404
Position: 3405
Position: 3406
Position: 3407
Position: 3408
Position: 3409
Position: 3410
Position: 3411
Position: 3412
Position: 3413
Position: 3414
Position: 3415
Position: 3416
Position: 3417
Position: 3418
Position: 3419
Position: 3420
Position: 3421
Position: 3422
Position: 3423
Position: 3424
Position: 3425
Position: 3426
Position: 3427
Position: 3428
Position: 3429
Position: 3430
Position: 3431
Position: 3432
Position: 3433
Position: 3434
Position: 3435
Position: 3436
Position: 3437
Position: 3438
Position: 3439
Position: 3440
Position: 3441
Position: 3442
Position: 3443
Position: 3444
Position: 3445
Position: 3446
Position: 3447
Position: 3448
Position: 3449
Position: 3450
Position: 3451
Position: 3452
Position: 3453
Position: 3454
Position: 3455
Position: 3456
Position: 3457
Position: 3458
Position: 3459
Position: 3460
Position: 3461
Position: 3462
Position: 3463
Position: 3464
Position: 3465
Position: 3466
Position: 3467
Position: 3468
Position: 3469
Position: 3470
Position: 3471
Position: 3472
Position: 3473
Position: 3474
Position: 3475
Position: 3476
Position: 3477
Position: 3478
Position: 3479
Position: 3480
Position: 3481
Position: 3482
Position: 3483
Position: 3484
Position: 3485
Position: 3486
Position: 3487
Position: 3488
Position: 3489
Position: 3490
Position: 3491
Position: 3492
Position: 3493
Position: 3494
Position: 3495
Position: 3496
Position: 3497
Position: 3498
Position: 3499
Position: 3500
Position: 3501
Position: 3502
Position: 3503
Position: 3504
Position: 3505
Position: 3506
Position: 3507
Position: 3508
Position: 3509
Position: 3510
Position: 3511
Position: 3512
Position: 3513
Position: 3514
Position: 3515
Position: 3516
Position: 3517
Position: 3518
Position: 3519
Position: 3520
Position: 3521
Position: 3522
Position: 3523
Position: 3524
Position: 3525
Position: 3526
Position: 3527
Position: 3528
Position: 3529
Position: 3530
Position: 3531
Position: 3532
Position: 3533
Position: 3534
Position: 3535
Position: 3536
Position: 3537
Position: 3538
Position: 3539
Position: 3540
Position: 3541
Position: 3542
Position: 3543
Position: 3544
Position: 3545
Position: 3546
Position: 3547
Position: 3548
Position: 3549
Position: 3550
Position: 3551
Position: 3552
Position: 3553
Position: 3554
Position: 3555
Position: 3556
Position: 3557
Position: 3558
Position: 3559
Position: 3560
Position: 3561
Position: 3562
Position: 3563
Position: 3564
Position: 3565
Position: 3566
Position: 3567
Position: 3568
Position: 3569
Position: 3570
Position: 3571
Position: 3572
Position: 3573
Position: 3574
Position: 3575
Position: 3576
Position: 3577
Position: 3578
Position: 3579
Position: 3580
Position: 3581
Position: 3582
Position: 3583
Position: 3584
Position: 3585
Position: 3586
Position: 3587
Position: 3588
Position: 3589
Position: 3590
Position: 3591
Position: 3592
Position: 3593
Position: 3594
Position: 3595
Position: 3596
Position: 3597
Position: 3598
Position: 3599
Action 15:15:01: RunPostInstallProperty. 
Action 15:15:01: RunPostInstall. 

DoStep
Position: 3600
Position: 3601
Action 15:15:01: CreateShortcuts. Creating shortcuts
Shortcut: Creating shortcuts
DoStep
Position: 3602
Position: 3603
Position: 3604
Position: 3605
Position: 3606
Position: 3607
Action 15:15:01: WriteRegistryValues. Writing system registry values
Key: Writing system registry values, Name: , Value: 
DoStep
Position: 3608
Position: 3609
Position: 3610
Position: 3611
Position: 3612
Position: 3613
Position: 3614
Position: 3615
Position: 3616
Position: 3617
Position: 3618
Position: 3619
Position: 3620
Action 15:15:01: InstallServices. Installing new services
Action 15:15:01: SchedSecureObjects. 
Action 15:15:01: ExecSecureObjects. 

DoStep
Position: 3621
Position: 3622
Action 15:15:01: RegisterUser. Registering user
Action 15:15:01: RegisterProduct. Registering product
Registering product
DoStep
Position: 3623
Position: 3624
Position: 3625
Position: 3626
Position: 3627
Action 15:15:02: PublishFeatures. Publishing Product Features
Feature: Publishing Product Features
DoStep
Position: 3628
Position: 3629
Position: 3630
Position: 3631
Position: 3632
Position: 3633
Position: 3634
Position: 3635
Position: 3636
Position: 3637
Position: 3638
Position: 3639
Position: 3640
Action 15:15:02: PublishProduct. Publishing product information
Position: 3641
Position: 3642
Position: 3643
Position: 3644
Position: 3645
Position: 3646
Position: 3647
Position: 3648
Action 15:15:02: InstallFinalize. 
Min: 0 Max: 520374709
Position: 520374709
Action 15:15:02: ProcessComponents. Updating component registration
Step: 24000
Position: 0
Step: 24000
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Position: 0
Action 15:15:03: CreateFolders. Creating folders
Folder: C:\ProgramData\MySQL\MySQL Server 8.0\
DoStep
Folder: C:\ProgramData\MySQL\MySQL Server 8.0\data\
DoStep
Folder: C:\ProgramData\MySQL\MySQL Server 8.0\data\mysql\
DoStep
Folder: C:\ProgramData\MySQL\MySQL Server 8.0\data\performance_schema\
DoStep
Folder: C:\ProgramData\MySQL\MySQL Server 8.0\data\test\
DoStep
Action 15:15:03: InstallFiles. Copying new files
File: ibd2sdi.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5096448
Position: 5096448
File: innochecksum.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5059584
Position: 10156032
File: libeay32.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 1672192
Position: 11828224
File: libmecab.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 1839616
Position: 13667840
File: lz4_decompress.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 4946432
Position: 18614272
File: my_print_defaults.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 4955136
Position: 23569408
File: myisam_ftdump.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5221376
Position: 28790784
File: myisamchk.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5328896
Position: 34119680
File: myisamlog.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5178368
Position: 39298048
File: myisampack.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5240832
Position: 44538880
File: mysql.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5290496
Position: 49829376
File: mysql_config.pl,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 7392
Position: 49836768
File: mysql_config_editor.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 4972544
Position: 54809312
File: mysql_secure_installation.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5178880
Position: 59988192
File: mysql_ssl_rsa_setup.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5004288
Position: 64992480
File: mysql_tzinfo_to_sql.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 4900864
Position: 69893344
File: mysql_upgrade.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 10997248
Position: 80890592
File: mysqladmin.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5186560
Position: 86077152
File: mysqlbinlog.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5475840
Position: 91552992
File: mysqlcheck.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5198848
Position: 96751840
File: mysqld.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 44932096
Position: 141683936
File: mysqld_multi.pl,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 28045
Position: 141711981
File: mysqldump.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5259264
Position: 146971245
File: mysqldumpslow.pl,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 8071
Position: 146979316
File: mysqlimport.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5179904
Position: 152159220
File: mysqlpump.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5663744
Position: 157822964
File: mysqlshow.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5178368
Position: 163001332
File: mysqlslap.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5196288
Position: 168197620
File: mysqlxtest.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 7355392
Position: 175553012
File: perror.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 5590528
Position: 181143540
File: resolveip.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 4953600
Position: 186097140
File: ssleay32.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 355840
Position: 186452980
File: zlib_decompress.exe,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\bin\,  Size: 4920832
Position: 191373812
File: binary_log_types.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 2886
Position: 191376698
File: errmsg.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 5294
Position: 191381992
File: my_command.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 4385
Position: 191386377
File: my_list.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 2603
Position: 191388980
File: mysql.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 31305
Position: 191420285
File: client_plugin.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\mysql\,  Size: 7295
Position: 191427580
File: mysql_com.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 34068
Position: 191461648
File: plugin_auth_common.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\mysql\,  Size: 5546
Position: 191467194
File: mysql_time.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 2996
Position: 191470190
File: udf_registration_types.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\mysql\,  Size: 3848
Position: 191474038
File: mysql_version.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 1054
Position: 191475092
File: mysqld_error.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 192670
Position: 191667762
File: mysqlx_ername.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 4745
Position: 191672507
File: mysqlx_error.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 2954
Position: 191675461
File: mysqlx_version.h,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\,  Size: 1861
Position: 191677322
File: applink.c,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\include\openssl\,  Size: 3176
Position: 191680498
File: libmysql.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\,  Size: 5164032
Position: 196844530
File: libmysql.lib,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\,  Size: 27066
Position: 196871596
File: char.bin,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_euc-jp\,  Size: 262496
Position: 197134092
File: dicrc,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_euc-jp\,  Size: 693
Position: 197134785
File: left-id.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_euc-jp\,  Size: 55910
Position: 197190695
File: matrix.bin,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_euc-jp\,  Size: 3463716
Position: 200654411
File: pos-id.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_euc-jp\,  Size: 1477
Position: 200655888
File: rewrite.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_euc-jp\,  Size: 6241
Position: 200662129
File: right-id.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_euc-jp\,  Size: 55910
Position: 200718039
File: sys.dic,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_euc-jp\,  Size: 37779919
Position: 238497958
File: unk.dic,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_euc-jp\,  Size: 5409
Position: 238503367
File: char.bin,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_sjis\,  Size: 262496
Position: 238765863
File: dicrc,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_sjis\,  Size: 693
Position: 238766556
File: left-id.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_sjis\,  Size: 55910
Position: 238822466
File: matrix.bin,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_sjis\,  Size: 3463716
Position: 242286182
File: pos-id.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_sjis\,  Size: 1477
Position: 242287659
File: rewrite.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_sjis\,  Size: 6241
Position: 242293900
File: right-id.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_sjis\,  Size: 55910
Position: 242349810
File: sys.dic,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_sjis\,  Size: 37635899
Position: 279985709
File: unk.dic,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_sjis\,  Size: 5409
Position: 279991118
File: char.bin,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_utf-8\,  Size: 262496
Position: 280253614
File: dicrc,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_utf-8\,  Size: 693
Position: 280254307
File: left-id.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_utf-8\,  Size: 55910
Position: 280310217
File: matrix.bin,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_utf-8\,  Size: 3463716
Position: 283773933
File: pos-id.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_utf-8\,  Size: 1477
Position: 283775410
File: rewrite.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_utf-8\,  Size: 6241
Position: 283781651
File: right-id.def,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_utf-8\,  Size: 55910
Position: 283837561
File: sys.dic,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_utf-8\,  Size: 49199027
Position: 333036588
File: unk.dic,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\dic\ipadic_utf-8\,  Size: 5690
Position: 333042278
File: mecabrc,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\mecab\etc\,  Size: 1403
Position: 333043681
File: mysqlclient.lib,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\,  Size: 61584560
Position: 394628241
File: adt_null.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 24064
Position: 394652305
File: component_log_filter_dragnet.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 31744
Position: 394684049
File: component_log_sink_json.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 16384
Position: 394700433
File: component_log_sink_syseventlog.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 15360
Position: 394715793
File: component_log_sink_test.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 30720
Position: 394746513
File: component_validate_password.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 65536
Position: 394812049
File: connection_control.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 47104
Position: 394859153
File: group_replication.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 1059840
Position: 395918993
File: ha_example.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 28160
Position: 395947153
File: keyring_file.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 108544
Position: 396055697
File: keyring_udf.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 25088
Position: 396080785
File: libpluginmecab.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 30720
Position: 396111505
File: libtest_framework.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 11776
Position: 396123281
File: libtest_services.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 19456
Position: 396142737
File: libtest_services_threaded.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 20480
Position: 396163217
File: libtest_session_attach.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 49152
Position: 396212369
File: libtest_session_detach.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 32256
Position: 396244625
File: libtest_session_in_thd.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 22528
Position: 396267153
File: libtest_session_info.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 50176
Position: 396317329
File: libtest_sql_2_sessions.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 34816
Position: 396352145
File: libtest_sql_all_col_types.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 37888
Position: 396390033
File: libtest_sql_cmds_1.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 37888
Position: 396427921
File: libtest_sql_commit.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 39424
Position: 396467345
File: libtest_sql_complex.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 41472
Position: 396508817
File: libtest_sql_errors.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 36864
Position: 396545681
File: libtest_sql_lock.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 45568
Position: 396591249
File: libtest_sql_processlist.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 34816
Position: 396626065
File: libtest_sql_replication.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 38400
Position: 396664465
File: libtest_sql_shutdown.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 29696
Position: 396694161
File: libtest_sql_sqlmode.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 39424
Position: 396733585
File: libtest_sql_stmt.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 65024
Position: 396798609
File: libtest_sql_stored_procedures_functions.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 38912
Position: 396837521
File: libtest_sql_views_triggers.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 38912
Position: 396876433
File: libtest_x_sessions_deinit.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 22016
Position: 396898449
File: libtest_x_sessions_init.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 27136
Position: 396925585
File: locking_service.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 13312
Position: 396938897
File: mypluglib.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 13312
Position: 396952209
File: mysql_no_login.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 12288
Position: 396964497
File: rewrite_example.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 13312
Position: 396977809
File: rewriter.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 65536
Position: 397043345
File: semisync_master.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 75776
Position: 397119121
File: semisync_slave.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 29696
Position: 397148817
File: test_security_context.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 12800
Position: 397161617
File: test_services_plugin_registry.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 23040
Position: 397184657
File: test_udf_services.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 14848
Position: 397199505
File: validate_password.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 53760
Position: 397253265
File: version_token.dll,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\lib\plugin\,  Size: 62976
Position: 397316241
File: LICENSE,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\,  Size: 301518
Position: 397617759
File: README,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\,  Size: 687
Position: 397618446
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\bulgarian\,  Size: 257216
Position: 397875662
File: armscii8.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5939
Position: 397881601
File: ascii.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5925
Position: 397887526
File: cp1250.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 8654
Position: 397896180
File: cp1251.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 8783
Position: 397904963
File: cp1256.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5982
Position: 397910945
File: cp1257.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 9315
Position: 397920260
File: cp850.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5919
Position: 397926179
File: cp852.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5941
Position: 397932120
File: cp866.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 6026
Position: 397938146
File: dec8.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 6942
Position: 397945088
File: geostd8.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5929
Position: 397951017
File: greek.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 6141
Position: 397957158
File: hebrew.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5930
Position: 397963088
File: hp8.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5915
Position: 397969003
File: Index.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 19495
Position: 397988498
File: keybcs2.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5942
Position: 397994440
File: koi8r.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5923
Position: 398000363
File: koi8u.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 6945
Position: 398007308
File: latin1.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 10229
Position: 398017537
File: latin2.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 7651
Position: 398025188
File: latin5.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 5928
Position: 398031116
File: latin7.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 7851
Position: 398038967
File: macce.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 8460
Position: 398047427
File: macroman.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 8471
Position: 398055898
File: README,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 1749
Position: 398057647
File: swe7.xml,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\charsets\,  Size: 6943
Position: 398064590
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\czech\,  Size: 257722
Position: 398322312
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\danish\,  Size: 257722
Position: 398580034
File: dictionary.txt,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\,  Size: 25575
Position: 398605609
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\dutch\,  Size: 258742
Position: 398864351
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\english\,  Size: 256963
Position: 399121314
File: errmsg-utf8.txt,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\,  Size: 824111
Position: 399945425
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\estonian\,  Size: 257227
Position: 400202652
File: fill_help_tables.sql,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\,  Size: 1023732
Position: 401226384
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\french\,  Size: 258370
Position: 401484754
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\german\,  Size: 264657
Position: 401749411
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\greek\,  Size: 263754
Position: 402013165
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\hungarian\,  Size: 257604
Position: 402270769
File: innodb_memcached_config.sql,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\,  Size: 3999
Position: 402274768
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\italian\,  Size: 258733
Position: 402533501
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\japanese\,  Size: 264409
Position: 402797910
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\korean\,  Size: 260003
Position: 403057913
File: mysql_sys_schema.sql,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\,  Size: 289693
Position: 403347606
File: mysql_system_tables.sql,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\,  Size: 109850
Position: 403457456
File: mysql_system_tables_data.sql,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\,  Size: 5461196
Position: 408918652
File: mysql_test_data_timezone.sql,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\,  Size: 10830
Position: 408929482
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\norwegian\,  Size: 257033
Position: 409186515
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\norwegian-ny\,  Size: 257086
Position: 409443601
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\polish\,  Size: 257892
Position: 409701493
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\portuguese\,  Size: 259923
Position: 409961416
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\romanian\,  Size: 258675
Position: 410220091
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\russian\,  Size: 272301
Position: 410492392
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\serbian\,  Size: 259344
Position: 410751736
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\slovak\,  Size: 257489
Position: 411009225
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\spanish\,  Size: 258617
Position: 411267842
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\swedish\,  Size: 257816
Position: 411525658
File: errmsg.sys,  Directory: C:\Program Files\MySQL\MySQL Server 8.0\share\ukrainian\,  Size: 266875
Position: 411792533
Action 15:15:09: RunPostInstall. 
Action 15:15:09: CreateShortcuts. Creating shortcuts
Shortcut: icon.ico
DoStep
Shortcut: Icon.MysqlCmdShell
DoStep
Shortcut: rpxm3ds_|MySQL 8.0 Command Line Client
DoStep
Shortcut: 7ejegqmo|MySQL 8.0 Command Line Client - Unicode
DoStep
Action 15:15:10: WriteRegistryValues. Writing system registry values
Step: 13200
Position: 411792533
Key: \SOFTWARE\MySQL AB\MySQL Server 8.0, Name: Location, Value: C:\Program Files\MySQL\MySQL Server 8.0\
DoStep
Position: 411792533
Key: \SOFTWARE\MySQL AB\MySQL Server 8.0, Name: Version, Value: 8.0.11
DoStep
Position: 411792533
Key: \SOFTWARE\MySQL AB\MySQL Server 8.0, Name: DataLocation, Value: C:\ProgramData\MySQL\MySQL Server 8.0\
DoStep
Position: 411792533
Key: \SOFTWARE\MySQL AB\MySQL Server 8.0, Name: , Value: 
DoStep
Position: 411792533
Key: \Console\MySQL 8.0 Command Line Client - Unicode, Name: FaceName, Value: Lucida Console
DoStep
Position: 411792533
Key: \Console\MySQL 8.0 Command Line Client - Unicode, Name: FontWeight, Value: #400
DoStep
Position: 411792533
Key: \Console\MySQL 8.0 Command Line Client - Unicode, Name: , Value: 
DoStep
Position: 411792533
Key: \Software\MySQL AB\MySQL Server 8.0, Name: installed, Value: #1
DoStep
Action 15:15:10: ExecSecureObjects. 
Position: 411793533
Position: 411794533
Position: 411795533
Position: 411796533
Action 15:15:10: RegisterProduct. Registering product
Position: 517293109
{11CF35A6-DF56-426A-8FEF-BAA039D8FF31}
DoStep
Action 15:15:10: PublishFeatures. Publishing Product Features
Feature: RegKeys
DoStep
Feature: Client
DoStep
Feature: MYSQLSERVER
DoStep
Feature: SharedLibraries
DoStep
Feature: DEVEL
DoStep
Feature: Readme
DoStep
Feature: ALWAYSINSTALL
DoStep
Feature: Server_Scripts
DoStep
Feature: MISC
DoStep
Feature: ProgramMenu
DoStep
Feature: UserEditableDataFiles
DoStep
Feature: DOCUMENTATION
DoStep
Action 15:15:10: PublishProduct. Publishing product information
Action 15:15:11: RollbackCleanup. Removing backup files
1: MySQL Server 8.0 2: {11CF35A6-DF56-426A-8FEF-BAA039D8FF31} 3: 1 
Action 15:15:12: INSTALL. 
1: MySQL Documents 8.0 2: {20B3A2F7-90F4-4EA9-8F82-5033C405A8EF} 
Action 15:15:12: FindRelatedProducts. Searching for related applications
Action 15:15:12: ValidateProductID. 
Action 15:15:12: CostInitialize. Computing space requirements
Action 15:15:12: FileCost. Computing space requirements
Action 15:15:12: CostFinalize. Computing space requirements
Action 15:15:12: InstallValidate. Validating install
Min: 0 Max: 87
Position: 25
Position: 50
Position: 50
Position: 50
Action 15:15:12: InstallInitialize. 
Action 15:15:12: RemoveExistingProducts. Removing applications
Action 15:15:12: ProcessComponents. Updating component registration
Action 15:15:12: GenerateScript. Generating script operations for action:
Position: 51
Position: 52
Updating component registration
DoStep
Position: 53
Position: 54
Position: 55
Position: 56
Action 15:15:12: UnpublishFeatures. Unpublishing Product Features
Action 15:15:12: RemoveFiles. Removing files
Action 15:15:12: InstallFiles. Copying new files
File: Copying new files,  Directory: ,  Size: 
DoStep
Position: 57
Position: 58
Position: 59
Position: 60
Position: 61
Position: 62
Position: 63
Position: 64
Action 15:15:12: RegisterUser. Registering user
Action 15:15:12: RegisterProduct. Registering product
Registering product
DoStep
Position: 65
Position: 66
Position: 67
Position: 68
Position: 69
Action 15:15:13: PublishFeatures. Publishing Product Features
Feature: Publishing Product Features
DoStep
Position: 70
Position: 71
Position: 72
Action 15:15:13: PublishProduct. Publishing product information

DoStep
Position: 73
Position: 74
Position: 75
Position: 76
Position: 77
Position: 78
Position: 79
Position: 80
Action 15:15:13: InstallFinalize. 
Min: 0 Max: 116646827
Position: 116646827
Action 15:15:13: ProcessComponents. Updating component registration
Step: 24000
Position: 0
Position: 0
Action 15:15:13: InstallFiles. Copying new files
File: refman-8.0-en.pdf,  Directory: C:\Program Files (x86)\MySQL\MySQL Documentation 8.0\,  Size: 39496533
Position: 39496533
File: refman-8.0-en.a4.pdf,  Directory: C:\Program Files (x86)\MySQL\MySQL Documentation 8.0\,  Size: 39505110
Position: 79001643
Action 15:15:14: RegisterProduct. Registering product
Position: 116598827
{20B3A2F7-90F4-4EA9-8F82-5033C405A8EF}
DoStep
Action 15:15:15: PublishFeatures. Publishing Product Features
Feature: ServerA4Feature
DoStep
Feature: ServerFeature
DoStep
Action 15:15:15: PublishProduct. Publishing product information
Action 15:15:15: RollbackCleanup. Removing backup files
1: MySQL Documents 8.0 2: {20B3A2F7-90F4-4EA9-8F82-5033C405A8EF} 3: 1 
Action 15:15:15: INSTALL. 
1: MySQL Examples and Samples 8.0 2: {409E9607-1B91-4534-8381-1CD753D5530F} 
Action 15:15:15: FindRelatedProducts. Searching for related applications
Action 15:15:15: ValidateProductID. 
Action 15:15:15: CostInitialize. Computing space requirements
Action 15:15:15: FileCost. Computing space requirements
Action 15:15:15: CostFinalize. Computing space requirements
Action 15:15:15: InstallValidate. Validating install
Min: 0 Max: 205
Position: 25
Position: 50
Position: 75
Position: 100
Position: 125
Position: 150
Position: 150
Position: 150
Action 15:15:16: InstallInitialize. 
Action 15:15:16: RemoveExistingProducts. Removing applications
Action 15:15:16: ProcessComponents. Updating component registration
Position: 150
Action 15:15:16: GenerateScript. Generating script operations for action:
Position: 151
Position: 152
Updating component registration
DoStep
Position: 153
Position: 154
Position: 155
Position: 156
Action 15:15:16: UnpublishFeatures. Unpublishing Product Features
Action 15:15:16: RemoveRegistryValues. Removing system registry values
Action 15:15:16: RemoveFiles. Removing files
Action 15:15:16: InstallFiles. Copying new files
File: Copying new files,  Directory: ,  Size: 
DoStep
Position: 157
Position: 158
Position: 159
Position: 160
Position: 161
Position: 162
Position: 163
Position: 164
Position: 165
Position: 166
Position: 167
Position: 168
Action 15:15:16: WriteRegistryValues. Writing system registry values
Key: Writing system registry values, Name: , Value: 
DoStep
Position: 169
Position: 170
Position: 171
Position: 172
Position: 173
Position: 174
Position: 175
Action 15:15:16: RegisterUser. Registering user
Action 15:15:16: RegisterProduct. Registering product
Registering product
DoStep
Position: 176
Position: 177
Position: 178
Position: 179
Position: 180
Action 15:15:16: PublishFeatures. Publishing Product Features
Feature: Publishing Product Features
DoStep
Position: 181
Position: 182
Action 15:15:16: PublishProduct. Publishing product information

DoStep
Position: 183
Position: 184
Position: 185
Position: 186
Position: 187
Position: 188
Position: 189
Position: 190
Action 15:15:16: InstallFinalize. 
Min: 0 Max: 4821616
Position: 4821616
Action 15:15:16: ProcessComponents. Updating component registration
Step: 24000
Position: 0
Position: 0
Action 15:15:16: InstallFiles. Copying new files
File: sakila.mwb,  Directory: C:\Program Files (x86)\MySQL\Samples and Examples 8.0\Sample Databases\Sakila\,  Size: 50019
Position: 50019
File: sakila-data.sql,  Directory: C:\Program Files (x86)\MySQL\Samples and Examples 8.0\Sample Databases\Sakila\,  Size: 3398148
Position: 3448167
File: sakila-schema.sql,  Directory: C:\Program Files (x86)\MySQL\Samples and Examples 8.0\Sample Databases\Sakila\,  Size: 23353
Position: 3471520
File: world-schema.sql,  Directory: C:\Program Files (x86)\MySQL\Samples and Examples 8.0\Sample Databases\World\,  Size: 397328
Position: 3868848
Action 15:15:17: WriteRegistryValues. Writing system registry values
Step: 13200
Position: 3868848
Key: \Software\MySQL AB\MySQL Examples and Samples 8.0, Name: Location, Value: C:\Program Files (x86)\MySQL\Samples and Examples 8.0\
DoStep
Position: 3868848
Key: \Software\MySQL AB\MySQL Examples and Samples 8.0, Name: Sample Databases, Value: C:\Program Files (x86)\MySQL\Samples and Examples 8.0\Sample Databases\
DoStep
Position: 3868848
Key: \Software\MySQL AB\MySQL Examples and Samples 8.0, Name: , Value: 
DoStep
Position: 3868848
Key: \Software\MySQL AB\MySQL Examples and Samples 8.0, Name: , Value: 
DoStep
Action 15:15:17: RegisterProduct. Registering product
Position: 4720816
{409E9607-1B91-4534-8381-1CD753D5530F}
DoStep
Action 15:15:17: PublishFeatures. Publishing Product Features
Feature: SampleDB
DoStep
Action 15:15:17: PublishProduct. Publishing product information
Action 15:15:17: RollbackCleanup. Removing backup files
1: MySQL Examples and Samples 8.0 2: {409E9607-1B91-4534-8381-1CD753D5530F} 3: 1 
```





mysql的软件体系是什么 

- 有mysql server mysql workbench 还有sqlyog 
- 命令使用的时候也有很多 sql sqld 很奇怪





https://www.runoob.com/mysql/mysql-install.html

弄清楚整个安装过程每个步骤的目的都是什么

每个步骤在干什么



![image-20230308154000653](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308154000653.png)

找一个命令行文件检索工具

