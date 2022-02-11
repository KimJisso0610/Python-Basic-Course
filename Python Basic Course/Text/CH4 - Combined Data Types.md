# 人工智能社团基础课——Python编程
# CH4 - 组合数据类型
## 前言
本章讲组合数据类型，是Python里基础的四个类型，包括列表、元组、集合、字典。

## 列表（list）
列表类型类似于C语言里的数组，它的定义方法为：列表名称 = [<元素>]，例如List = [1, 2, 3, 4, 5]。其中1，2，3，4，5分别是列表中的第0、1、2、3、4个元素，可以用下标运算符[]获取List中的元素。

我们可以创建空列表，即[]或[None]。

Python中的组合数据类型实际上是广义表，每个元素的类型可以不一样，可以是int,float,str，甚至list,tuple,set,dict等，例如：
```python 3
List = [1, "Python", [2,3,4], True, {A: 4, B: 6}, 1.11155]
```
我们可以使用list()函数，将字符串、元组或集合转换为列表。
```python 3
string = "Python"
List = list(string)
print(List)

'''
程序输出：
['P', 'y', 't', 'h', 'o', 'n']

'''
```
有关列表的一些操作：
1. List[i]：取List中的第i个元素。假如List长度为length，那么0到length-1代表着List中的第1、2、3、......、length个元素。-1到-length代表着List中的倒数第1、2、3、......、length个元素。
   ![avatar](/Python%20Basic%20Course/Picture/13.png)
2. List[i:j:k]：列表切片，返回一个列表，从i到j（不包括j）以k为步长，i不写默认为0，j不写默认为len(List)，k不写默认为1。
   ![avatar](/Python%20Basic%20Course/Picture/14.png)
3. 其他：![avatar](/Python%20Basic%20Course/Picture/15.png)
   
## 元组（tuple）
元组类型与列表类型的唯一区别就是：元组类型一旦被定义，就不可以进行元素改变（例如插入、删除、修改等），它的定义方式为：元组名称 = (<元素>)。
![avatar](/Python%20Basic%20Course/Picture/16.png)

同样地，我们可以创建一个空元组，也可以使用tuple函数将字符串、列表或集合转换为元组。

元组的一些操作：
![avatar](/Python%20Basic%20Course/Picture/17.png)

大家注意，这些操作在list中同样适用。

## 集合（set）
集合类型与列表类型的唯一区别就是：集合里的元素具有互异性，即不会出现相同的元素，定义方法为：集合名称 = {<元素>}；

创建空集合的方法为：Set = set()，即使用set()，而不是{}，因为{}代表创建一个空字典。

可以用set()函数将list/str/tuple类型转化为set类型，常用于列表中的重复元素去重，很方便。

![avatar](/Python%20Basic%20Course/Picture/18.png)

注意：使用set()函数后可能会打乱原来的顺序。

集合的一些操作：
![avatar](/Python%20Basic%20Course/Picture/19.png)

## 字典（dict）
字典可以看作一种映射。字典中每一个元素都有一对键值对构成，键key可以当作自变量理解，值value可以当作因变量理解。Dict = {“键1”:“值1”, “键2”:“值2”, ……}。

创建一个空字典的方法：Dict = {}。

而当我们使用字典进行索引取值时，运算符内应该是key的内容。

![avatar](/Python%20Basic%20Course/Picture/20.png)

字典的一些操作：
![avatar](/Python%20Basic%20Course/Picture/21.png)

## 结语
本章主要介绍的是4种基本的组合数据类型。介绍的东西比较少，但是实际应用起来却可以有很多玩法。比如创建一个矩阵，就可以使用列表嵌套，列表中的每个元素都为列表，这样就是一个二维矩阵。外面再嵌套一层列表，就是三维矩阵。

这一章务必要多多练习，才能很好地掌握元组的应用。大家去PTA里刷起来！
![avatar](/Python%20Basic%20Course/Picture/22.png)