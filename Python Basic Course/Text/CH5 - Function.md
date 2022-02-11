# 人工智能社团基础课——Python编程
# CH5 - 函数
## 前言
本章来学习一个很重要的东西，叫做函数。

假如你有多个代码段需要重复运行，你就可以创建一个函数，将代码段存放至函数内，然后多次调用函数就可以了，省去了时间与空间。

## 函数的定义
我们先看一个简单的函数：
```python 3
# 函数定义
def say_hello():
    print("Hello")

# 主体
say_hello()
print("Goodbye")
```
运行时，程序调用主体的say_hello()函数，进入函数内部并运行其中的代码块，然后执行print("Hello")，函数调用结束，回到主体上，运行主体的下一句代码，即print("Goodbye")。

如果我们想把print("Goodbye")也封装到函数中，就可以这样：
```python 3
# 函数定义1
def say_goodbye():
    print("Goodbye")

# 函数定义2
def say_hello():
    print("Hello")

# 主体
say_hello()
say_goodbye()
```
我是故意这么写的，目的就是告诉大家，函数的定义顺序不影响函数的调用顺序。现在给大家看一个定义函数的例子：
![avatar](/Python%20Basic%20Course/Picture/23.png)

return代表返回，返回一个数字和一个列表。

而def f(x, y)中的x和y代表参数，更具体地说是形式参数。我们调用函数时，要把实际参数传进函数里，比如f(2, 3)。此时在函数内部x为2，y为3。

定义函数，大家要注意：
1. def是保留字，定义函数必须使用；
2. 函数体相较于def语句要缩进一个Tab；
3. return语句可有可无，为动态类型。

## 函数的调用
实际上我们之前一直在调用函数，例如将一个列表转换为集合：
```python 3
List = [1,2,3,4,4]
Set = set(List)  # 调用set()函数
```
调用函数的时候，赋值符号左边的变量用来接收函数的返回值，有几个返回值就要有几个变量，没有返回值的函数可直接调用，例如强制退出函数exit(0)，还有打印函数print("Hello")。

大家可以看一下下面这个示例函数的运行结果：
![avatar](/Python%20Basic%20Course/Picture/24.png)

运行结果如下：

![avatar](/Python%20Basic%20Course/Picture/25.png)

有人会问了，map(abs, a_list)就是把abs()函数作用到a_list中的每个元素，为什么结果不是[1, 9, 10, 32]呢？

因为map函数返回了一个结果，我们却没有定义一个变量去接收它，而a_list实际上并没有改变。故返回的是原列表。而如果我们把这两句改成这样：
```python 3
new_list = list(map(abs, a_list))
return a_number, new_list
```
结果就是[1, 9, 10, 32]了。

## 函数参数
形参和实参的概念相信大家在程序设计语言课上都掌握了，还不清楚的先停一下，自己去查一下资料。

接下来我们要讲的是函数的形参。

### 1. 位置参数
调用函数时必须传入的参数，少或者多均会报错。

例如下面这个demo_function。
![avatar](/Python%20Basic%20Course/Picture/24.png)

三个参数（a_number、a_string、a_list）都是位置参数，如果调用函数时传入的参数个数不是三个就会报错。

### 2. 默认参数
在定义函数时赋予其一个默认值，如果调用函数时在该位置没有传入参数则使用默认值。
![avatar](/Python%20Basic%20Course/Picture/26.png)

参数表中，a_number、a_string为位置参数，a_list为默认参数。

### 3. 可变参数
传入的参数个数是可变的。例如定义一个sum函数，对传入的若干个数进行求和。
```python 3
def my_sum(*number):
    s = 0
    for i in number:
        s += i
    return s

num1 = my_sum(1,2,3,4,5,6,7)
num2 = my_sum(1,3,5,7)
```
实际上，Python会自动把传入\*number（可变参数）的参数放入一个tuple（元组）内，所以number实际上就是一个tuple（元组）。将组合数据类型作为可变参数传入函数时，只需要在数据名称前面加入*即可，例如sum(*num_list)。

### 4. 关键字参数
调用函数时，可以指定参数名（关键字）从而可以不考虑参数的传入顺序。例如：
![avatar](/Python%20Basic%20Course/Picture/26.png)
调用时，我可以这样：
```python 3
new_number, new_list = demo_function(Number, a_list = List, a_string = String)
```
当需要传入的参数个数未知，且每个参数都有名字时，可以使用关键字参数。

例如：我们定义一个创建用户信息的函数，其中姓名，性别与年龄是必选参数，但是有时会传入地区、职业、文化程度等其他信息，这些信息可以是0个或多个，此时可以这样定义函数：

```python 3
def create_a_person(name, sex, age, **kw):
    ···
```
实际上，Python会自动把传入**kw（关键字参数）的参数放入一个dict（字典）内，所以kw实际上是一个dict（字典），其中键是参数名，值是参数值。

请大家看下面的例子：
![avatar](/Python%20Basic%20Course/Picture/27.png)

运行结果为：

![avatar](/Python%20Basic%20Course/Picture/28.png)

### 5. 命名关键字参数
有时需要指定关键字参数的名字，例如在上一个示例中，我们要求必须指定用户所在的地区信息，这时可以用到关键字参数，定义函数如下：
```python 3
def create_a_person(name, sex, age, *, city, **kw):
    ···
```
即在命名关键字之前加一个*。同时，可以给命名关键字参数定义默认值。

请大家看下面的例子：
![avatar](/Python%20Basic%20Course/Picture/29.png)

大家注意：
1. 当参数表有可变参数时，命名关键字参数之前不需要加*,
2. 命名关键字参数与位置参数的区别是：调用函数时，可以不指定位置参数的参数名，但一定要指定命名关键字参数的参数名（如果需要传入），否则会报错。

### 6. 综合
相信学了那么多形参，大家肯定都晕了，那么请大家看一下下面这个例子，涵盖了上面列举的所有参数。

首先先告诉大家，参数表中形参的顺序是固定的，即必须按照：位置参数、默认参数、可变参数、命名关键字参数、关键字参数的顺序。

那么大家思考一下，create_a_person()这个函数中的参数表，它们各为什么参数？

![avatar](/Python%20Basic%20Course/Picture/30.png)

答案如下：

位置参数：name、sex、age；

可变参数：assets；

命名关键字参数：area、job，其中job有默认值None；

关键字参数：**kw。

然后接下来大家把自己的大脑当作编译器，思考一下它会是一个怎样的运行结果。

![avatar](/Python%20Basic%20Course/Picture/31.png)

## 在函数内调用函数
我们可以在函数内调用别的函数，但是该函数必须也要被定义，否则无法被调用。
例如：
```python 3
def f1():
    x = f2(30)
    print(x)

def f2(num):
    return num*num

f1()

'''
控制台输出：
900

'''
```
def f2(num)写在调用f1()之前的任意位置均可。

我们也可以在函数内部调用自己，称为函数递归。递归一般需要有递归出口，否则将陷入无限递归。
```python 3
# 定义一个阶乘函数
def f(n):
    if n == 1:
        return n
    else:
        return n*f(n-1)

result = f(10)  # 10的阶乘
print(result, end='')

'''
控制台输出：
3628800
'''
```

## 高阶函数
在Python中，变量可以指向函数，函数可以作为另一个函数的参数，函数还可以作为结果返回，这些都是高阶函数。

### 1. 变量指向函数
此操作相当于给函数更名。
```python 3
# 定义一个阶乘函数
def f(n):
    if n == 1:
        return n
    else:
        return n*f(n-1)

result = f(10)  # 10的阶乘
print(result, end=' ')

factor = f
print(factor(10))

'''
控制台输出：
3628800 3628800

'''
```
但是如果我们给函数名赋值，则它会变成变量，无法再调用。

### 2. 函数可以作为另一个函数的参数
```python 3
# 定义一个阶乘函数
def factor(n):
    f = factor
    if n == 1:
        return n
    else:
        return n*f(n-1)

def my_sum_function(x, y, f):
    return f(x)+f(y)

print(my_sum_function(8, 9, factor))  # 计算8!+9!

'''
控制台输出：
403200

'''
```

### 3. 函数可以作为结果返回
这一块算是扩展了，比较难，大家不理解就直接跳过。

![avatar](/Python%20Basic%20Course/Picture/32.png)

运行结果如下：

![avatar](/Python%20Basic%20Course/Picture/33.png)

当调用lazy_sum()时，返回的是sum()函数，所以相当于result = sum，当调用result()函数（即sum()函数）时，才会返回结果。内部函数sum可以引用外部函数lazy_sum的参数和局部变量，当lazy_sum返回函数sum时，相关参数和变量都保存在返回的函数中，这种结构称为“闭包（Closure）”。

这里还用到了在函数内定义函数的操作，则内部的函数只对外部的函数有效，例如你在主体或者其他函数内都无法调用lazy_sum()里的sum()函数。

为了大家理解，可以看这里例子
```python 3
def function1():
    print("I'm function 1.")

def function2():
    # function1() ，写在这里会报错
    def function1():
        print("I'm function 1 in function 2.")
    function1()

def function3():
    function1()

function1()
function2()
function3()

'''
控制台输出：
I'm function 1.
I'm function 1 in function 2.
I'm function 1.

'''
```

## 常用的高阶函数
接下来我们来讲3个常用的高阶函数。
### 1. map函数
map()函数是咱们的老熟人了，从CH2开始就一直在用。它接收两个参数，一个是函数，一个是list。map()函数将传入的函数依次作用到每个元素，并把结果作为一个新的迭代器（CH6讲）返回。

而现在大家不知道什么是迭代器，我们只需要先知道，list()函数可以作用在这个迭代器上，把它变成一个list。

我们看下面这个例子：
```python 3
def f(x):
    return x*x

List1 = [1,2,3,4,5]
List2 = list(map(f, List1))
print(List2)

'''
控制台输出：
[1, 4, 9, 16, 25]
'''
```
### 2. filter函数
起筛选作用，把函数作用在list上，若返回True则保留，否则删除之，最后也是返回一个迭代器，我们可以把它传入list()函数中让它转换成list。

例如下面这个例子：筛选1到100内的所有素数。

```python 3
def is_prime(x):
    if x < 2:
        return False
    else:
        for i in range(2, int(pow(x, 0.5))+1):
            if x % i == 0:
                return False
        return True

list1 = []
for i in range(1, 101):
    list1.append(i)

list2 = list(filter(is_prime, list1))
print(list2)
```
大家可以把这段代码自己copy到IDE上运行一下。然后请大家理解这段程序，尤其是筛选素数的函数，理解原理。很多作业题都有素数出现。

### 3. sorted函数
一共有3个参数，分别是iterable,key,reverse。

其中iterable是可迭代对象，比如list,tuple,set。

key函数可有可无。若有，将key函数作用在每个元素后再进行比较。

reverse是升序或降序，True为降序，False为升序（默认）。

之后返回一个list。

下面这个例子表示，以绝对值降序对List进行排序。
```python 3
List = [-4, 3, 1, 0, -9]
List2 = sorted(List, key=abs, reverse=True)
print(List2)

'''
控制台输出：
[-9, -4, 3, 1, 0]

'''
```
## 匿名函数
有些函数比较简短，如果还用常规的def方法来定义，浪费时间和空间。所以，我们可以使用匿名函数。

匿名函数的定义方法：
lambda 变量名:公式

特点：方便，不用另起函数名。

例如：
```python 3
list1 = [1,2,3,4,5]
print(list(map(lambda x: x*x, list1)))

'''
控制台输出：
[1, 4, 9, 16, 25]

'''
```
其中```lambda x: x*x```就是相当于```f(x)```，且定义了：
```python 3
def f(x):
    return x*x
```

再看一个例子：一个List中每个元素都是一个二元有序对，代表每个人的姓名与分数，现在按分数降序对List进行排序。
![avatar](/Python%20Basic%20Course/Picture/34.png)

## eval函数
eval函数十分强大，官方定义为：返回传入字符串的表达式的结果。就是说：将字符串当成有效的表达式来求值并返回计算结果。

1. 计算算式字符串的结果
   ```python 3
   print(eval('1+2*7-4/2+9')) #输出22.0

   x = 1
   print(eval("x+2")) #输出3
   ```
2. 将输入为列表（元组、集合、字典）格式的字符串转化为列表（元组、集合、字典）来返回
   ```python 3
   x = eval(input())
   print(x)
   # 尝试输入[1,2,3]、(1,2,3)、{1,1,3,4,2,2}吧！

## 结语
本章内容超级多，而且难理解，大家课后要好好消化。

然后要多做练习！所以我又布置作业啦！

PTA：浙大版《Python程序设计》题目集，第六章的所有题目以及函数题（函数题只需要提交函数）

以下题目尝试使用函数完成：
4-2、4-4、4-5、4-10、4-11、4-13、4-26、4-30

至此，你已经把Python的基础内容全部学完了。但是接下来的内容同样重要，让我们继续吧！

不过我真诚地建议，不要太快，多去PTA上刷题！等你真正学了所有的基础知识，又会运用了，再进行接下来的学习。