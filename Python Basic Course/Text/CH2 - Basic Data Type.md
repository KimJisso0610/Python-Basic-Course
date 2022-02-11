# 人工智能社团基础课——Python编程
# CH2 - 基本数据类型
## 前言
接下来我们将开始编程语言的学习，应老师的要求我会把代码放到Jupyter NoteBook上，大家可以直接在上面运行，也可以copy代码到IDE上运行。

~~本章的代码在这里：~~
~~https://datalore.jetbrains.com/notebook/NhV6A6YgESEElnprCWqWzr/rvF4DIVZdwaAtIFmvFYAVB/~~

补！充！：由于Datalore不好用，我把代码都放到文档里了，大家不需要打开链接了！

## Python的输入与输出
Python的输入与输出语句比较简单，就是使用input()和print()，例如：
```python
x = input()
print(x)
print(x)
```
运行这段代码之后，首先控制台会需要你从键盘上输入东西，按下回车键之后，你输入的东西就会传到x里面去。print(x)的意思就是把x里的东西再输出出来。由此，你就已经学会了基本的输入和输出了。你可以在Datalore上试着运行一下[1]，或者把[1]的代码copy到Pycharm上去运行。
```python 3
# [1]
x = input()
print(x)
print(x) 
```

## Python的基本数据类型
Python的数据类型有如下：

1. 整型（int）：即整数，例如1、2、3、100、200，整型数据可以满足整数的运算法则，例如加减乘除等。值得注意的是，Python的整型是没有范围的；
2. 浮点型（float）：即小数，例如1.5、2.225、3.0，浮点型数据也满足小数的运算法则，也是没有范围的；
   >接着要补充一下Python的运算符规则：
   >
   >(1) “+”：用于两个数字类型（整型、浮点型）相加；
   >
   >(2) “-”：用于两个数字类型相减；
   >
   >(3) “*”：用于两个数字类型相乘；
   >
   >(4) “/”：用于两个数字类型相除，结果必为浮点型；
   >
   >(5) “//”：用于两个数字类型相除（向下取整），结果必为整型；
   >
   >(6) “//”：用于两个数字类型取余，如8%3=2；
   >
   >不同的数字类型运算，浮点型会覆盖整型。如100.12 × 200 = 20024.0。
3. 字符串型(str)：单个字符或多个字符组成，例如'a'、'Python'、'I love you'等，注意用单引号或双引号，效果相同。
   > 字符串也有符号运算，但是只可以用“+”和“*”。
   >
   > 例如：
   >
   > 'abcde'+'fghi' = 'abcdefghi'；
   >
   > 'abc'*3 = 'abcabcabc'。
4. 布尔类型(bool)：只有真（用True表示）和假（用False表示）；
5. 空类型：用None表示；
6. 组合数据类型：我们将在下一章讲到，包括列表(list)、元组(tuple)、集合(set)和字典(dict)。

你可以通过Datalore里的[2]去测试自己是否理解了数据类型，建议先自己猜一下a~k都是什么数据类型，然后再去运行代码检查是否正确。
```python 3
# [2]
a = 123
b = 1.05
c = 2.0000000
d = '123'
e = "3.14159265"
f = 'Y'
g = None
h = True
i = 1+8
j = 16-(8/2)
k = 9%(7//4)

print(a, type(a))
print(b, type(b))
print(c, type(c))
print(d, type(d))
print(e, type(e))
print(f, type(f))
print(g, type(g))
print(h, type(h))
print(i, type(i))
print(j, type(j))
print(k, type(k))
```

## 字符串操作
我们可以使用一些函数来对字符串进行操作。如果你还不理解函数的意思，可以先照着下面的去做。
1. lower()和upper()：把字符串里的大写字母变为小写的，或者小写字母变为大写的；
   用法："ABCDE".lower()，结果为"abcde"；'efg'.upper()，结果为'efg'。通过Datalore里的[3]去体会。
   ```python 3
   print('FHWEIfhewifbw123  ....，，。。？？12389hdqubdGUY2G'.upper())
   print('FHWEIfhewifbw123  ....，，。。？？12389hdqubdGUY2G'.lower())
   ```

2. split(sep)：根据sep分割字符串，返回一个列表（下一章讲）；
   用法：'1,2,3,4,5'.split(',')，结果为['1','2','3','4','5']，即以逗号分割字符串，变为5个部分。通过Datalore里的[4]去体会。
   ```python 3
   # [4]
   print('abcabcabcabcabc'.split('bc'))
   print('a,b,c,d,e,f,g'.split(','))
   print('1 2 3 4 5 6 7'.split())
   print('a,,,,b,,,,,,,c,,d,,,,e,,'.split(','))
   ```
3. count(str)：返回str在字符串中出现的次数；
   用法："An apple a day!".count('a')，结果为3。
4. replace(old, new)：把原来的字符串里的old字符串替换为new字符串后返回一个新的字符串；
   用法：'abcabcabc'.replace('a','d')，结果为'dbcdbcdbc'。通过Datalore里的[5]去体会。
5. strip(sep)：从字符串左侧及右侧去掉sep中出现的字符后返回一个新的字符串。通过Datalore里的[6]去体会。
   ```python 3
   # [5]
   print('abcabcabc'.replace('a','aaaaaa'))
   print('aaaaaaaaaaaabbaaaaaaaaabcccccaaa'.replace('aa','*'))

   # [6]
   print("abcdabcdabcdabcd".strip("ad"))
   print("   ==  I love Python  ==  ".strip("=n"))
   print("   ==  I love Python  ==  ".strip(" =n"))
   print("   Ha ha ha ha.  ".strip())
   ```
6. sep.join(str)：在str除最后一个字符外的每一个字符后面插入sep，然后返回一个新的字符串。通过Datalore里的[7]去体会。
   ```python 3
   # [7]
   print(", ".join("ABCDEFG"))
   print('.'.join("I Love Python."))
   ```
7. str与int/float的转换：
   1. 用str()将int转换为str，用int()将str转换为int，float同理。
   2. 将str转换为int时，str必须为纯数字。
   3. 进制转换：int(str, base)，其中base默认为10。
   4. 通过Datalore里的[8]去体会。
   ```python 3
   # [8]
   print(int("10101010111", 2))
   print(int("a65ff90d", 16))
   print(float("3.1415000000000"))
   ```
## 变量
变量可以是任何类型，Python中的变量类型是动态的，即不需要声明其类型，但是如果在某些条件下由于类型没有声明而造成TypeError，这时就需要用函数来对其声明类型。

> ```python 3
> # 以下对变量的赋值是符合规则的：
> 
> a = 1  # 变量a自动认为int类型
> b = 0.1234  # 变量b自动认为float类型
> c = "Python"  # 变量c自动认为str类型
> d = [1, 2, 3, 4]  # 变量d自动认为list类型
> 
> b = str(b)  # 将变量b转换为str类型
> d = set(d)  # 将变量d转换为set类型
> ```

变量的命名规则：
1. 必须以字母、下划线开头，后面可以跟任意数目的字母、数字和下划线。此处的字母并不局限于 26 个英文字母，可以包含中文字符、日文字符等。
2. 由于 Python 3 支持 UTF-8 字符集，因此 Python 3 的标识符可以使用 UTF-8 所能表示的多种语言的字符。Python 语言是区分大小写的，因此 abc 和 Abc 是两个不同的标识符。
3. 命名时不能使用保留字。

养成良好的命名习惯：
1. 变量名字起得有意义，例如count表示一个计数器，sum表示总和，number表示数字。
2. 用英语来命名。
3. 组合单词命名法：（1）驼峰命名法，每个单词的首字母大写，例如SquareArea，常用于类名；（2）下划线分隔命名法，每个单词用下划线分隔，例如square_area，常用于变量名和函数名。

为什么要强调大家养成良好的命名习惯，方便自己也是方便他人。例如如下两段代码，你觉得哪个看起来更舒服：

```python 3
class Complex:
    
    def __init__(self, user_input_real, user_input_image):
        self.real = user_input_real
        self.image = user_input_image
    
    def print_complex(self):
        if self.image < 0:
            print("{}-{}i".format(self.real, abs(self.image)))
        else:
            print("{}+{}i".format(self.real, self.image))

   
def add_complex(complex1, complex2):
    result_real = complex1.real + complex2.real
    result_image = complex1.image + complex2.image
    result = Complex(result_real, result_image)
    return result


complex1 = Complex(2, 3)
complex2 = Complex(4, 5)
complex3 = add_complex(complex1, complex2)
complex3.print_complex()
```
```python 3
class fushu:

    def __init__(self, shibu, xubu):
        self.shibu = shibu
        self.xubu = xubu

    def shuchufushu(self):
        if self.xubu < 0:
            print("{}-{}i".format(self.shibu, abs(self.xubu)))
        else:
            print("{}+{}i".format(self.shibu, self.xubu))


def fushuxiangjia(x, y):
    a = x.shibu + y.shibu
    b = x.xubu + y.xubu
    xindefushu = fushu(a, b)
    return xindefushu


a = fushu(2, 3)
b = fushu(4, 5)
c = fushuxiangjia(a, b)
c.shuchufushu()
```

## 保留字
前面跟大家说了变量命名时不能使用保留字，有人就问了，啥是保留字？

保留字是Python语言中一些已经被赋予特定意义的单词，这就要求开发者在开发程序时，不能用这些保留字作为标识符给变量、函数、类、模板以及其他对象命名。

也就是说，大家命名时不能用这些单词，因为它已经赋予了特定意义，如果打出来会变颜色。例如下面代码段中的深蓝色单词，都是保留字（注意浅蓝色的不是）：
```python 3
import math
a, b, c = map(int, input().split())
global x
x = 0
for i in range(10):
   if i % 2 == 0:
      print(str(a) * i)
   elif i % 3 == 0:
      print(str(b) * i)
      break
   else:
      x += 1
print(x)
```

Python中所有的保留字：
```python 3
>>> import keyword
>>> print(keyword.kwlist)
['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

## 注释
在写代码时，有时为了解释一些东西（比如你写的一长串判断语句是为了判断什么，或者写了一个函数是什么功能，或者定义了一个变量是用来干嘛的），可以在其之后写注释。只要在注释语句前加入#号就可。编译时不会编译#后的句子。下面代码段中绿色的斜体就是注释。
> ```python 3
> # 以下对变量的赋值是符合规则的：
> 
> a = 1  # 变量a自动认为int类型
> b = 0.1234  # 变量b自动认为float类型
> c = "Python"  # 变量c自动认为str类型
> d = [1, 2, 3, 4]  # 变量d自动认为list类型
> 
> b = str(b)  # 将变量b转换为str类型
> d = set(d)  # 将变量d转换为set类型
> ```

多行注释：使用三个单引号或双引号包住要注释的部分即可。
```python 3
'''
Time: 2022-02-06
Author: Yifei Lu
Name: Image recognition neural network for garbage classification based on PaddleX
'''

import numpy as np
......
```

大家务必多写注释，将一个程序员界的地狱笑话：一个程序员把他的同事杀了，因为他的同事写代码不写注释。

## 格式化输出
前面我们学习了怎么进行输出，但是这个print()函数功能可不止这些。

例子：现在有一个数据库，存有每个学生的姓名(name)的成绩(score)，现在要求从键盘上输入一个学生的姓名，按”(姓名)的成绩是(成绩)“的语句来输出，应该怎么用一句print语句实现呢？

这里有两个方法：一个是用%，一个是用.format()，都是格式化输出的例子。

1. 用 %
![avatar](/Python%20Basic%20Course/Picture/8.png)

2. 用.format()
![avatar](/Python%20Basic%20Course/Picture/9.png)
例如：
![avatar](/Python%20Basic%20Course/Picture/10.png)
大家也可以通过Datalore的[9]去体会。
```python 3
# [9]
print("{:*>8.2s}".format('Python'))
print("{}+1={}".format(3.23, 3.23+1))
print("I love {:^18s} !".format('Python'))
print("{1:<15s}, {2:6s}, {0:<2.4s}".format('is', 'like', 'are'))
```

接下来，还有一个规定输出语句末尾的参数end，因为我们平时用print()函数输出语句后，它会以换行结尾，假如我们需要以空格结尾，应该怎么做呢？
```python 3
print(123)
print(456)
print(789)

'''
控制台会这么输出：
123
456
789

'''
```
这时在print(...)后面加上参数end=' '，即可。
```python 3
print(123, end=' ')
print(456, end=' ')
print(789, end=' ')

'''
控制台会这么输出：
123 456 789
'''
```

## 关于输入
Python 3.x版本中，程序默认把控制台输出的所有内容视为字符串。
所以，当有些人做简单加法这个题目，会发现出问题。
```python 3
a = input()
b = input()
print(a+b)

'''
输入：
2
55
输出：
255

'''
```
还记得字符串加法吗？就是把两个字符串串在一起。为此，要AC这道题，我们需要把a和b转换成int类型，大家可以停下来想一想，怎么做来着？
```python 3
num1 = int(input())
num2 = int(input())
print(num1+num2)

'''
输入：
2
55
输出：
57

'''
```
接下来又有一个问题了，题目是这样输入的：2 55，不换行，用空格分隔。也就是说第二个语句完全读不到东西，这时我们可以使用分割字符串的方法，把这两个数分隔开来。
```python 3
string = input()  # string = "2 55"
list1 = string.split()  # list1 = ["2", "55"]
num1 = int(list1[0])
num2 = int(list1[1])
print(num1+num2)

'''
输入：
2 55
输出：
57

'''
```
接下来介绍一个语句，可以一句话搞定输入。

首先我们要知道Python可以进行同时多次赋值，例如：
```python 3
a, b, c = 1, 2, 3  # 将1、2、3分别赋值给a、b、c
a, b = b, a  # 交换a与b的值而不需要使用辅助变量
```
这给我们带来很大的方便。
map()函数的用法为map(f, list)，表示把函数f作用于list中的每个元素。我们在CH5会细讲。比如list1 = ['123', '234', '345']，那么map(int, list1)的意思表示为将int函数作用于list1中的每个元素中，把字符串变为int型。此时就会返回一个新的list，值为[123, 234, 345]。

于是，刚刚那段代码可以这样改写：
```python 3
num1, num2 = map(int, input().split())
print(num1+num2)
```
是不是超级快！

## 结语
在下一章，我们将会讲到程序的三种结构，包括顺序、分支、循环。那么这一章就没有建议练习了，留到下一章再告诉大家。