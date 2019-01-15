# 第 9章	 错误、异常和调试

## 9.1 错误

在 Python 开发时，我们遇到的大部分错误是语法错误(Syntax Error)。如下例

```python
>>> print('Hello, world)    
File "<stdin>", line 1      
print('Hello, world)                         
              ^  
SyntaxError: EOL while scanning string literal
```

## 9.2 异常

有时候，即使语法正确，也会在执行时遇到错误，在执行中检测出来的错误一般称为异常。如下例：

```python
>>> a = 10  
>>> b = 0  
>>> a / b  
Traceback (most recent call last):    
  File "<stdin>", line 1, in <module>  
ZeroDivisionError: division by zero
```

**异常处理**

示例： 042_exceptions_handle_demo.py

```python
# -*- coding:utf-8  -*-  
# 上面那一句中文编码支持，在 Python3 里默认会支持  
try:      
  text = input('请输入些什么 --> ')  	
  print('你输入了', text)  
except EOFError:      
  # 按 ctrl + d      
  print('你输入了 EOF ...')  
except KeyboardInterrupt:      
  # 按 ctrd + c      
  print('你结束了该程序...')  
else:      
  print('谢谢配合！')  
finally:  	
  print('END')
```

当我们预估某些代码可能运行中会出错，就可以用 try 来运行这段代码。如果执行到某行代码出错，则 try 语句里该行代码之后的代码不会继续执行，而是直接跳到错误处理代码，即相应的 except 语句块；如果，没有出错，在 try 语句块执行完之后，还会继续执行 else 语句块。最后的 finally 是不管出错不出错，都会最后执行到的语句。当然，else 和 finally 都是可选的。

## 9.3 调试

程序很少一次编写就能正常运行的，有时候，哪怕是正常运行的程序也会出现各种各样的非预期行为，在软件开发里，我们把这种情况，统称为 bug。遇到 bug 很正常，重要的是，我们要掌握通过调试定位并修复 bug 的能力。

在 Python 开发中，我们可以通过print暴力调试、断言、logging、pdb、pdb.set_trace() 等方式来调试 bug。

**print 暴力调试**

示例：  043_print_debug_demo.py

```python
def n_divided_by_m(n, m):      
  n = int(n)      
  m = int(m)      
  # 出错后，我们可以把关键信息打印出来，进行debug  
  print('>>> n = %d' % n)      
  print('>>> m = %d' % n)      
  print(n, '/', m, '=', m/n)   
  
def main():      
  print('我们正在进行除法运算：')      
  n = input('请输入一个除数：')      
  m = input('请输入一个被除数：')      
  n_divided_by_m(n, m)   
  
main()
```

print 暴力调试，最大的弊端在于，程序运行会产生各种调试信息，调试完了后，还需要删除这些 print语句

**断言**

示例： 044_assert_debug_demo.py

```python
def n_divided_by_m(n, m):      
  n = int(n)      
  m = int(m)      
  # 我们通过断言，断定 n 不能为 0      
  assert n != 0, '天哪，n 竟然是 0'      
  print(n, '/', m, '=', m/n)   
  
def main():      
  print('我们正在进行除法运算：')      
  n = input('请输入一个除数：')      
  m = input('请输入一个被除数：')      
  n_divided_by_m(n, m)   
  
main()
```

使用断言，比 print暴力调试好了很多。只会在遇到断言失效的时候，才会抛出调试信息。

**logging**

示例： 045_logging_debug_demo.py

```python
import logging
logging.basicConfig(filename='045_logging_debug_demo.log', level=logging.INFO)   

def n_divided_by_m(n, m):      
  n = int(n)      
  m = int(m)      
  # 将程序运行中的关键信息，记录到日志文件，是一个好的习惯  
  logging.info('n = %d' % n)      
  logging.info('m = %d' % m)      
  print(n, '/', m, '=', m/n)   
  
def main():      
  print('我们正在进行除法运算：')      
  n = input('请输入一个除数：')      
  m = input('请输入一个被除数：')      
  n_divided_by_m(n, m)   
  
main()
```

使用 logging 模块可以既保存记录程序运行的关键信息，又不影响程序的正常输出，是一个很好的习惯和方式。

**pdb**

我们运行 python 程序时，加上参数 -m pdb 启动后，就可以进行单步调试了。

l (list): 可以列出源代码，n (next): 可以执行单步代码， p(print): 可以打印变量名，q(quit): 结束调试，退出程序。

**pdb.set_trace()**

这本质上还是 pdb 单步调试，典型用在代码量很大的时候，我们可以在源代码中导入 pdb 模块，然后在需要单步暂停调试的地方执行 pdb.set_trace() 语句即可。

示例： 046_set_trace_debug_demo.py

```python
import pdb   

def n_divided_by_m(n, m):      
  n = int(n)      
  m = int(m)      
  # 当我们认为这个地方可能会是出错的地方时，      
  # 可以通过 pdb.set_trace() 在此暂停，进行单步调试      
  # 调试完成，按 c 让程序继续运行      
  pdb.set_trace()      
  print(n, '/', m, '=', m/n)   
  
def main():      
  print('我们正在进行除法运算：')      
  n = input('请输入一个除数：')      
  m = input('请输入一个被除数：')      
  n_divided_by_m(n, m)   
  
main()
```
