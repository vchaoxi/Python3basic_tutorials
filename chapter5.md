# 第 5章	 函数

## 5.1 函数定义和函数调用

示例1： 014_print_star_func.py

```Python
# 下面以 def 开始的是函数定义，包括以下几部分  
# def  
# 函数名 print_star  
# ()  
# 参数 line  
# :  
# 函数体  
# 有的函数还有返回语句，如 015_maximum_func.py  
# 两个 ''' 括起来的内容为文档字符串，用来说明函数的功能，  
# 有些软件通过文档字符串可以直接生成函数的使用手册。  
def print_star(line):      
    ''' 
    该函数用来打印正三角的星星。          
    参数 line 用来指定需要打印多少行      
    '''      
    for i in range(line):          
        space_num = line-i-1          
        star_num = 2*i + 1          
        print(' ' * space_num, end='')          
        print('*' * star_num)
  
print('请输入要打印多少行: ')  
line = int(input())   
    
# 下面这句是函数调用  
print_star(line)
```

示例2： 015_maximum_func.py

```python
# 下面函数定义里包含 2 条返回语句  
def maximum(x, y):      
    if x > y:          
        return x      
    else:          
        return y
           
print(maximum(2, 3))
```

函数定义时的参数被称为形参，函数调用时的参数被称为实参。

## 5.2 局部变量和全局变量

示例1： 016_local_var_demo.py

```python
num = 100 
  
def func(num):      
    print('函数内: 修改前 num 的值为', num)      
    num = 10      
    print('函数内: 修改后 局部变量 num 的值为', num)
    
func(num)  
print('函数外: 函数调用后 num 的值为', num)
```

示例2：017_global_var_demo.py

```python
num = 100   

def func():      
    # 声明使用全局变量 num，全局变量要定义在所以函数和类的外部
    global num      
    print('函数内: 修改前 num 的值为', num)      
    num = 10      
    print('函数内: 修改后 全局变量 num 的值为', num)   
    
func()  
print('函数外: 函数调用后 num 的值为', num)
```

**注意**：*尽量避免使用全局变量。*

## 5.3 函数参数

### 5.3.1 默认参数

默认参数是相对于必选参数而言的，必选参数，也就是说在函数调用时必须要传入的参数，如上例中的 x 。

在函数定义时，形参列表中要明确默认参数的形式，如上例 中的 n=2 。

在函数定义时，要做到必选参数在前，默认参数在后；变化大的参数在前，变化小的参数在后。

示例： 018_default_para_demo.py

```python
def power(x, n=2):      
    res = 1      
    while n > 0:          
        n = n - 1          
        res = res * x      
    return res
       
print(power(5))  
print(power(5, 2))  
print(power(5, 3))
```

**注意**：*默认参数仅仅会被计算一次，但当默认参数是可变对象（如 list 或 dictionary）时，可能会出现有与预期不符的现象。*

示例： 019_default_para_mutable_demo.py

```python
def add_end(L=[]):      
    L.append('END')      
    return L  
     
print(add_end([1, 2, 3]))  
print(add_end(['a', 'b', 'c']))  
print(add_end())  
print(add_end())
```

以上代码修改如下：

示例： 020_default_para_immutable.py

```python
def add_end(L=None):      
    if L is None:          
        L = []      
        L.append('END')      
    return L   
    
print(add_end([1, 2, 3]))  
print(add_end(['a', 'b', 'c']))  
print(add_end())  
print(add_end())
```

### 5.3.2 关键词参数

函数调用时传入的实参默认是按照函数定义时形参中的顺序进行的，一般称这种实参为位置参数。

我们也可以按照 kwarg=value 这种形式来进行函数调用，这种方式就不用考虑函数调用时的参数位置，这种实参被称为关键词参数。

示例： 021_keyword_para_demo.py

```python
def func(a, b=5, c=10):      
    print('a is', a, 'and b is', b, 'and c is', c)   
    
func(3, 8)  
func(25, c=80)  
func(c=50, a=100)
```

在函数调用时，如果同时使用位置参数和关键词参数，要确保关键词参数在位置参数之后。

关键词参数是相对于位置参数而言的，更多的是函数调用时的概念，而非函数定义。不过当函数定义时形参最后一个参数是 **name 这种形式时，它会接收一个字典，该字典包含除之前形参之外的所有关键词参数。

示例： 022_keyword_para_2_demo.py

```python
def enroll(name, age, gender, **keywords): 
    print('*' * 40)      
    print('基本信息:')      
    print('姓名 :', name)      
    print('年龄 :', age)      
    print('性别 :', gender)      
    print('-' * 40)      
    print('其他信息:')      
    for kw in keywords:          
        print(kw, ':', keywords[kw])   
        
enroll('张三', 18, '男', 城市='郑州', 专业='Python')  
enroll('李四', 22, '男', 城市='郑州', 专业='Python', 爱好='唱歌')
```

### 5.3.3 可变参数

有时候我们可能会需要定义能够接收任意多个参数的函数，就像 print 一样，这就需要用到可变参数。

在函数定义的形参中出现 *args 这种参数，就表明这是个可变函数。

示例： 023_varargs_demo.py

```python
def list_items(*args):      
    id = 0      
    for iterm in args:          
        print(id, iterm)          
        id = id + 1      
    print('_' * 40)
       
list_items('桔子', '香蕉', '苹果', '菠萝')  
list_items('C', 'C++', 'Python', 'Java', 'PHP')
```

关键词参数中我们提到 \*\*name 这种形式的参数只能出现在形参的最后一个，所以，如果形参中 \*args 跟 \*\*name 这两种形式需要同时出现时，\*args 要在 \*\*name 的前面。

示例： 024_varargs_keywordargs_demo.py

```python
def enroll(name, *args, **fam):      
    print('*' * 40)      
    print('基本信息:')      
    print(name)      
    for item in args:          
        print(item)      
    print('-' * 40)      
    print('家庭成员信息:')      
    for kw in fam:          
        print(kw, ':', fam[kw])
           
enroll('张三', 父亲='张无忌', 母亲='殷素素')  
enroll('李四', 22, '男', '郑州', 父亲='李小龙')
```

\*args 之后 \*\*name 之前还可以出现其他的形参，这些形参被称为 'keyword-only' 参数，也就是只能通过关键词参数的方式来调用。

从本质上来讲 \*args 和 \*\*name 这两种形式都是可变参数，只不过 \*\*name 这种形式在内部实现时被封装成了字典，只能用关键词参数的形式来调用。

**解压参数**

在调用形参中出现 *args 和 **name 这两种形式的函数时，我们可以通过传入一个 tuple/list 和 dict 来调用，这种方式被称为解压参数。

示例： 025_unpacking_arg_demo.py

```python
def func(a, b, c=7, *args, d, **kw):      
    print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'd =', d, 'kw =', kw)   
    
args1 = (1, 2, 3, 4)  
args2 = [10, 20, 30, 40, 50]  
kw1 = {'d':11,  'aa':'!!', 'bb':'##'}  
kw2 = {'aa':'!!', 'bb':'##'}  
# 注意下面调用时的 * 和 **  
func(*args1, **kw1)   
func(*args2, **kw1)   
# 下面这个语句执行时会报错，请思考下为什么？  
# func(*args2, **kw2) 
```

**5.4 Lambda 表达式**

**5.5 函数注释**

