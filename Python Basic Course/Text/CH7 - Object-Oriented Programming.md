# 人工智能社团基础课——Python编程
# CH7 - 面向对象编程
## 前言

接下来我们进行第七章的学习，从第六章来的可以缓一缓，第六章确实是比较难理解的东西。

这一章，需要把你们的男朋友/女朋友叫过来，毕竟是，面向对象编程（bushi）。

什么？你没对象？那直接去第八章啦~（别真的跑啊）

开个玩笑。

## 类和对象的概念
类是一个抽象数据类型，用于存储数据与方法，例如int类、list类等，用户可以自己创建一个类，需要用关键字class。

以类为模板创建一个个对象的过程称为类的实例化，这些对象又叫做实例，例如之前我们定义a_list = [1, 2, 3, 4, 5]，其中a_list就可以叫做list类的一个实例（或一个对象）。

面向对象编程的概念在此不多说，如果之前没有接触过，可以去查阅其他资料。

## 类的创建与实例化
跟定义函数差不多，使用关键字class，例如：
```python 3
class Student:
    ......
```
而创建类的对象又叫类的实例化。模板为实例名称=类名(<参数表>)，例如上面的Student类，我们可以创建一个对象：
```python 3
s = Student()
```
由于目前不需要传任何参数，所以创建一个Student类就写一个括号就行。

## 类的属性与方法
属性：例如在前面的Student类中，我们可以在类里面定义学生的姓名，学号，成绩等，这些叫做属性。属性分为类属性和实例属性。

方法：例如在前面的Student类中，我们可以在类里面定义获得学生的成绩，更改学生的姓名等操作，这些叫做方法。方法分为类方法和实例方法。

## 定义实例属性
我们怎么定义实例属性呢？这就需要用到构造函数了。格式为def \_\_init\_\_(<参数表>)，例如：
```python 3
class Student:
    
    def __init__(self, name, number, score=0):
        self.name = name
        self.number = number
        self.score = score
        self.age = 18
        self.city = "Xiamen"
```
在实例中，定义的每个函数都需要带有self参数，用于在函数体内部指明是该实例的属性（方法即为self.属性名）。

在上面的例子中，一个实例有如下属性：name，由创建实例时传入且必须传入；number，由创建实例时传入且必须传入；score，可由创建实例时传入，不传入则默认为0；age，固定为18除非接下来定义方法去修改；city，固定为"Xiamen"除非接下来定义方法去修改。

创建实例时，以下两个都是正确的：
```python 3
student1 = Student("Alice", 202201, 100)
student2 = Student("Bob", 202202)  # 默认Bob为0分
```

## 定义类属性
类属性（相当于C++的静态数据成员）的定义：在__init__函数之外定义，这个属性是所有类的实例共享的，比如在Student类内定义一个类属性average，存储所有学生的平均分，每个实例共享之。
```python 3
class Student:
    
    count = 0  # 记录人数
    average = 0.0  # 记录平均分

    def __init__(self, name, score=0):
        self.name = name
        self.score = score
        self.age = 18
        self.city = "Xiamen"
        Student.count += 1
        Student.average = (Student.average+score)/Student.count
```

类属性可以直接通过类名.属性名访问，也可以通过实例.属性名访问。

例如，创建两个类后，我们可以获得学生的平局分。

```python 3
student1 = Student("Alice", 120)
student2 = Student("Bob", 100)
print(Student.average)
# 用student1.average或student2.average也一样
```

## 定义实例方法
跟定义函数一样，不过第一个参数必须是self。
```python 3
class Student:
    
    def __init__(self, name, score=0):
        self.name = name
        self.score = score
        self.age = 18
        self.city = "Xiamen"
    
    def get_score(self):
        print("{}'s score is {}".format(self.name, self.score))
```
在实例中使用方法：
```python 3
student1 = Student('Alice', 120)
student1.get_score()

"""
控制台输出：
Alice's score is 120

"""
```
## 定义类方法
在函数定义前用@classmethod绑定，函数的第一个参数必须是cls，例如定义一个打印学生平均分的类方法。
```python 3
class Student:
    
    count = 0  # 记录人数
    average = 0.0  # 记录平均分

    def __init__(self, name, score=0):
        self.name = name
        self.score = score
        self.age = 18
        self.city = "Xiamen"
        Student.count += 1
        Student.average = (Student.average+score)/Student.count
    
    @classmethod
    def get_average(cls):
        print("The average is {}".format(cls.average))

student1 = Student("Alice", 120)
student2 = Student("Bob", 100)
Student.get_average()
```
同样，实例也可以使用类方法。

学会了类方法后，我们可以这样改写Student类：
```python 3
class Student:
    count = 0  # 记录人数
    average = 0.0  # 记录平均分

    def __init__(self, name, score=0):
        self.name = name
        self.score = score
        self.age = 18
        self.city = "Xiamen"
        Student.calculate_average(score)
    
    @classmethod
    def calculate_average(cls, score):
        Student.count += 1
        Student.average = (Student.average+score)/Student.count

    @classmethod
    def get_average(cls):
        print("The average is {}".format(cls.average))


student1 = Student("Alice", 120)
student2 = Student("Bob", 100)
student1.get_average()
```

## 运算符重载
我们之前学过，对于+号运算符，如果是两个int类型相加，就是进行普通的整数相加，如果是两个str类型相加，就是将两个字符串连接起来，实际上str类型中对+号运算符进行了重载，改变了其功能。

Python的运算符重载与C++不同，重载运算符需要定义运算符对应的函数方法名，下面列举一些常用运算符的方法名：
![avatar](/Python%20Basic%20Course/Picture/42.png)

给大家一个例子：定义一个复数类，重载+与*运算，并定义复数的格式化输出函数print()。

这里我为什么直接贴图呢，一个是因为我懒（理直气壮）。还有我希望大家自己打一遍代码，增强记忆与理解。

类的定义：

![avatar](/Python%20Basic%20Course/Picture/43.png)

实例的创建：

![avatar](/Python%20Basic%20Course/Picture/44.png)

## 访问限制
在类的外部，我们可以轻易修改一个类或实例的属性：

``` python 3
class DemoClass:
    def __init__(self):
        self.data = 100

an_object = DemoClass()
print(an_object.data)

an_object.data = 50
print(an_object.data)
```
在实际应用中，我们并不希望外部能直接更改类或实例的属性，以避免运行产生错误。此时可以在属性前加入下划线，这样外部就不能访问了。
```python 3
class Student:
    def __init__(self, name, score = 0):
        self.__name = name
        self.__score = score
    
    def print(self):
        print(self.__name)

student_a = Student('Alice', 120)
student_a.name = 'Bob'
print(student_a.name)
student_a.print()

"""
控制台输出：
Bob
Alice

"""
```

有同学可能就会有疑问了，这个结果是怎么出来的？

首先，在属性名前加两个下划线，它就变成了私有的，外部不能直接访问。而```student_a.name = 'Bob'```这一步实际上是新定义了一个名为student_a.name的变量，所以输出结果是Bob。

在Python中，访问了私有的实例属性不会报错，而是将其当作一个新定义的变量名来看待。

类或实例的属性实际上有三个类型：分别为公有的(public)，受保护的(protected)，私有的(private)。定义受保护属性只需在属性名前加入一个下划线即可，除了类与其派生类可以访问，其他部分不可访问；定义私有属性只需在属性名前加入两个下划线即可，除了类自身可以访问，其他部分不可以访问。其余属性均为公有属性（包括名称前后都有下划线的属性）。

## 类的继承
在定义一个新类时，可以直接从原有的类中复制（继承）其属性和方法。其中原来的类叫父类或基类，新定义的类叫做子类或派生类。

继承的方法：class 派生类名(基类名1, 基类名2, …):

注意基类的顺序，在派生类继承基类的属性时，如果基类1和基类2都有共同的属性或方法名，派生类优先继承前者的。大家可以把下面的代码copy到IDE上运行。
```python 3
class Father:
    def __init__(self):
        self.name = "father"

class Mother:
    def __init__(self):
        self.name = "mother"

class Son1(Father, Mother):
    def print(self):
        print(self.name)

class Son2(Mother, Father):
    def print(self):
        print(self.name)

a = Son1()
b = Son2()
a.print()
b.print()
```
给派生类添加额外属性时，要声明对基类__init__的调用。

方法：super().\_\_init__(<参数表>)
```python 3
class Father:
    def __init__(self, data3):
        self.data1 = 10
        self.data2 = 100
        self.data3 = data3

class Son(Father):
    def __init__(self, data3, data5):  # 参数表中要带上传入基类__init__()的参数
        super().__init__(data3)
        self.data4 = 1000
        self.data5 = data5

```

哈哈哈哈哈，例子又来咯！

定义一个员工类，其属性有姓名，年龄，性别。由其派生出一个经理类，额外添加职位属性。二者都有一个同样的方法名print。

类的定义部分：

![avatar](/Python%20Basic%20Course/Picture/45.png)

实例的创建部分：

![avatar](/Python%20Basic%20Course/Picture/46.png)

## 类的多态性
当基类和派生类拥有同样的方法名时，实际上互相不冲突。在实例中，使用实例方法时调用本类的方法。如上面的例子，a_manager.print()调用的是Manager类的print()，而an_employee.print()调用的是Employees类的print()，这就是类的多态性。

现在我们定义一个打印信息函数print_information，传入的参数是一个类，函数内部调用类的print()方法。于是乎在一个数据库中，对于不同类的实例，print_information函数就能根据传入参数的类型来调用每个实例所属类的print()方法，这就是多态的优势所在。

## 结语
本章最重要的部分就是类的定义和对象（实例）的创建两个部分。并且学会实例属性和实例方法的定义。如果你一时消化不了，那类属性、类方法和继承这一块可以暂时先不去理解。