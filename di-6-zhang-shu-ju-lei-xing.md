# 第 6章	 数据类型

## 6.1 数据类型概述

### 6.1.1 数据的组织逻辑分类

### 6.1.2 Python 语言的内置数据类型

## 6.2 List 列表

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





