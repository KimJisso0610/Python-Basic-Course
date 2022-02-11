# 人工智能社团基础课——Python编程
# CH9 - 文件操作
## 前言
大家好，这一章我们来学习非常重要的内容。

有时我们需要使用Python来处理大量的数据，这些数据存储在文件里面，所以我们就需要使用Python来读取文件里的内容，有时还得把处理后的数据写入新的文件中。

所以这一章我们来学习文件操作，先简要介绍txt文件的读和写。然后介绍一些常用格式的文件的处理，可能需要安装一些新的库，如果忘记怎么安装的请倒退回上一章去看看。

## 读取txt文件

假如我们有一个pi.txt文件，里面的内容如下图：三行数字。（别问我为什么是ch1demo，忘记改名然后就懒得改了.....）

![avatar](/Python%20Basic%20Course/Picture/53.png)

然后我们在main.py里写入读取文件的代码，注意pi.txt和main.py必须在同一个目录下，才能使用相对路径。

```python 3
with open('pi.txt') as file:
    contents = file.read()
    print(contents)
```
运行main.py，我们就能看到控制台输出了pi.txt的内容。

大家一定会觉得，哇！好神奇！但是肯定不太理解这段代码的原理。且让我来给大家一一说明：

1. 首先解释一下绝对路径和相对路径：
   > 节选自：https://zhuanlan.zhihu.com/p/263756528
   > 
   > 绝对路径：目标文件在硬盘上的真实路径（最精确路径）
   > 
   > 举个栗子：找到文件，右键点击后打开属性，可以看到我把喜欢的封面'cover1.jpg'储存在了路径C:\Users\80975\OneDrive\Desktop\cover
   >
   > 那么_C:\Users\80975\OneDrive\Desktop\cover\cover1.jpg就是绝对路径
   >
   > ![avatar](https://pic2.zhimg.com/80/v2-d94ccf0e8dad8f473340271f5148ca91_720w.jpg)
   > 
   > 所以在html的图片引用中可以写为
   > C:\Users\80975\OneDrive\Desktop\cover\cover1.jpg" 
   >
   > 相对路径：相对于当前文件位置的路径
   >
   > 举个栗子：我不想用绝对路径，那么在html中要怎么写才能引用cover1.jpg呢？
   > 
   > 这里要介绍一个等级概念,目录的上级(父级)，同级，下级（子级）。从这里开始，我们管文件夹叫目录(directory)。
   >
   > 下级（子目录）：在web目录下，可以看到有一个用chrome打开的文件，我把它叫做test.html，那么test.html就叫做web目录的下级。
   >
   > 上级：web是test.html的上级目录。
   > 
   > 同级：web和cover1.jpg在同目录中，成为同级。
   
   如果main.py是pi.txt的上级，那么表示pi.txt存储在跟main.py同级的目录中，此时我们只需要从跟main.py同级的目录开始，一层一层往下级写，直到写到pi.txt为止。例如pi.txt的目录为"digit/p/pi.txt"，其中digit文件夹与main.py同级并且上级目录为ch1demo，则main.py内打开pi.txt就写```open('digit/p/pi.txt')```。

   如果main.py是pi.txt的同级，则为前面例子的情况。

   如果main.py是pi.txt的下级，如下面这种情况：

   ![avatar](/Python%20Basic%20Course/Picture/54.png)

   目录app与pi.txt同级，main.py是pi.txt的下级，且隔了两个目录，这时我们只需要按照图片里的方式即可，隔了几个目录就写几个../。

2. open()函数：函数参数为文件目录（字符串），以及模式（可选参数）。读取到文件后，将其转换为Python定义的文件类的一个对象，其中as后面为变量名，表示这个对象的名字叫做file。
3. with：在不再需要访问文件的时候将其关闭。如果不用，就需要手动输入close()函数来关闭文件。因为close()函数在程序有Bug时会出问题，所以用with关键字更好，而且省事。
4. read()函数：文件类的一个方法，读取文件的所有内容。同时，还有如下函数：readline()函数，读取文件的一行；readlines([size])，读取文件的多行，把每一行存到一个列表中，size不写则读取所有行。注意：使用readline或readlines时，读取文件的一行，末尾会有带有一个换行符，可以使用strip()函数去掉。

接下来我们来处理从文件里得到的内容，我们把三行数字整理为一行并输出为一个浮点型，代码如下：
```python 3
with open('pi.txt') as file:
    lines = file.readlines()

    # 处理换行符
    for i in range(len(lines)):
        lines[i] = lines[i].strip()

    # 将字符串连接起来
    string = ''
    for line in lines:
        string += line

    # str转换为float
    pi = float(string)
    print(string)
    print(pi)
```
这时你会发现float有精度问题，大家思考一下怎么解决，当然直接百度也可以出结果。

## 写入txt文件
首先我们使用open()函数打开一个文件，如果按照上面的方法写，默认为只读模式，不可以写入。所以，我们需要追加一个可选参数。

还是上面那个例子，我们想把string写入一个pi2.txt文件里，我们可以这样写代码：
```python 3
with open('pi2.txt', 'w+') as file:
    file.write(string)
```
'w+'表示读取和写入模式，即你可以对文件又读取又写入。open()函数会自动创建文件如果该文件不存在，但是如果存在，写入操作会覆盖掉原有的内容。

如果我们想把string加到pi.txt的第四行怎么办？我们可以使用'a+'，表示追加和读取模式，此时一打开文件，文件的指针（相当于光标）就指向文件结尾。上述操作的完整代码如下：
```python 3
with open('pi.txt') as file:
    lines = file.readlines()

    # 处理换行符
    for i in range(len(lines)):
        lines[i] = lines[i].strip()

    # 将字符串连接起来
    string = ''
    for line in lines:
        string += line

    # str转换为float
    pi = float(string)
    print(string)
    print(pi)

with open('pi.txt', 'a+') as file:
    file.write('\n'+string)

with open('pi2.txt', 'w+') as file:
    file.write(string)
```
运行结束后，我们可以看到pi2.txt文件被成功创建，pi.txt文件末尾也成功追加了数字。

![avatar](/Python%20Basic%20Course/Picture/55.png)

注意，write()函数不像print()函数会自动换行，所以要追加到新的一行的话，要在字符串前面加上换行符'\n'。

注意，write()函数内必须为字符串才能写入！

## Office Word文件的操作
请先安装库python_docx！

接下来，我们简要地学习docx文件的读取。

我们有一个与main.py同级的文件poem.docx，使用如下代码读取它的内容：

```python 3
from docx import Document

document = Document('poem.docx')

for paragraph in document.paragraphs:
    print(paragraph.text)
```

我们从docx库中导入Document类，然后创建一个对象，构造时只需要传入docx文件的路径即可。document.paragraphs存储了docx文件内的所有段落（它是Document类的一个属性），我们可以使用for...in...循环去获取每个段落，但是这些段落仍然是一个类的对象，它有属性text，存储段落中的内容。于是，我们可以这样逐行打印docx文件里的所有段落。

接下来我们简要地学习docx文件的写入。

![avatar](/Python%20Basic%20Course/Picture/56.png)

我们在原来的poem.docx上追加内容，在最后一段添加时间2022-02-10，操作如下：

```python 3
from docx import Document

document = Document('poem.docx')
document.add_paragraph('2022-02-10')
document.save('poem.docx')
```
之后打开文件，我们可以看到：

![avatar](/Python%20Basic%20Course/Picture/57.png)

我们只需要弄到这里就够了。关于docx库的更多，可以参考这些：
1. https://www.jianshu.com/p/7d2fcf976914
2. https://www.osgeo.cn/python-docx/
   
## Office Excle文件的操作
请先安装库pandas！

假如我们有一个表格student source.xlsx，存储了一些学生的成绩：

![avatar](/Python%20Basic%20Course/Picture/58.png)

接下来我们尝试读取这些数据：
```python 3
import pandas as pd

# 打开工作表，默认为第一个
sheet = pd.read_excel('student source.xlsx')

# 直接输出该工作表
print(sheet)
```

![avatar](/Python%20Basic%20Course/Picture/59.png)

read_excel()函数默认读取第一个工作表，如果需要读取其他工作表，可以添加参数sheet_name='工作表名'。

有关Excel的操作先讲到这里，因为后续我们也会讲Pandas的操作，所以我们留在到时一起说。

其实刚开始我是想用xlrd和xlwt的，但是由于版本太高，导致打开xlsx文件失败......，有关这两个库的内容大家可以自行去网上搜索。

## Json文件的操作
Json文件的内容类似于Python中的字典，接下来我们尝试使用Python创建一个Json文件并读取它的内容。

```python 3
import json

student_score = {'Alice': 100, 'Bob': 99, 'Cindy': 98, 'David': 97}

with open('student score.json', 'w+') as json_file:
    json.dump(student_score, json_file)

with open('student score.json') as json_file:
    a_dict = json.load(json_file)
    print(a_dict)
```

## 目录操作

下面列举一些常用的目录操作，需要导入os库与shutil库。

 1. 得到当前工作目录，即当前Python脚本工作的目录路径: os.getcwd()
 2. 返回指定目录下的所有文件和目录名:os.listdir()
 3. 函数用来删除一个文件:os.remove()
 4. 删除多个目录：os.removedirs（r'c:\python'）
 5. 检验给出的路径是否是一个文件：os.path.isfile()
 6. 检验给出的路径是否是一个目录：os.path.isdir()
 7. 返回一个路径的目录名和文件名:os.path.split() 例如 os.path.split('/home/swaroop/byte/code/poem.txt') 结果：('/home/swaroop/byte/code', 'poem.txt')
 8.  分离扩展名：os.path.splitext()
 9.  获取路径名：os.path.dirname()
 10. 获取文件名：os.path.basename()
 11. 重命名：os.rename（old， new）
 12. 创建多级目录：os.makedirs（r"c:\python\test"）
 13. 创建单个目录：os.mkdir（"test"）

例如我们要列举出ch1demo目录下目录树，
```python 3
# 这是曹冬林老师课件上的代码
import os


def list_files(startpath):
    for root, dirs, files in os.walk(startpath):
        # root是字符串，dirs、files均为列表
        level = root.replace(startpath, '').count(os.sep)
        # os.sep得到路径的分隔符“\\”,level表示路径中“\\”的个数，即路径的深度
        dir_indent = "|   " * (level) + "|-- "
        file_indent = "|   " * (level + 1) + "|-- "
        if not level:
            print('{}'.format(startpath[0]))  # 输出盘符
            print('|--{}'.format(startpath[3:]))  # 输出目录名
        else:
            print('{}{}'.format(dir_indent, os.path.basename(root)))
            # os.path.basename(root)得到路径root的最后一个名字
        for f in files:
            print('{}{}'.format(file_indent, f))


startpath = 'E:\Project\Python Project\ch1demo'
list_files(startpath)
```
结果如下：
```
"D:\Application\Anaconda 3\python.exe" "E:\Project\Python Project\ch1demo\main.py"
E
|--Project\Python Project\ch1demo
|   |-- main.py
|   |-- my_module.py
|   |-- pi.txt
|   |-- pi2.txt
|   |-- poem.docx
|   |-- student score.json
|   |-- student source.xlsx
|   |-- .idea
|   |   |-- .gitignore
|   |   |-- ch1demo.iml
|   |   |-- misc.xml
|   |   |-- modules.xml
|   |   |-- workspace.xml
|   |   |-- inspectionProfiles
|   |   |   |-- profiles_settings.xml
|   |-- app
|   |   |-- python
|   |-- __pycache__
|   |   |-- my_module.cpython-39.pyc

Process finished with exit code 0

```
理解这段代码可能有点难，我们这样，用一个新的例子：从ch1demo中读取所有txt文件的内容并输出。
```python 3
import os

path = 'E:\Project\Python Project\ch1demo'

def scan_dir(path):
    for p in os.listdir(path):
        if os.path.isfile(p) and os.path.splitext(p)[1] == '.txt':
            with open(os.path.dirname(p) + p) as file:
                print(file.read())
        elif os.path.isdir(p):
            scan_dir(os.path.dirname(p) + p)

scan_dir(path)
```
这里用到了函数递归。列举当前目录下的内容，然后逐个遍历，如果是目录，就开始新的一轮扫描，如果是文件且后缀为.txt，就输出文件内容。

## 结语
本章内容多且复杂，大家要好好消化。课上讲的东西比较少，大家感兴趣的话可以自己查资料学习。未来大家写代码都需要查找大量资料。

我还记得有一次我写一个程序，不停地查资料，结果写完关机的时候发现我的浏览器打开了近40个窗口hhhhhh。

下一章就是最后一章了，比较简单。教大家使用Pycharm进行调试，让大家在运行程序时查看哪一步出问题，并且实时监控变量的值，很有用，大家学起来！