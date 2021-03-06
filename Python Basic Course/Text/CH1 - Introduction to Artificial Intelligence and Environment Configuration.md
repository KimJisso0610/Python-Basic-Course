# 人工智能社团基础课——Python编程
# CH1 - 人工智能简介与环境配置
## 前言1
各位社团成员大家好！经过一年的沉淀，社团基础培训课将以新的面孔与大家见面。

先自我介绍一下，我叫卢逸飞，XMU人工智能系2019级本科生。也是社团创始人和第一第二届的社长。编写这个教程我会使用大量比较轻松、吐槽的语句，让看教程的你们有一种在和我对话的感觉，这样看起来就不会那么生硬、乏味。

今年，我负责的基础课程培训有三个部分，Python编程、机器学习和深度学习。我先起草一下大纲，然后交给一些大佬润色，最后发布给大家，欢迎大家积极帮忙勘误。我们在下个学期（也就是2021-2022年春季学期）计划每两周举办一次讲座培训，内容与编写的教程对应。大部分都是我来给大家讲述，有不完美的地方欢迎大家多提意见！

除了我负责的三个部分以外，还有一些硬件和软件的教程，由其他同学负责，欢迎大家多多学习。在空余的时间内，学到感兴趣的东西。~~卷死其他人！（误）~~

之前大家约定一起使用MarkDown语法来写教程，不知道其他人有没有用，我是感觉挺方便的，所以之后我的教程将全部都是.md文件。大家如果不知道怎么预览的，可以下载MarkDown编辑器来看。我的建议是用VS Code。

## 前言2
接下来给大家介绍一下这一个系列的课程，本系列为Python编程。大家都知道，入门这一行，那得必须会编程，所以我们将从编程基础给大家上起。而选择Python的原因大家都心里有数，它不仅是人工智能语言，而且简单、易学、配置方便。学会了Python编程以后，C++、Java等语言也不在话下了。

编程基础一般都涵盖以下：首先是最简单的输入输出（谁学一门语言不是从`Hello World`开始的呢）、然后到认识变量以及变量类型、到程序结构、到函数、然后指针。

不过恭喜大家的是，Python语言不需要再学指针！这个当时狂虐大一新生的东西（以及后续的链表）不会在这里出现！

但是我们将会学习一些Python的高级语法，像列表生成式、匿名函数等等，这些又是C语言没有的东西。然后我们还将学习OOP（面向对象程序设计）的一些基础知识，还有正则表达式，最后学习一些常用的库。（不知道什么是库？那先保留这个疑问，后面你们就会知道啦）

## 前言3
（怎么还有前言！）

是的，还没完。

我还要继续唠叨几句（《几  句》）。

我写的教程，是面向稍微有一点编程基础的同学的，比如有学过C语言、VB之类的。如果你一点语言基础都没有，上课或者看教程可能会有点跟不上。没关系，这里给大家推荐一些书和学习网站。大家如果在上课或者看教程时有疑问，可以翻阅一下资料或者百度一下有疑问的地方。

学习网站：
1. 中国大学MOOC《Python语言程序设计》（北京理工大学嵩天）https://www.icourse163.org/course/BIT-268001
2. 中国大学MOOC《Python程序设计》（浙江大学陈春晖、翁恺、季江民）https://www.icourse163.org/course/ZJU-1206456840
3. 廖雪峰的官方网站：https://www.liaoxuefeng.com/wiki/1016959663602400
4. 在线程序设计平台（在线练习）——拼题A（PTA）https://pintia.cn

书:

![avatar](/Python%20Basic%20Course/Picture/1.png)

书的资源在社团群文件里有。这本书是我们专业课内的Python编程课使用的书，感觉还不错，适合新手入门。

我大一初学Python用的是廖雪峰的官方网站，他写的内容有点难，适合有编程基础的人看。除此之外，MOOC上的课程也很不错。

编程也是理科，光学不做等于白学。所以大家学了语法之后一定要多做对应的练习。我推荐大家使用拼题A，在上面注册一个账号，然后选择Python程序设计，完成上面的练习。每一章内容的最后，我也会给大家划对应的PTA的题。然后题的AC代码汇总也在群文件里有，如果实在无法通过，可以查看一下我的代码。

好的，大家一定嫌我啰嗦得烦了，那我们接下来就开始课程里的内容吧！

## 1.1 人工智能简介

其实说实话，人工智能是什么？怎么定义？这个我也不清楚。那我简介一些什么呢？其实就是给大家谈一谈人工智能的学习路线。不然到头来大家一股脑跟着学，却不明白我们学什么？为什么要学？

我在第二次社员大会上有给大家画过一个图，大家应该还记得吧：

![avatar](/Python%20Basic%20Course/Picture/2.png)

对于一个现实中的问题，可以将其分类为简单为题和复杂问题，简单问题简单分析，复杂问题复杂分析。简单分析可以采用数据分析的方法，而复杂分析就可以采用AI来解决问题。

接一下我将引用 https://easyai.tech/ai-definition/ai/ 上的一些原话给大家介绍AI。

> 传统软件与人工智能的区别：
> 
> 传统软件是「if-then」的基本逻辑，人类通过自己的经验总结出一些有效的规则，然后让计算机自动的运行这些规则。传统软件永远不可能超越人类的知识边界，因为所有规则都是人类制定的。简单的说：传统软件是「基于规则」的，需要人为的设定条件，并且告诉计算机符合这个条件后该做什么。这种逻辑在处理一些简单问题时非常好用，因为规则明确，结果都是可预期的，程序员就是软件的上帝。但是现实生活中充满了各种各样的复杂问题，这些问题几乎不可能通过制定规则来解决，比如人脸识别通过规则来解决效果会很差。
> 
> 人工智能现在已经发展出很多不同分支，技术原理也多种多样，这里只介绍当下最火的深度学习。深度学习的技术原理跟传统软件的逻辑完全不同：机器从「特定的」大量数据中总结规律，归纳出某些「特定的知识」，然后将这种「知识」应用到现实场景中去解决实际问题。这就是人工智能发展到现阶段的本质逻辑。而人工智能总结出来的知识并不是像传统软件一样，可以直观精确的表达出来。它更像人类学习到的知识一样，比较抽象，很难表达。
> 
> ![avatar](https://easy-ai.oss-cn-shanghai.aliyuncs.com/2020-01-02-ailuoji.png)

由此，我们要把人工智能最基础的两个精华学习了，才能入门。一个是机器学习，一个是深度学习。这两个课程的具体内容，也将在后续介绍。把这两个基础打好，你还要掌握如下东西：

1. 编程语言（最好是Python）；
2. 数学基础（微积分、线性代数、概率论与数理统计）。

没错，还是有你逃不掉的数学。但是没有办法，它就是需要数学基础。

学习完基础之后，你就可以尝试人工智能的各个领域：

* 计算机视觉
* 模式识别
* 智能机器人（智能控制）
* 自然语言处理
* 专家系统
* ......

有关人工智能的更多，比如伦理道德、发展趋势等内容，欢迎大家到上面提到的网站去看，我这里就不介绍那么多了。接下来，我将带领大家入门Python语言。相信已经有很多同学开始跃跃欲试了。

打住打住！

首先，一个问题：你在哪里写代码？你写了代码之后如何运行查看结果？（好像是两个问题，dbq.....）

所以，先别急，我们要先做好这一步。好在，我们有IDE。

IDE，全称为Integrated Development Environment，中文名为集成开发环境。你可以在IDE上完成编写代码、编译运行、查看输出结果等操作，有一些功能完善的IDE，可以进行语法检查、代码调试等操作。所以，我们可以安装IDE。

## IDE的安装
Python语言的IDE有很多：

>1. IDLE：是一个纯 Python 下使用 Tkinter 编写的相当基本的 IDE，具备基本的IDE的功能，是非商业Python开发的不错的选择。
>2. Pycharm：是一种Python IDE，带有一整套可以帮助用户在使用Python语言开发时提高其效率的工具。此外，该IDE提供了一些高级功能，以用于支持Django框架下的专业Web开发。
>3. Visual Studio：开源IDE工具。（当然VS Code也很不错），它可以作为很多编程语言的IDE，对于编程专业的学生很合适。
>4. Anaconda：Anaconda适用于科学计算和数据分析，开源免费。
>5. Eclipse：本身只是一个框架平台，但是众多插件的支持使得Eclipse拥有其他功能相对固定的IDE软件很难具有的灵活性。许多软件开发商以Eclipse为框架开发自己的IDE。

当然还有其他的，不在此一一列举。去年我们上Python编程课的时候推荐大家使用的是IDLE，因为学一点Python编程基础不需要多高级的IDE。但是今年，我还是建议大家使用Pycharm+Anaconda，这不仅是为接下来的机器学习、深度学习的编程环境配置做准备，也可以让大家感受一下jetbrains公司的IDE的强大。

由于我已经安装过了，我就不在此写安装教程，直接给大家CSDN上的。到上课的时候，我会一步一步教大家进行安装，因为新手真的超级容易踩雷！

1. IDLE安装：https://www.bilibili.com/video/BV1r5411n7FE?p=2
2. Pycharm和Anaconda安装：https://www.bilibili.com/video/BV1r5411n7FE?p=3

说一下，Pycharm和Anaconda安装的那个视频里有一点问题，Anaconda安装那里写有Python 3.8不是因为它需要安装Python对应的版本，而是安装后的Anaconda里面有这个版本的Python。

安装完之后，大家可以在安装Anaconda的文件夹目录下查看，给大家展示一下我的：

![avatar](/Python%20Basic%20Course/Picture/3.png)
![avatar](/Python%20Basic%20Course/Picture/4.png)

大家只需要记住两个，一个是第一张图的envs文件夹，一个是第二张图的python（实际上是python.exe）。envs文件夹是存放虚拟环境的文件夹，而python.exe就是用来运行.py代码文件的，我们称之为解释器。

这里又提到一个概念，叫做虚拟环境。我们为什么会用到它？首先，我在上面（即第二张图）提到的解释器可以叫做默认解释器（或者基本解释器），称它在base环境下（又叫默认环境或者基本环境）。这个默认解释器的版本号是Python 3.9。但是未来我们安装库时，这个库需要的解释器版本是Python 3.7，这时我们安装在默认环境下，就会报错。所以，我们可以创建一个虚拟环境，创建时制定Python的版本为3.7，然后把库安装在虚拟环境中就可以了。所以envs的结构大致是这样的：

```
--envs
    --env_name_1
        --python.exe
        --[others]
    --env_name_2
        --python.exe
        --[others]
    --......
```

也就是说，每个虚拟环境下都会有一个解释器。这样你就可以使用不同版本的Python解释器去运行代码。

## Hello World
接下来就是振奋人心的时刻，我们终于可以开始写代码了！

大家务必遵循以下步骤，以免出现差错。

1. 打开Pycharm，创建一个Project。选择一个Project的存放位置（建议最好不要放C盘！）。即在下图的Location那里修改。然后还要配置Python解释器，我们选择Previously configured interpreter，即选择现有的解释器。此时你们的图跟我的应该不一样，因为还要继续配置。大家点击Interpreter那一栏最右边的三个点，然后进入下一步。
   ![avatar](/Python%20Basic%20Course/Picture/5.png)

2. 左边选择Conda Environment，即选择Conda环境。然后点击Interpreter右边的三个点，找到你的Anaconda安装的地方（如果刚刚安装在C盘的同学，我估计你找不到了吧~），我在上一节是不是说过base下有一个解释器python.exe？选择它。然后点击OK，下面那个Conda execulable它会自动找到。然后就配置完成了。再点击OK，应该就跟上面那张图一样了。
   ![avatar](/Python%20Basic%20Course/Picture/6.png)

3. 点击Create创建，然后在main.py里面输入：
   
   ```python
   print("Hello World")
   ```
   点击右上角的三角形按钮（运行），查看运行结果：
   ![avatar](/Python%20Basic%20Course/Picture/7.png)
   
   然后窗口下方就会弹出控制台，运行，并显示结果。

至此，你成功完成了代码文件的创建与运行！未来的编程操作都是如此，接下来我就会给大家讲解Python的语法！