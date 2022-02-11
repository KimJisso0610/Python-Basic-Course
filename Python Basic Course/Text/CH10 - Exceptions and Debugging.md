# 人工智能社团基础课——Python编程
# CH10 - 异常与调试
## 前言

如果你能坚持学到第十章，说明你真的是一个有毅力的人！👏

最后一章了，本章主要讲的是异常的种类与处理，以及如何调试代码。我们在做大型项目时，例如使用爬虫爬取网页，有时会因为爬取失败而报一个错误，这个错误可能会导致整个程序直接中止。但是我们希望的是当爬虫爬取失败时，跳过它，爬取其他的地方，这时我们就需要使用语句来捕获异常并处理异常。

## 异常的种类

> 转载自：https://blog.csdn.net/likunkun__/article/details/81916269
> ![avatar](/Python%20Basic%20Course/Picture/60.png)

上面是一些常见的异常种类，除此之外还有别的。

## 异常的处理

接下来我们看一个例子：

有两个列表List1 = [3,5,7,9,10]，List2 = [0,1,2]，现在我们想用List2中的每个元素除List1中的每个元素，得到的代码如下：
```python 3
List1 = [3, 5, 7, 9, 10]
List2 = [0, 1, 2]

for i in List2:
    for j in List1:
        print(j/i)
```

此时我们会发现，运行程序会报错：
```
Traceback (most recent call last):
  File "E:\Project\Python Project\ch1demo\main.py", line 6, in <module>
    print(j/i)
ZeroDivisionError: division by zero

Process finished with exit code 1
```
我们先来学会都这个报错：
1. File "E:\Project\Python Project\ch1demo\main.py", line 6, in \<module> 这句话表示：错误出现在main.py的第6行。
2. ZeroDivisionError: division by zero 表示异常的类型，此处为除数为0产生的异常。

接下来我们处理这段代码，如果除数为0，我们就输出'Divide by zero!'，否则就正常输出商。

大家首先肯定想到的就是用if语句，这也是可以的。只是在这一章中，为了演示，我们规定：如果程序抛出了ZeroDivisionError，我们立即捕获它，防止程序中止，并输出'Divide by zero!'。

于是我们需要用到try-except代码块。

```python 3
try:
    代码段
except Exception1, Exception2:
    操作1
except Exception3:
    操作2
else:
    操作3
```
运行时，先运行try里面的代码段，如果代码段中抛出异常，就会被捕获，转移给except处理。如果异常是Exception1和Exception2，就进入操作1处理；如果异常是Exception3，就进入操作2处理；如果是其他异常，就进入操作3处理。

else是可以省略的。except后也可以不跟异常类型，这表示只要try代码段抛出异常，不管是什么异常，都由except后的代码段处理。

处理后的代码如下：
```python 3
List1 = [3, 5, 7, 9, 10]
List2 = [0, 1, 2]

try:
    for i in List2:
        for j in List1:
            print(j/i)
except ZeroDivisionError:
    print('Divide by zero!')
```

这时我们会发现，如果抛出了异常，那么整个try代码段就不再运行了，这显然也不是我们想要的结果。所以我们应该把try-except放在循环里面：
```python 3
List1 = [3, 5, 7, 9, 10]
List2 = [0, 1, 2]

for i in List2:
    for j in List1:
        try:
            print(j/i)
        except ZeroDivisionError:
            print('Divide by zero!')
```
当然，你也可以删掉ZeroDivisionError，这表示只要抛出任何异常，都进行处理。

## 使用Pycharm进行调试

接下来我们来学习最后一部分，就是debug。

首先我们要学会打断点。

![avatar](/Python%20Basic%20Course/Picture/61.png)

如上图，我在第七行打了一个断点。只需要在数字7右边的空白部分点一下就能打上断点。

接着我们点击一下运行旁边的那个虫的图标，就是进行调试。程序会开始运行，至断点处停止，并显示相关信息。

![avatar](/Python%20Basic%20Course/Picture/62.png)

我们可以看到，Pycharm会在停止时，在相关变量旁边显示它当前的值，我们可以在下面的窗口视图里查看变量的一些信息。

接下来我们就要用到这几个很重要的调试键了。

![avatar](/Python%20Basic%20Course/Picture/63.png)

我来一一给大家解释一下：

1. Show Execution Point：把光标移动到程序运行停止的地方，即第七行print(j/i)左边。
2. Step Over：单步执行，如果遇到函数调用，则不会进入函数，直接跳到函数执行完的结果处。即点一下，跳到第8行。
3. Step Into：单步执行，如果遇到函数，会进入函数的定义部分，继续单步执行。如果你使用的函数是在别的文件里定义的，会打开别的文件。
4. Step Into My Code：与Step Into差不多，就是不会打开别的文件。
5. Step Out：假如进入了一个函数体中，你看了两行代码，不想看了，跳出当前函数体内，返回到调用此函数的地方，即使用此功能即可。
6. Run To Cursor：运行到光标处，你把光标放到哪它就运行到哪然后停下来。懒人专用，有时我就打一个断点就够。

比较常用的就是Step Over，有时循环比较大，你不想单步执行，就把光标放到循环外面，然后Run To Cursor即可。

怎么样，是不是很方便？大家可以自己Debug一些代码去感受一下！

## 结语
恭喜大家！毕业了！

感谢大家一直以来的坚持！学到就是赚到这个东西。

其实我来漏了一些内容没和大家说，比如正则表达式、断言、日志等，大家就自己找资料学啦！

有了Python的编程基础，后续你学习别的编程语言，或者学习Python的其他功能，比如数据分析、深度学习、网络爬虫等等就会轻松很多。接下来我们即将要学习的是机器学习，然后到深度学习。未来再见！