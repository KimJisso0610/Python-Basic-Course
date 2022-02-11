# 人工智能社团基础课——Python编程
# CH8 - 模块化编程
## 前言

这一章我们来学习模块化编程。Python有很多功能强大的库供我们使用，而我们在环境下安装好后，就可以用import方法导入这些库并使用里面的方法。有点类似于C的#include<>。

## 使用Python的库
我们安装的Anaconda环境有默认安装很多库。比如math、random等。我们可以使用它。

例如生成一个0到99范围内的随机数。
```python 3
import random

random_number = random.randint(0, 100)
print(random_number)
```
我们使用random库的randint函数来生成。使用某个库的某个方法，我们就需要使用库名.方法名去调用。

再例如，我们使用正弦函数，可以调用math库里的sin函数。
```python 3
import math

result = math.sin(20)
print(result)
```

## 使用Anaconda安装新的Python库
网络之大，无奇不有。Python的优势就在于它有很多强大的库，我们可以使用pip命令，它就会自动下载安装。

接下来教大家安装requests库和BeautifulSoup库，它是网络爬虫需要用到的库，网络爬虫我们不教，你们可以自己去网上学。

1. 我们打开Anaconda Prompt这个程序。
   
   ![avatar](/Python%20Basic%20Course/Picture/47.png)

   打开后，它默认是在base环境下的，我们就在base环境下安装即可。

   ![avatar](/Python%20Basic%20Course/Picture/48.png)

2. 我们把pip的源改为清华源，因为它默认是国外源，下载速度比较慢。
   
   把这段指令复制到上面，按回车运行。
   ```shell
   pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
   ```
   ![avatar](/Python%20Basic%20Course/Picture/49.png)
   
   如果为上图所示，则表示修改成功。

3. 更新一次pip，输入如下指令：
   
   ```shell
   pip install --upgrade pip
   ```
   ![avatar](/Python%20Basic%20Course/Picture/50.png)

   如果为上图所示，则表示修改成功。warning不用管，因为我们在CH1安装Anaconda时没有把它放到PATH中才造成的。

4. 安装requests库和BeautifulSoup库，分别输入如下两个指令：
    ```shell
   pip install requests
   pip install BeautifulSoup4
   ```
   ![avatar](/Python%20Basic%20Course/Picture/51.png)

   由于我的已经安装过了，所以我的是这样显示。大家如果安装成功，会在最后一句显示successfully installed xxx字样。

至此，你已经学会了如何安装Python库了，后续我们讲别的内容时都可能会需要额外安装一些库，大家按照步骤走即可，不过可以省去步骤2和3，它只要运行一次就已经做好了修改。

## 模块的存储与导入(函数)

假如你在一个.py文件里写出了一段绝妙的代码，后续在其他.py文件想多次用这段代码里面的类或方法，就可以存储该模块。

比如，我们在同一目录下创建两个.py文件，my_module存储我们定义的一些函数，main为主程序。

![avatar](/Python%20Basic%20Course/Picture/52.png)

我们在my_module.py中输入如下代码：
```python 3
def my_function():
    print("This is my function.")
    print("My function is so good!")


def my_add(x, y):
    return x+y
```
然后在main.py中导入该模块，即可使用my_module.py里的函数。
```python 3
import my_module

my_module.my_function()

a, b = 2, 3
result = my_module.my_add(a, b)
print(result)

"""
控制台输出：
This is my function.
My function is so good!
5

"""
```
我们可以仅仅导入其中一个函数，这样就不需要再使用模块名.函数名的样式，直接显式调用：
```python 3
from my_module import my_add

a, b = 2, 3
result = my_add(a, b)
print(result)
```

我们还可以使用as给模块或函数起别名：
```python 3
from my_module import my_add as ma
import my_module as mm

mm.my_function()

a, b = 2, 3
result = ma(a, b)
print(result)
```

## 模块的存储和导入（类）
同样地，我们可以把类也存储在模块中，比如我们在my_module.py中输入以下：
```python 3
class my_class:
    
    def __init__(self, user_input_data = 0):
        self.data = user_input_data
    
    def print_data(self):
        print("The data of this object is {}".format(self.data))
```
然后就可以在main.py中使用这个类了。
```python 3
import my_module as mm

an_object = mm.my_class(40)
an_object.print_data()
```

## 常用的Python库
咱们在编程时一般会用到的库有这些，并且我给出了网上的一些链接，告诉大家这些库有哪些函数和类可以使用：
1. math库：https://zhuanlan.zhihu.com/p/358932997
2. random库：https://blog.csdn.net/weixin_43509127/article/details/104203388
3. time库：https://zhuanlan.zhihu.com/p/111022726
4. PIL库：https://zhuanlan.zhihu.com/p/45326961
5. numpy库：https://www.runoob.com/numpy/numpy-tutorial.html
6. pandas库：http://c.biancheng.net/pandas/
7. matplotlib库：http://c.biancheng.net/matplotlib/
   
其中567三个库在后续机器学习中会使用到，到时也会跟大家简单讲解一下。

## 结语
没有，再见。