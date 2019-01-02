# 第 2章	 Python 基础知识

## 2.1 注释

Python 中 以 # 开始的内容为注释，如下所示：

```python
print('hello world') # print 是一个函数 
  
# 下面的 print 是一个函数  
print('hello world')
```

## 2.2 字面常量

```python
23、3.14、'Hello'  
上面的数字和字符串在 Python中被称为字面常量；  
字面常量的字面指它就表示其本身的含义，没有任何的其他语法含义，常量指它的内容没法被修改。
```

### 2.2.1 数字

数字主要有整形和浮点两种类型。

```python
7 是整形类型。
3.14 是浮点类型。  
16.8E-4 也是浮点类型，表示16.8 * 10^-4 = 0.00168。
```

**注意**：*跟 C 语言等其他语言不同，Python中没有 long 等其他整形类型，int 就代表所有整形类型。*

### 2.2.2 字符串

**单引号**

```python
'This is a string'
```

**双引号**

```python
"This's is another string."
```

**注意**：*单引号字符串和双引号字符串在 Python 中基本上是一样的。*

**三引号**

如果需要跨多行的字符串，可以用三引号 ''' 或 """

```python
'''This is multiline string.  
Whai's ur name?  
I am "Dorayo".  
'''
```

**format() 方法**

示例： 000_format_demo.py

```python
>>> name = 'Dorayo'  
>>> country = '中国'  
>>> print('{0} loves {1}!'.format(name, country))  
Dorayo loves 中国!  
>>> print('{} loves {}!'.format(name, country))  
Dorayo loves 中国!
   
# 表示浮点精度  
>>> print('{0:.3f}'.format(1.0/3))  0.333
   
# 表示百分百  
>>> points = 19  
>>> total = 22  
>>> 'Correct answers: {:.2%}'.format(points/total)  
'Correct answers: 86.36%' 
  
# 表示整数  
>>> for i in range(11):  
...     print('{:2d} {:3d} {:4d}'.format(i, i*i, i*i*i))  
...   
  0   0   0   
  1   1   1   
  2   4   8   
  3   9   27   
  4   16  64   
  5   25  125   
  6   36  216   
  7   49  343   
  8   64  512   
  9   81  729  
  10  100 1000
```

**转义字符**

示例： 001_escape_sequences_demo.py

```python
>>> print('What\'s your name?')  
What's your name? 
  
>>> print('This is the first line\nThis is the second line')  
This is the first line  
This is the second line 
  
>>> print('This is the first sentence. \  
... This is the second sentence.')  
This is the first sentence. This is the second sentence.
```

**原始字符**

```python
>>> print(r'Newlines are indicated by \n')  
Newlines are indicated by \n
```

## 2.3 变量

### 2.3.1 变量的本质

**变量是程序员对内存的抽象。**

### 2.3.2 变量名

```python
变量名第一个字符以字母或下划线(_)开始  
剩余的字符可以是字母、下划线或数字  
大小写敏感，比如 myName 和 myname 就是两个不同的变量名
```

### 2.3.3 数据类型

**Python 常用内置基本数据类型有**

**布尔类型 True False**

**字类型 int, float, complex**

**序列类型 list, tuple, range**

**字符串类型 str**

**集合类型 set**

**映射类型 set**

## 2.4 逻辑行和物理行

示例： 002_logicline_physicline_demo.py

```python
# style1 一个物理行，一个逻辑行  
i = 7  
print(i)
   
# style2 一个物理行，一个逻辑行  
i = 7;  
print(i);
   
# style3 一个物理行，两个逻辑行  
i = 7; print(i);
   
# style4 一个物理行，两个逻辑行  
i = 7; print(i)
   
以上 4 种 style 结果完全一样，推荐 style1
```

## 2.5 缩进

示例： 003_indent_demo.py

```python
>>> num = 7  
>>>  print('num is', num)    
File "<stdin>", line 1      
print('num is', num)      
^  
IndentationError: unexpected indent  
>>> print('num is', num)  
num is 7
```

## 2.6 基本输入和输出

示例： 004_input_output_demo.py

```python
>>> print('Please input your name.')  
Please input your name.  
>>> name = input()  
dorayo  
>>> print('Your name is: ', name)  
Your name is:  dorayo

注意：在 Python 3 中 input 默认接受的是字符串类型 str。
```




