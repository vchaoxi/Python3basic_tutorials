# 第 6章	 数据类型

## 6.1 数据类型概述

### 6.1.1 数据的组织逻辑分类

计算机处理的数据主要分为两大类。单值的标量数据和集合数据。

诸如 7，3.14，'北京'  ，这每一个都属于单值的标量数据。

集合数据又分为序列集合数据，映射集合数据和无序集合数据。

如，我们想表示一个学生的初中各学科成绩，就需要一个映射集合数据类型，类似 {语文 :  90, 数学 : 98, 英语 : 96} 这种样式；

如果，我们想处理数学上的交，并，差等集合运算，就天然地需要用到无序集合数据类型。

如，我们想表示《福布斯》富豪排行榜，就需要一个序列集合数据类型，类似 [Bill Gates, Warren Buffett, Jeff Bezos, Amancio Ortega, Mark Zuckerberg] 样式；

### 6.1.2 Python 语言的内置数据类型

Pyhon 内置的数据结类型美的符合数据的组织逻辑，主要提供了 list 和 tuple 来组织处理序列集合数据，提供了 dict 来组织处理映射集合数据， 提供了 set 来组织处理无序集合数据。

## 6.2 List 列表

用方括号括起来的序列，就构成了 一个 list，序列各元素之间用逗号隔开

示例： 026_list_use_demo.py

```python
zoo = ['老虎', '狮子', '猴子', '长颈鹿', '斑马']
   
print('动物园有', len(zoo), '种动物。')   

print('这些动物分别是:', end=' ')  
for animal in zoo:
   print(animal, end=' ')   
   
print('\n最近，新引进了大熊猫。')  
zoo.append('大熊猫')  
print('现在，动物园里都有', zoo)   

print('猴子引进的序号是', zoo.index('猴子'))   

zoo.reverse()  
print('动物园按照引进顺序从后往前依次是', zoo)   

print('-'*80)   

bookstore = ['Exit West', 'Killers of the Flower Moon', 'Little Fires Everywhere', 'Beartown', 'Exit West']

print('Exit West 这本书在书架上总共有',bookstore.count('Exit West'), '本')   

bookstore.sort()  
print('书架上的书整理排序后，分别是', bookstore)   

print('从书架上拿走最后放上去的那本书', bookstore.pop())

bookstore.insert(3, 'Coders at Work')  
print('在序号为 3 的那本书之前插入一本书之后，书架上的书为：', bookstore)
```

List 常用方法：

List 更多方法，详见官方文档 https://docs.python.org/3/tutorial/datastructures.html

del 语句

del 语句可以根据给定的索引来移除 list 中的元素，它跟 pop() 方法的不同点在于 pop() 方法会返回被移除的那个元素。

示例： 027_del_use_demo.py

```python
a = [-1, 1, 33, 18.6, 876, 33, 22]  
del a[0]  
print(a) 
del a[2:4]  
print(a)  
del a[:]  
# a.clear()  
print(a)
```
使用 List 来实现栈这种数据结构

栈是一种后进先出的数据结构，我们可以使用 list 的 append() 和 pop() 方法来很方便的实现栈这种数据结构。

示例： 028_list_stack_demo.py

```python
stack = [3, 4, 5]  
print('栈里的初始结果是', stack)  
print('往栈里添加一个 6')  
stack.append(6)  
print('往栈里再添加一个 7')  
stack.append(7)  
print('现在栈里的结果是', stack)  
print('出栈一个:', stack.pop())  
print('现在栈里的结果是', stack)  
print('出栈一个:', stack.pop())  
print('出栈一个:', stack.pop())  
print('现在栈里的结果是', stack)
```

使用 List 来实现队列这种数据结构

示例： 029_list_queue_demo.py

```python
from collections import deque  
queue = deque(["张三", "李四", "王五"])  
print('队列的初始结果是：', queue)  
print('赵六 入队')  
queue.append("赵六")  
print('田七 入队')  
queue.append("田七")  
print('出队一个：', queue.popleft())  
print('出队一个：', queue.popleft())  
print('队列现在的结果是：', queue)
```

队列式一种先进先出的数据结构，list 本身并不能很容易的实现队列，我们可以借助 collections 模块的 deque 库来实现。

List 解析式 (List Comprehensions)

示例： 030_list_comprehensions_demo.py

```python
print('01. 用程序生成 10 以内的自然数的平方列表')  
print('老方法：')  
squares = []  
for x in range(10):      
   squares.append(x**2)   
   
print(squares)   

print('List Comprehension 的方法：')  
squares = [x**2 for x in range(10)]  
print(squares)   

print('02. 再看一个更复杂的例子, 列表中的每一个元素是一个 tuple')  
l = [(x, y) for x in [1,2,3] for y in [2,3,4] if x != y]
print(l)  
print('如果没有 List Comprehension, 代码写起来会稍微复杂点，但结果一样：')  
l = []  
for x in [1,2,3]:      
   for y in [2,3,4]:          
      if x != y:              
         l.append((x, y))   
         
print(l)   

print('03. 嵌套 List Comprehension')  
matrix = [          
   [1, 2, 3, 4],          
   [5, 6, 7, 8],          
   [9, 10, 11, 12],          
      ]   
      
transposed = [[row[i] for row in matrix] for i in range(4)]  
print(transposed)   

print('用老方法：')  
transposed = []  
for i in range(4):      
   transposed_row = []      
   for row in matrix:    
      transposed_row.append(row[i])
   transposed.append(transposed_row)  
   print(transposed)
```

List 解析式是一种提供了一种便捷的方式来创建列表。

## 6.3 Tuple 元组

Tuple 中译为元组，跟 list 很像， 但又比 list 简单很多，两者的使用场景有重叠的也有不同的，根本原因在于 tuple 是不可变的。

用 圆括号 括起来的一个序列就构成了一个 tuple ，圆括号大部分时候都可以省略，但个人习惯建议加上。

示例： 031_tuple_demo.py

```python
# t = (12, 3.14, 'hello')  
t = 12, 3.14, 'hello'  
print(t[0])  
print(t)   

# tuple 可以嵌套  
tt = t, (1, 2, 3)  
print(tt)   

# tuple 是不可变的，所以，不能赋值，下面的语句会报错  
# t[0] = 88   

# 但是 tuple 包含的元素可以是可变对象  
l1 = [1, 2, 3]  
l2 = ['a', 'b', 'c']  
ttt = l1, l2  
print(ttt)  
l1[0] = 100  
l2[1] = 'x'  
print(ttt)
```

空元组和只含 1 个元素的元组稍微有点不同，如下所示：

```python
>>> empty = () # 空元组  
>>> singleton = 'hello',    # <-- 只含 1 个元素的元组，注意，最后的逗号  
>>> len(empty)  
0  
>>> len(singleton)  
1  
>>> singleton  
('hello',)
```

## 6.4 Sequence 序列

我们有三种基本的序列类型： list、tuple 和 range 对象。另外，专门用于二进制数据处理的 binary data 和 文本字符串处理的 text strings 也属于序列类型。

所有的序列都有些通用的操作，如下表所示：

![](/assets/屏幕快照_2018-01-04_上午11.47.10.png)

示例： 032_sequence_common_ops_demo.py

```python
l1 = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]  
l2 = ['a', 'b', 'c', 'd', 'e']  
s1 = 'Hello, world!'  
s2 = 'I love u.'   

print(3 in l1)  
print('!' not in s1)  
print(l1+l2)  
print(s1+s2)  
print(s1[2:4])  
print(l1[1:7:3])  
print(l1[-2])  
print(min(l1))  
print(max(l1))
```

可变序列还有些额外的操作，如下表所示：

![](/assets/屏幕快照_2018-01-04_下午1.12.29.png)

示例： 033_mutable_sequence_ops_demo.py

```python
l1 = [1, 2, 3, 4, 5, 6]  
l2 = ['a', 'b', 'c']   

l1[1] = 10  
print(l1)  
l2[0:2] = 'x','y','z' # 注意 'a', 'b' 被替换成了 'x', 'y', 'z'  
print(l2)  
del l2[0:2]  
print(l2)   

# 注意区分 append 和 extend 的区别  
# l1.append(l2)  
# l1.extend(l2)  
# l1.extend(l2) 等同于 l1 += l2  
l1 += l2  
print(l1)   

l3 = ['x']  
l3 *= 6  
print(l3)   

l3.insert(2, 'o')  
print(l3)  
l3.reverse()  
print(l3)
```

## 6.5 Dictionary 字典

字典用来表示映射关系，存储的是 键-值 对。

示例： 034_dict_demo.py

```python
student_infos = {'name': '张三', 'age': 18}  
print('学生的年龄是', student_infos['age'])
student_infos['gender'] = '男'  
print('学生的信息是', student_infos)  
del student_infos['age']  
print('学生的信息是', student_infos)  
print('学生信息中是否包含性别：', 'gender' in student_infos)
print('都包含哪些信息项：', list(student_infos.keys()))   

# 还可以通过 dict 类的构造函数来创建字典  
teacher_infos = dict([('name', '李四'), ('age', 38), ('gender', '女')])  
print(teacher_infos)   

teacher_infos = {}  
teacher_infos = dict(name='王五', age=36, gender='男')
print(teacher_infos)   

# 还可以通过字典解析式(dict comprehension)来构造字典  
dict = {x: x**2 for x in range(0, 10, 2)}  
print(dict)
```

## 6.6 Set 集合

Set 是一种无序的集合，可以用花括号{}或者set() 函数来创建 set。如果，要创建空 set 要用set()，而不是 {}。

示例： 035_set_demo.py

```python
sports = {'football', 'basketball', 'swimming', 'running'}  
print(sports)  
print('football' in sports)  
print('yoga' in sports)   

a = set('abcdefghijk')  
b = set(['a','c', 'e', 'f', 'x', 'y', 'z'])  
print(a)  
print(b)  
print(a - b)  
print(a | b)  
print(a & b)  
print(a ^ b)
```





