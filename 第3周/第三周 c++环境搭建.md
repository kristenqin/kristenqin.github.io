第三周 c++环境搭建

vscode中的c++插件和vscode的关系是什么



设置vscode中的输入输出为从文件输入输出



开大程序的栈空间

- 目的是什么
  - 解决栈空间使用过多的时候 程序会运行失败

![image-20230308085328412](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308085328412.png)

![image-20230308085609423](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308085609423.png)

![image-20230308085653062](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308085653062.png)

> 照着视频中加入了这段代码之后无法执行成功
>
> `"-wl,--stack=500000000",` 将视频中这段代码删除之后其他文件就能正常运行生成编译文件了

![image-20230308091525967](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308091525967.png)

> `F:\CProjects\test\cpp_standard_control.cpp:12:10: fatal error: bit: No such file or directory
>  #include <bit>
>           ^~~~~
> compilation terminated.` 错误原因





![image-20230308091719887](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308091719887.png)

> 需要自己像了解英语语法那样了解cpp的语法结构
>
> 不过可能会因为cpp的语法比较庞杂
>
> 自己应该会可能需要明确自己的使用目的来框定一个范围
>
> (语法本身体系庞大就一定语法体系的各部分组成结构不清晰吗)



![image-20230308092220503](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308092220503.png)

![image-20230308092259566](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20230308092259566.png)

> 一个vscode的工作窗口组成结构
>
> 各个结构对应的是什么
>
> 以及每部分的功能



```cpp
g++.exe: error: unrecognized command line option '--std=c++20'; did you mean '--std=c++2a'?
```

> 为啥每次修改一下.vscode里面的json文件就容易出错啊

