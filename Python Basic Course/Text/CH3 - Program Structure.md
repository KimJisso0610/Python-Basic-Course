# 人工智能社团基础课——Python编程
# CH3 - 程序结构
## 前言
接下来我们将开始编程语言的学习，应老师的要求我会把代码放到Jupyter NoteBook上，大家可以直接在上面运行，也可以copy代码到IDE上运行。

本章内容比较少，到真正讲课的时候估计会和第二章或者第四章一起讲。

~~本章的代码在这里：~~
~~https://datalore.jetbrains.com/notebook/NhV6A6YgESEElnprCWqWzr/gwou7mn63X0U5gkNnZQCb7/~~

补！充！：由于Datalore不好用，我把代码都放到文档里了，大家不需要打开链接了！

## 顺序结构
顾名思义，就是按顺序运行的结构。
只需要比较这两个代码，很好理解的。
```python 3
a = int(input())
b = int(input())
print()
print(a)
print(b)
print(a+b)
```
``` python 3
a = int(input())
print(a)
b = int(input())
print(b)
print()
print(a+b)
```
## 条件结构
也就是经典的if-else类型的结构。用到三个保留字：if / elif / else，其中if和elif后面可以跟条件，满足则进入，不满足则不进入。例如这个判断闰年的程序：
![avatar](/Python%20Basic%20Course/Picture/11.png)

你可以在Datalore里运行[3]，先猜猜输出结果，再去运行验证一下猜测是否正确。
```python 3
# [3]
# In each conditional structure, enter at most 1 code block.

a = 100

if a % 3 == 0:
    print(1)
elif a % 2 == 0:
    print(2)
elif a % 10 == 0:
    print(3)
else:
    print(4)
```

## 缩进
Python对代码缩进非常严格。if语句后面的代码块必须比if语句多四个字符的缩进（4个空格或1个Tab），缩进不正确会报错，而且影响程序运行。
你可以在Datalore里运行[1]和[2]，观察由于缩进不对造成运行结果的不对。
```python 3
# [1]

number = 11
if number % 2 == 1:
    print(number, end=' ')
    print("Number is odd.")
else:
    print(number, end=' ')
print("Number is even.")

# [2]

number = 11
if number % 2 == 1:
    print(number, end=' ')
    print("Number is odd.")
else:
    print(number, end=' ')
    print("Number is even.")
```

## 循环结构
### while循环
满足while后的条件则进入循环，否则退出循环。
```python 3
# 计算1到100的和

Sum = 0
i = 1

while i <= 100:
    Sum = Sum+i
    i = i+1

print(Sum)
```
### break & continue
break代表直接结束循环，continue代表跳过本次循环。
```python 3
# 列举1到100以内的所有偶数
i = 1

while True:
    # while True是一个永远为真的语句，是一个无限循环

    if i > 100:
        break
    
    i = i+1

    if i % 2 != 0:
        continue

    print(i)
```
上面的代码含义如下：
1. 当i大于100时，进入if语句里，执行break，整个while循环结束，break后面的语句都不执行。
2. 当i为奇数时，进入if语句里，执行continue，跳过本次循环，从while循环的头开始运行，continue后面的语句都不执行。
3. 输出i

### for...in...循环
从一个list中依次取元素直至取完。
运行Datalore里的[4]查看结果。
```python 3
# [4]
List = [1,2,3,4,5,6,7,12,313]
for i in List:
    print(i)
```
range(a, b, step)：一个可迭代对象，目前可以先理解为一个list，生成一个以a开头，以step为步长的list，直到b为止（但是不包括b），step不写默认为1，a写默认为0。运行Datalore里的[5]查看结果。
```python 3
# [5]
print(list(range(1, 4)))
print(list(range(2, 10, 2)))
print(list(range(3)))
print(list(range(10,0,-1)))
```

## 结语
没错，结束了，没想到吧......

但是确实没什么可以讲的。

有一些小白看到这里，肯定就要骂我了，list到底是个什么鬼东西！怎么还不讲！

别急别急，下一章就给你们讲。

接下来，就是布置作业（bushi）时间！

![avatar](/Python%20Basic%20Course/Picture/12.png)