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
注意：跟 C 语言等其他语言不同，Python中没有 long 等其他整形类型，int 就代表所有整形类型。

### 2.2.2 字符串

**单引号**

```python
'This is a string'
```
**双引号**

```python
This's is another string."
```
注意：单引号字符串和双引号字符串在 Python 中基本上是一样的。

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


