第四周 python训练

https://www.bilibili.com/video/BV1ad4y1t773

> `print(s+“*3+1”)`和`print(s,”*3+1")`是不一样的
>
> 造成结果不同的本质原因是什么

```
进行的运算性质不同
+ 应该进行的是字符串拼接运算
, 对于的是参数的分隔
```



> 每次写代码的时候都会出现最初因为算法设计有问题
>
> 需要自己重头写的情况

```python
# 2 02 12 22 20 21
# 1 100 
    # 
number = input().split
start = int(number[1])
end = int(number[2])

def max(digit):
    for i in digit:
        max += "2"
    return max
def min(digit):
    min = "2"
    for i in digit - 1:
        min += "0"
    return min

def count_digit(number):
    digit = 0
    while(number):
        number/=10
        count += 1
    return digit
# '20' 21 20 '22'  10000 '10002' '20000'
def mid(start_digit,end_digit):
    mid_digit = end_digit  - start_digit


# 计算start和end各自的位
# 计算start位对应的最大值 end位对应的最小值
    #需要将其和最小start进行比较
    # 其他位同理
# end需要和最大的进行比较
```



> 审题过程中对细节的把握不太行

![image-20230318205720072](Untitled.assets/image-20230318205720072.png)



> 自己看到下面`object has no attribute`根本就不理解是什么出现问题了
>
> 直接就开始怀疑是自己环境配置上的问题
>
> 结果发现input()函数没有带括号
>
> 使用一些插件可以避免这种情况的发生
>
> 但是没办法锻炼自己看报错的能力 以及发现自己真正的问题 自己本质上根本不知道`object`在这里指代的是什么

![image-20230318210112758](Untitled.assets/image-20230318210112758.png)

```makefile
Traceback (most recent call last):
  File "f:\PythonProjects\basic_algorithm\digit_count.py", line 72, in <module>
    usercase = input.split()
AttributeError: 'builtin_function_or_method' object has no attribute 'split'   
```



> 自己这种编程写法反应了哪种错误
>
> 对什么知识点理解得不够清楚透彻呢
>
> 核心问题还是自己对代码判断执行过程理解得很粗糙费劲

```python
usercase = input().split()
start = int(usercase[0])
end = int(usercase[1])

count = 0
result = []
for number in range(start, end + 1):
    # list = []
    number = str(number) 
    flag = 0
    # TODO:python中使用的数据类型, 自己和cpp中的混淆了 12000
    for digit in number:
        if digit == '2':
            # list.append(number)
            if(result.append(number)):
                flag = 1
    if flag:
        count += 1
        
print(result)
print(count)
```

```
result.append()对象的函数返回的是None 插件有对应的提示
Changed if(result.append(number)) to if(result.append(number_str)) as list.append() always returns None.
```

```python
usercase = input().split()
start = int(usercase[0])
end = int(usercase[1])

count = 0
result = []
for number in range(start, end + 1):
    number_str = str(number)  # Renamed 'number' variable to 'number_str'
    flag = False  # Changed 'flag' to a boolean variable
    
    for digit in number_str:
        if digit == '2':
            result.append(number_str)
            flag = True  # Changed flag to True if '2' is found in the number
        
    if flag:
        count += 1
        
print(result)
print(count)
```





