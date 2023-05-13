- [ ] 配置wsl mysql开发环境

  [1]:https://pen-y-fan.github.io/2021/08/08/How-to-install-MySQL-on-WSL-2-Ubuntu/

  

- [ ] 命令行执行`sudo apt update && sudo apt upgrade`时间很长

  - [ ] 看下载速度是否由网络速度导致的
  - [ ] 自己想取消下载 重新尝试

- [ ] mysql安装步骤不理解

  - [ ] 不能理解安装逻辑导致每次安装都需要重新找到相关文档

- [ ] linux对重复执行的命令行如何处理

  - [ ] 可以检测出来重新下载的软件码

```shell
sudo mysql_secure_installation

Securing the MySQL server deployment.

Connecting to MySQL using a blank password.

VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No: n
Please set the password for root here.

New password: 

New password: Sorry, you can't use an empty password here.
```

- [ ] 如何终止上述设置密码的进程

- [ ] wsl的一些常用操作
  - [ ] 从windows命令行转移到ubuntu Linux命令行的时候需要注意什么

![image-20230224103707449](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230224103707449.png)

- [ ] 使用命令行操作因为看不到执行结果容易执行一半放弃, 找不到自己找过什么东西



![image-20230224132341338](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230224132341338.png)

什么是database driver

为啥从vscode连接本地mysql server这么困难
还有一个就是非常不理解创建connection这个过程的逻辑是什么
别人的教程我只会一步一步跟着搞



![image-20230224133908635](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230224133908635.png)

![image-20230224134037657](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230224134037657.png)



```shell
bigorilla@kristen:~/group_practice$ sudo mysql -u root
[sudo] password for bigorilla: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
bigorilla@kristen:~/group_practice$ sudo mysql -u root -p password
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
bigorilla@kristen:~/group_practice$ sudo service mysql start
 * Starting MySQL database server mysqld                                                                   su: warning: cannot change directory to /nonexistent: No such file or directory
                                                                                                    [ OK ]
bigorilla@kristen:~/group_practice$ sudo service mysql start
 * Starting MySQL database server mysqld                                                            [ OK ] 
bigorilla@kristen:~/group_practice$ sudo mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 8.0.32-0ubuntu0.22.04.2 (Ubuntu)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 



sudo /etc/init.d/mysql start

sudo service mysql start
```

如何理解这些输出文档

```
[1677377173268] INFO  (ext): SQLTools is starting
[1677377173280] INFO  (ext): initializing language client...
[1677377173292] INFO  (ext): Registering client for languages [{"scheme":"sqltools"},{"language":"sql","scheme":"untitled"},{"language":"sql","scheme":"file"},{"language":"sql","scheme":"sqltools"}]
    ns: "lc"
[1677377173337] INFO  (ext): loading plugins...
[1677377173338] INFO  (ext): registering Formatter Plugin.
    plugin: {
      "name": "Formatter Plugin"
    }
[1677377173339] INFO  (ext): registering Connection Manager Plugin.
    plugin: {
      "name": "Connection Manager Plugin"
    }
[1677377173340] INFO  (ext): registering CodeLens Plugin.
    plugin: {
      "name": "CodeLens Plugin",
      "registeredLanguages": []
    }
[1677377173346] INFO  (ext): registering Dependency Manager Plugin.
    plugin: {
      "name": "Dependency Manager Plugin",
      "installingDrivers": []
    }
[1677377173359] INFO  (ext): Connection explorer changed. Will be updated.
    ns: "conn-man:explorer"
[1677377173360] INFO  (ext): registering History Manager Plugin.
    plugin: {
      "name": "History Manager Plugin"
    }
[1677377173362] INFO  (ext): registering Bookmarks Manager Plugin.
    plugin: {
      "name": "Bookmarks Manager Plugin"
    }
[1677377173369] INFO  (ext): registering Authentication Provider Plugin.
    plugin: {
      "name": "Authentication Provider Plugin",
      "isRegistered": false
    }
[1677377173374] INFO  (ext): SQLTools activation completed. 102.937961 ms
[1677377173375] INFO  (ext): Formatter Plugin registered!
[1677377173376] INFO  (ext): CodeLens Plugin registered!
[1677377173376] INFO  (ext): Dependency Manager Plugin registered!
[1677377173377] INFO  (ext): Connection Manager Plugin registered!
[1677377173377] INFO  (ext): History Manager Plugin registered!
[1677377173377] INFO  (ext): Bookmarks Manager Plugin registered!
[1677377173378] INFO  (ext): Authentication Provider Plugin registered!
[1677377173613] INFO  (ext): registering MySQL/MariaDB Plugin (driver).
    plugin: {
      "extensionId": "mtxr.sqltools-driver-mysql",
      "name": "MySQL/MariaDB Plugin",
      "type": "driver"
    }
[1677377174091] INFO  (ls): SQLTools Server started!
===============================
Using node runtime?: no
ExecPath: /home/bigorilla/.vscode-server/bin/441438abd1ac652551dbe4d408dfcec8a499b8bf/node 
===============================
[1677377174351] INFO  (ext): LanguageClient ready
    ns: "lc"
[1677377174331] INFO  (ls): Initialized with node version:v16.14.2
[1677377174358] INFO  (ls): REQUEST RECEIVED => ls/RegisterPlugin
[1677377174358] INFO  (ls): request to register plugin: "/home/bigorilla/.vscode-server/extensions/mtxr.sqltools-driver-mysql-0.5.1/out/ls/plugin.js"
[1677377174619] INFO  (ext): EXECUTING COMMAND => sqltools.refreshTree
[1677377174620] INFO  (ext): Connection explorer changed. Will be updated.
    ns: "conn-man:explorer"
[1677377175362] INFO  (ext): Connection explorer changed. Will be updated.
    ns: "conn-man:explorer"
[1677377175462] INFO  (ls): Driver mysql registered!
    place: "driver-map"
    ns: "ls-context"
[1677377175463] INFO  (ls): Driver mariadb registered!
    place: "driver-map"
    ns: "ls-context"
[1677377175630] INFO  (ext): MySQL/MariaDB Plugin (driver) registered!
[1677377175765] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677377175770] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677377176632] INFO  (ext): EXECUTING COMMAND => sqltools.refreshTree
[1677377176632] INFO  (ext): Connection explorer changed. Will be updated.
    ns: "conn-man:explorer"
[1677377177650] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677377177654] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677377179459] INFO  (ext): EXECUTING COMMAND => sqltools.selectConnection
[1677377179461] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677377179471] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677377179478] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677377179493] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677377179499] INFO  (ls): REQUEST RECEIVED => connection/ConnectRequest
[1677377179513] INFO  (ls): Connection instance created for test.
    ns: "conn-manager"
[1677377179663] ERROR (ls): {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn"
[1677377179664] ERROR (ls): Connecting error: {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn-manager"
[1677377179665] ERROR (ls): Open connection error
    ns: "conn-manager"
[1677377179669] ERROR (ext): ERROR: Error opening connection connect ECONNREFUSED 127.0.0.1:3306, {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}}}
    ns: "error-handler"
[1677377218911] INFO  (ext): EXECUTING COMMAND => sqltools.selectConnection
[1677377218912] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677377218913] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677377218918] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677377218919] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677377218922] INFO  (ls): REQUEST RECEIVED => connection/ConnectRequest
[1677377218923] INFO  (ls): Connection instance created for testconnection.
    ns: "conn-manager"
[1677377218931] ERROR (ls): {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn"
[1677377218932] ERROR (ls): Connecting error: {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn-manager"
[1677377218933] ERROR (ls): Open connection error
    ns: "conn-manager"
[1677377218935] ERROR (ext): ERROR: Error opening connection connect ECONNREFUSED 127.0.0.1:33060, {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}}}
    ns: "error-handler"
[1677377219126] INFO  (ext): EXECUTING COMMAND => sqltools.selectConnection
[1677377219127] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677377219128] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677377219129] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677377219131] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677377219132] INFO  (ls): REQUEST RECEIVED => connection/ConnectRequest
[1677377219133] INFO  (ls): Connection instance created for testconnection.
    ns: "conn-manager"
[1677377219139] ERROR (ls): {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn"
[1677377219140] ERROR (ls): Connecting error: {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn-manager"
[1677377219141] ERROR (ls): Open connection error
    ns: "conn-manager"
[1677377219143] ERROR (ext): ERROR: Error opening connection connect ECONNREFUSED 127.0.0.1:33060, {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}}}
    ns: "error-handler"
[1677377905430] INFO  (ext): EXECUTING COMMAND => sqltools.openAddConnectionScreen
[1677377906313] INFO  (ext): getting extension mtxr.sqltools-driver-mysql information.
    ns: "ext-util"
[1677377906314] INFO  (ext): loaded extension information mtxr.sqltools-driver-mysql for driver MySQL/MariaDB.
    ns: "ext-util"
[1677377961399] INFO  (ext): EXECUTING COMMAND => sqltools.testConnection
[1677377982763] INFO  (ls): REQUEST RECEIVED => connection/TestConnectionRequest
[1677377982775] ERROR (ls): {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn"
[1677378003882] INFO  (ext): EXECUTING COMMAND => sqltools.testConnection
[1677378003959] INFO  (ls): REQUEST RECEIVED => connection/TestConnectionRequest
[1677378003965] ERROR (ls): {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn"
[1677378007776] INFO  (ext): EXECUTING COMMAND => sqltools.testConnection
[1677378007799] INFO  (ls): REQUEST RECEIVED => connection/TestConnectionRequest
[1677378007806] ERROR (ls): {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn"
[1677378027902] INFO  (ext): EXECUTING COMMAND => sqltools.testConnection
[1677378027903] INFO  (ls): REQUEST RECEIVED => connection/TestConnectionRequest
[1677378027911] ERROR (ls): {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn"
[1677378029527] INFO  (ext): EXECUTING COMMAND => sqltools.testConnection
[1677378029528] INFO  (ls): REQUEST RECEIVED => connection/TestConnectionRequest
[1677378029537] ERROR (ls): {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn"
[1677378036647] INFO  (ext): EXECUTING COMMAND => sqltools.addConnection
[1677378036785] INFO  (ext): Connection explorer changed. Will be updated.
    ns: "conn-man:explorer"
[1677378036849] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677378036851] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677378037508] INFO  (ext): Connection explorer changed. Will be updated.
    ns: "conn-man:explorer"
[1677378037713] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677378037715] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677378044737] INFO  (ext): EXECUTING COMMAND => sqltools.selectConnection
[1677378044738] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677378044739] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677378044742] INFO  (ext): EXECUTING COMMAND => sqltools.getConnections
[1677378044743] INFO  (ls): REQUEST RECEIVED => connection/GetConnectionsRequest
[1677378044745] INFO  (ls): REQUEST RECEIVED => connection/ConnectRequest
[1677378044745] INFO  (ls): Connection instance created for test3.
    ns: "conn-manager"
[1677378044754] ERROR (ls): {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn"
[1677378044755] ERROR (ls): Connecting error: {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}},"name":"Error"}
    ns: "conn-manager"
[1677378044756] ERROR (ls): Open connection error
    ns: "conn-manager"
[1677378044757] ERROR (ext): ERROR: Error opening connection ER_ACCESS_DENIED_ERROR: Access denied for user 'root'@'localhost' (using password: YES), {"code":-1,"data":{"driver":"MySQL","driverOptions":{"mysqlOptions":{"authProtocol":"default"}}}}
    ns: "error-handler"
[1677378054211] INFO  (ext): EXECUTING COMMAND => sqltools.showOutputChannel

```

```sql
mysql> use mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> selct User, Host, plugin FROM mysql.user;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'selct User, Host, plugin FROM mysql.user' at line 1
mysql> select User, Host, plugin FROM mysql.user;
+------------------+-----------+-----------------------+
| User             | Host      | plugin                |
+------------------+-----------+-----------------------+
| debian-sys-maint | localhost | caching_sha2_password |
| mysql.infoschema | localhost | caching_sha2_password |
| mysql.session    | localhost | caching_sha2_password |
| mysql.sys        | localhost | caching_sha2_password |
| root             | localhost | auth_socket           |
+------------------+-----------+-----------------------+
5 rows in set (0.00 sec)

mysql> update user set plugin='mysql_native_password' where user = 'root';
Query OK, 1 row affected (0.06 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> flush privileges;
Query OK, 0 rows affected (0.01 sec)

mysql> exit;
Bye
bigorilla@kristen:~/group_practice$ sudo service mysql restart;
 * Stopping MySQL database server mysqld                                                            [ OK ] 
 * Starting MySQL database server mysqld                  
 su: warning: cannot change directory to /nonexistent: No such file or directory
```

`su: warning: cannot change directory to /nonexistent: No such file or directory` 如何理解这个报错内容

查找传统与数据库有关的开发环境



![image-20230226103532588](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226103532588.png)

下载之后能在软件上查到相关的信息吗

win(或者自己的操作系统上)电脑上如何配置环境 

- 方便管理
- 方便拓展

像一个软件工程师那样管理自己的开发环境

How to manage your development environment like a software engineer

Managing your development environment like a software engineer involves setting up a ==consistent, efficient, and organized environment== for your development work. Here are some steps you can follow:

1. ==Choose your development tools==: Select the tools you need for your development environment, such as code editors, IDEs, command-line tools, version control systems, and testing frameworks.
2. ==Set up a version control system==: Use a version control system (e.g., Git) to track changes in your code, collaborate with others, and manage multiple versions of your code.
3. ==Create a consistent workspace==: Create a consistent workspace by organizing your files, folders, and configurations in a standardized way. Use a project structure that makes sense to you and your team.
4. ==Use automation==: Automate repetitive tasks, such as building, testing, and deploying code, using tools like build automation systems (e.g., Gradle) and continuous integration/continuous deployment (CI/CD) pipelines (e.g., Jenkins).
5. ==Use containerization==: Use containerization tools (e.g., Docker) to create a consistent and isolated environment for your development work, ensuring that your code runs the same way across different machines.
6. ==Document your processes==: Document your development processes and workflows, including coding standards, best practices, and deployment procedures. This can help you and your team members work more efficiently and consistently.
7. ==Keep your environment up-to-date==: Keep your development environment up-to-date by regularly updating your tools and dependencies, and by maintaining a backup of your environment to avoid losing your work.

By following these steps, you can manage your development environment like a software engineer, enabling you to work more efficiently, collaborate more effectively, and produce high-quality code.



Can you recommend some youtube videos about configuring an environment like a software engineer?

1. "Setting up your Development Environment" by Traversy Media: This video covers the basics of setting up a development environment, including installing Node.js, Visual Studio Code, and Git. https://www.youtube.com/watch?v=QaYts9sPmcY
2. "How to Set Up a Development Environment" by The Net Ninja: This video goes over how to set up a development environment for Node.js, including installing Node.js, setting up a text editor, and installing npm packages. https://www.youtube.com/watch?v=2GdZ9o8VZfM
3. "How to Set Up a React Development Environment" by FreeCodeCamp: This video covers how to set up a development environment for React, including installing Node.js, creating a new React project, and configuring a text editor. https://www.youtube.com/watch?v=OUPAIn3Sj6I
4. "How to Configure a Python Development Environment" by Corey Schafer: This video covers how to set up a Python development environment, including installing Python, setting up a text editor, and installing packages with pip. https://www.youtube.com/watch?v=YYXdXT2l-Gg
5. "How to Set Up a Java Development Environment" by Telusko: This video goes over how to set up a Java development environment, including installing the Java Development Kit, setting up a text editor, and configuring the classpath. https://www.youtube.com/watch?v=HNw4Qn8DVjc

<img src="C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226140004184.png" alt="image-20230226140004184" style="zoom:50%;" />

看details的时候能看出来软件安装工具实在干什么

<img src="C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226140716050.png" alt="image-20230226140716050" style="zoom:50%;" />

<img src="C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226140901533.png" alt="image-20230226140901533" style="zoom:50%;" />

![image-20230226143037327](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226143037327.png)

![image-20230226143223909](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226143223909.png)

![image-20230226143335074](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226143335074.png)

如果我结束这个进程 之后运行相关程序 需要进程操作系统会怎么办

以及出现端口占用的情况是为什么发生的

![image-20230226143447890](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226143447890.png)

![image-20230226143633004](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226143633004.png)

![image-20230226145314002](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226145314002.png)

![image-20230226145418533](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226145418533.png)

![image-20230226145620157](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230226145620157.png)

```
Beginning configuration step: Initializing database (may take a long time)

Attempting to run MySQL Server with --initialize-insecure option...
Starting process for MySQL Server 8.0.32...
Starting process with command: C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqld.exe --defaults-file="C:\ProgramData\MySQL\MySQL Server 8.0\my.ini" --console --initialize-insecure=on --lower-case-table-names=1...
mysqld: Can't get stat of 'C:\Users\Public\Documents\Wondershare\CreatorTemp' (OS errno 2 - No such file or directory)
option 'read_buffer_size': unsigned value 4096 adjusted to 8192.
The designated data directory C:\ProgramData\MySQL\MySQL Server 8.0\Data\ is unusable. You can remove all files that the server added to it.
Aborting
Process for mysqld, with ID 18284, was run successfully and exited with code 1.
Failed to start process for MySQL Server 8.0.32.
Database initialization failed.
Ended configuration step: Initializing database (may take a long time)
```



结束上述安装过程

计划使用中文文档进行安装









