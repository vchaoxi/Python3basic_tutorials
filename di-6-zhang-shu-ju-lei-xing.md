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


![](/assets/屏幕快照_2018-01-04_下午1.12.29.png)

