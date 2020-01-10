---
title: python语言基础要素
date: 2019-11-29 10:14:11
tags:
- pandas
- python
- 数据处理
categories:
- Python
mathjax: false
---

简单了解一下数值、字符串、正则表达式与模式匹配、日期、列表、元组、字典、控制流等概念

## 数值

python中常用的数值类型主要有：整数、浮点数、长整数和复数

### print语句中的.format

format函数中两个比较重要的 符号：`{}`和`:`

- `{}`是一个占位符，表示这里将要传入print语句一个具体的值，可以按照默认顺序接受也可以设定接收指定位置的数据；
- `:`是用来分隔传入的值和它的格式。
<!--more-->

具体数字格式化以及使用实例参考：[python format 格式化函数](https://www.runoob.com/python/att-string-format.html)

需要知道的是，数值处理时会用到几种标准库模块和内置函数与模块来进行常见的数学计算。其中，标准库模块需要引入才能使用，比如，想要使用`math`模块中的一些函数：`exp`、`log`、`sqrt`，需要`from math import exp, log, sqrt`。

## 字符串	

字符串可以包含在单引号、双引号、3个单引号或者3个双引号之间。

用来管理字符串的标准模块、内置函数和操作符也有很多，常用的操作符和函数包括：`+`、`*`、`len`。

处理字符串的一个常用标准库模块是string。在string模块中可以使用多个函数，如：`split`、`join`、`strip`、`replace`和`lower、upper、capitalize`等来有效管理字符串。

### 字符串与引号

#### 单引号、双引号

如果想要print输出`I'm enjoying learning python`这句话，那么单引号，或者双引号的如法区别如下：

- `print("Output #14: {0:s}".format('I\'m enjoying learning Python.'))    `
- `print("Output #14: {0:s}".format("I'm enjoying learning Python."))    `

即，如果使用单引号来包含z这个字符串的话，就不需要在`"I'm"`的单引号前面使用反斜杠了。

#### 长字符串的换行

使用反斜杠`\`对长字符串进行换行处理，需要注意的是：

- 反斜杠必须是每一行最后一个字符

如果意外按下一个看不见的空格键，脚本就会抛出语法错误，不能正常运行

#### 三个单引号和三个双引号

使用三个单引号或者三个双引号，就是为了避免使用反斜杠对长字符串进行分行的，但是它们之间的的分行效果也有差异：

- 反斜杠换行：即使在print中换行了，输出在屏幕上长字符串仍然是一行
- 三个单引号或者三个双引号换行：在print中式如何换行的，输出在屏幕上就是怎么换行的

### 字符串的一些操作符和内置函数

#### +操作符

+操作符是将两个z字符串按照原样相加，所以如果想要连接两个字符串成一个句子的话，需要注意在连接出加上空格

#### *操作符

\*操作符是将字符串重复一定的次数，格式也比较简单，例如`"this is a string"*4`

#### 内置函数len
内置函数len用来确定字符串中字符的数量，它会将空格和标点符号也计算在内

### string模块中的一些函数
#### split
#### join
#### strip
#### replace
#### lower、upper、capitalize

## 列表list

### 创建列表

用方括号创建列表，用`len()`计算列表中元素的数量，用`max()`和`min()`找出最大值和最小值，用`count()`计算出列表中某个值出现的次数

### 列表索引值

使用列表索引值可以访问列表中的特定元素，其中[0]是第一个元素，[-1]是最后一个元素

### 列表切片

使用列表切片访问列表元素的一个子集，从开头开始切片，可以省略第一个索引值，一直切片到末尾们可以省略第二个索引值，例如：

~~~python
a_list = [1, 2, 3, 4]
print("{}".format(a_list[0:2])) # 1，2 
print("{}".format(a_list[:2]))# 1，2
print("{}".format(a_list[1:3]))# 2，3
~~~

### 列表复制

使用`[:]`复制一个列表，例如，下文中复制列表a_list中的内容给a_new_list，语句为：`a_new_list = a_list[:]` 

### 列表连接

使用`+`将两个或者更多个列表连接起来 :`a_longer_list = a_list + another_list` 

### 使用in和not in

使用`in`和`not in`来检查列表中是否有特定元素：`a = 2 in a_list`或`b = 2 not in a_list`，这些语句的返回值是`True`或者`False`

### 追加、删除和弹出元素

- 使用`append()`向列表末尾追加一个新元素；

- 用`remove()`从列表中删除一个特定元素；

- 使用`pop()`从列表末尾删除一个元素；

### 列表反转

使用`reverse()`原地反转一个列表，但是这样会修改原列表；想要反转列表同时又不修改原列表，可以先复制列表，然后对列表副本进行reverse操作。使用格式是：

```python 
a_list = [1, 2, 3, 4]
copy_list = a_list[:]
copy_list.reverse()
print(copy_list)
```

### 列表排序

使用`sort()`对列表进行原地排序，这样会修改原列表；想要排序但同时不修改原列表，可以先复制列表，然后对列表副本进行sort操作。使用的格式和reverse类似：`copy_list.sort()`，如果是数字排序后则从小到大排列。

### sorted排序函数

使用sorted()函数对一个列表集合按照列表中某个位置的元素进行排序。与sort()函数不同的是，sorted()函数返回一个新的排好序的列表，并不改变原列表的元素顺序

####  eg1:sorted()函数和lambda()函数的配合使用

```python
my_lists = [[1,2,3,4],[4,3,2,1],[2,4,1,3]]
my_lists_sorted_by_index_3 = sorted(my_lists, key=lambda index_value:index_value[3])
print("{}".format(my_lists_sorted_by_index_3))
```

则输出为

> [[4, 3, 2, 1], [2, 4, 1, 3], [1, 2, 3, 4]]

在这个示例中，关键字是一个`lambda`函数，表示使用索引位置为3的值（也就是列表中的第四个元素）对列表进行排序。

#### eg2:使用operator模块中的itemgetter函数

导入operator模块中的itemgetter函数，使用每个列表中多个索引位置的值对列表集合进行排序

```python
#!/usr/bin/env python3
from operator import itemgetter
mylist = [[123, 2, 2, 444], [22, 6, 6, 444], [354, 4, 4, 678], [235, 5, 5, 678],\
         [578, 1, 1, 290], [461, 1, 1, 290]]
my_list_sorted_by_index_3_and_0 = sorted(mylist, key=itemgetter(3,0))
print("{}".format(my_list_sorted_by_index_3_and_0))
```

则输出为

> [[461, 1, 1, 290], [578, 1, 1, 290], [22, 6, 6, 444], [123, 2, 2, 444], [235, 5, 5, 678], [354, 4, 4, 678]]

## 元组

元组除了不能被修改之外其余地方和列表非常相似，应用于列表的函数和操作符，比如：len函数返回元组中元素的个数，元组索引和元组切片可以引用元组中特定的元素，+操作符可以连接多个元组。

### 创建元组、元组解包及元组转换成列表（或列表转换成元组）

```python 
#使用圆括号创建元组，方括号创建列表
my_tuple = ('x', 'y', 'z')
my_list = [1, 2, 3]
#使用赋值操作符左边的变量对元组进行解包
one, two, three = my_tuple
#list()将元组转换成列表，tuple()将列表转化成元组
print("{}".format(tuple(my_list)))
print("{}".format(list(my_tuple)))
```

## 字典

python中字典的本质是包含带有唯一标识符的成对信息的列表。

### 列表和字典的区别

1. 在列表中，可以使用被称为**索引**或**索引值**的连续整数来引用某个列表值。在字典中，要引用一个字典值，则可以使用整数、字符串或其他python对象，这些统称为**字典键**。在唯一键值比连续整数更能反映出变量值含义的情况下，这个特点使字典比列表更实用。
2. 列表中，列表值是隐式排序的，因为索引是连续整数。在字典中，字典值则没有排序，因为索引不仅仅只是数值。你可以为字典中的项目定义排序操作，但是字典确实没有内置排序。
3. 在列表中，为一个不存在的位置（索引）赋值是非法的。在字典中，则可以在必要的时候创建新的位置（键）。
4. 因为没有排序，所以当你进行搜索或添加新值时，字典的响应时间更快（当你插入一个新项目时，计算机不需要重新分配索引值）。当你处理的数据越来越多时，这是一个重要的考虑因素。

### 创建字典、引用字典中的值和复制字典

使用花括号`{}`创建字典；使用冒号`:`分隔键-值对；使用`len()`计算出字典中键-值对的数量；使用键来引用字典中特定的值，需要字典名称、一对方括号和一个特定的键值（字符串形式）；使用`copy()`复制字典，需要先在字典名称后面加上copy函数，然后将这个表达式赋给一个新的字典即可:

```python
a_dict = {'one':1, 'two':2, 'three':3}
print("{}".format(a_dict))
print("a_dic has {!s} elements".format(len(a_dict)))
print("{}".format(a_dict['two']))
copy_dict = a_dict.copy()
```





### 复制

### 键、值和项目

### 使用in、not in和get

### 排序





# pandas数据结构

## Series

- 多维数组
- 字典
- 标量值
- Series类似多维数组
- Series类似字典
- 适量操作与对齐Series标签

## DataFrame

dataframe是由多种类型的列构成的二维标签数据结构

- 用**Series字典**或者**字典**生成DataFrame
  - index和columns属性分别用于访问行、列标签
- 用**多维数组字典**、**列表字典**生成DataFrame
- 用**结构多维数组**或**记录多维数组**生成DataFrame
- 用**列表字典**生成DataFrame
- 用**元组字典**生成DataFrame
- 用**Series**创建DataFrame
- 备选构建器
  - DataFrame.from_dict
  - DataFrame.from_records
- 提取、添加、删除列
- 用方法链分配新列

参考：[pandas中文网](http://www.pypandas.cn/docs/getting_started/dsintro.html#series )