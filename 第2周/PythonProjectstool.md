```
  File "f:\PythonProjects\tool_projects\test.py", line 10
    file_directory = "F:\Notes\BasicNotes\Notesys\ComputerScience\DataStructure\Projects\reference_code"
                                                                                                        ^
SyntaxError: (unicode error) 'unicodeescape' codec can't decode bytes in position 2-3: malformed \N character escape
```

https://stackoverflow.com/questions/1347791/unicode-error-unicodeescape-codec-cant-decode-bytes-cannot-open-text-file

`In your code, the escape is followed by the character 's', which is invalid.` 是什么意思

![image-20230227170648919](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230227170648919.png)





![img](C:\Users\lenovo\Desktop\数据结构.assets\Z55B7C$_HMD9T4TCBH]EDIS.png)

乱码问题处理

如何批量修改编码格式



https://www.zhihu.com/question/34415763

针对vscode乱码的解决办法

![image-20230227171459115](C:\Users\lenovo\Desktop\数据结构.assets\image-20230227171459115.png)

这个操作只能更改一个文件

如果批量解决所有文件出现的问题

reopen和save的区别是什么





乱码问题汇总整理