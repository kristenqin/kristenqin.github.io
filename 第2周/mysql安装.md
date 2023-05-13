mysql安装

https://www.bilibili.com/video/BV1iq4y1u7vj?p=6&vd_source=bd363ff17b54594b4e6ad483160d92e2

四个位置

1. 软件本身位置

2. 软件数据位置

3. 服务状态查看

   `\HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\EventLog\Application\MySQLD Service`

   删除服务

   ![image-20230227131829235](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230227131829235.png)

   ![image-20230227132122311](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230227132122311.png)

   > `refreshenv` 之后还是删不干净

   `sc delete mysql` 尝试使用这个命令进行删除

4. 环境变量位置




mysql可以多版本同时存在



`第四次报错有两种情况，第一种:注意安装的文件夹不能有中文文字出现，第二种：没有卸载干净（iobit这个卸载软件）`



![image-20230227150437986](mysql安装.assets/image-20230227150437986.png)



重装之后还是出现上次的问题了

```
1、windows端使用Win+R --> 运行 "services.msc" --> 打开service服务管理器，找到安装mysql的服务名称 
2、右键 --> 属性 --> 登录，更改成“本地系统账户” --> 确定 回到安装界面,,点击 Execute
```

![image-20230227154339675](mysql安装.assets/image-20230227154339675.png)

尝试安装5.7

```
Beginning configuration step: Initializing database (may take a long time)

Deleting the data directory from a previous (failed) configuration...
Attempting to run MySQL Server with --initialize-insecure option...
Starting process for MySQL Server 5.7.41...
Starting process with command: F:\Software\MySQL\MySQL Server 5.7\bin\mysqld.exe --defaults-file="C:\ProgramData\MySQL\MySQL Server 5.7\my.ini" --console --initialize-insecure=on --lower-case-table-names=1...
TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
InnoDB: Unable to create temporary file; errno: 0
InnoDB: Plugin initialization aborted with error Generic error
Plugin 'InnoDB' init function returned error.
Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
Failed to initialize builtin plugins.
Aborting
Process for mysqld, with ID 19272, was run successfully and exited with code 1.
Failed to start process for MySQL Server 5.7.41.
Database initialization failed.
Ended configuration step: Initializing database (may take a long time)
```

大失败啊啊啊啊啊啊啊啊啊啊啊