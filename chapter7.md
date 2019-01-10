# 第 7章	 模块

## 7.1 什么是模块

在进行 Python 编程，命令行解释器在退出后再进入，创建的函数和定义的变量就消失了，所以，稍微长些的程序，我们一般会用编辑器编写代码并保存为一个文件，这个文件也被称为脚本(script)，该文件以 .py 的后缀结尾。

随着代码量的增加，我们一般会根据功能将一个脚本文件拆分为多个脚本文件，以便于维护，每个脚本文件中一般都包含若干个函数和变量，我们可以在其他脚本文件中使用这些函数和变量。

这样的每个脚本文件，也被成为模块。

## 7.2 为什么需要模块

通过模块来拆分代码，最大的好处在于提高了代码的可维护性。

其次，提高了代码的可复用性，提升了开发效率。我们把常用的功能做成模块，以后开发任何项目，如果需要用到该功能，我们就能够直接导入该模块，使用该功能，而不用从零开始开发了。Python 有很多优秀的内置模块和第三方模块。

使用模块，还可以避免函数名和变量名冲突，即相同的名字和函数可以同时存在于不同的模块中。但要避免与系统内置函数名冲突。https://docs.python.org/3/library/functions.html 该链接给出了系统内置函数。

## 7.3 使用模块

示例： 036_sys_module_using_demo.py

```python
import sys # 导入 sys 模块   

print('命令行参数是：')  
# argv 是 sys 模块的一个变量，存储命令行参数  
for i in sys.argv:      
    print(i)   
    
# path 也是 sys 模块的一个变量，后面会详细解释  
print('\n\n PYTHONPATH:', sys.path)   

# 每一个模块都默认有一个全局变量 __name__，该变量的值为字符串，存储该模块的名字，模块的名字即模块文件去除后缀 .py 之后的那个字符串，sys 模块的模块文件为sys.py，模块名为 sys  print('\n\nsys 模块的名字是', sys.__name__)
```

**模块的查找路径**

*当我们通过 import 语句导入一个模块时，Python 解析器会首先在系统内置模块列表中查找该名字，如果，没有找到，紧接着会在 sys.path 变量储存的路径列表中查找。*

## 7.4 创建并使用模块

我们首先创建一个模块，用来打印给定行数的三角形

示例： dry_01_print_triangle.py 

```python
def print_right_triangle(line):      
    ''' 该函数用来打印直角三角形          
    参数 line 用来指定需要打印多少行      
    '''      
    line = int(line)      
    for i in range(line):          
        print('*' * (i+1))   
        
def print_triangle(line):      
    ''' 该函数用来打印正三角形          
    参数 line 用来指定需要打印多少行      
    '''      
    line = int(line)      
    for i in range(line):          
        space_num = line-i-1          
        star_num = 2*i + 1          
        print(' ' * space_num, end='')  
        print('*' * star_num)
```

接着，我们写一个脚本，在该脚本中导入我们刚才的模块

示例： 038_module_demo.py

```python
from dry_01_print_triangle import print_triangle, print_right_triangle  import sys   

def main(argv):      
    print(sys.argv[0])      
    if len(sys.argv) < 3 or \      
    sys.argv[1] not in ('print_right_triangle','print_triangle'):
        print('Usage: python3', sys.argv[0], '<print_right_triangle> | <print_triangle>', '<5>')
        exit()       
        
    # eval 可以将字符串当做函数名来进行函数调用，但是，要慎用，避免用户借此执行恶意代码      
    eval(argv[1])(argv[2])   

if __name__ == '__main__':      
    main(sys.argv)
```

**from … import …**

if \_\_name == '\_\_main\_\_':

在 Python 中，每一个 以 .py 后缀的文件，都被称为一个模块。每个模块的模块的模块名都保存在 \_\_name\_\_ 的全局变量里。

当该模块被别的模块导入时，\_\_name\_\_ 的值为模块的文件名（不带 .py 后缀）字符串；

当该模块独自运行时，\_\_name\_\_ 的值为 '\_\_main\_\_' 。

\_\_pycache\_\_ 和 .pyc

Python 为了提高效率，在我们导入非系统内置模块时，会在程序运行的当前目录中创建一个名为 __pycache__ 的目录，在里面存放被导入的模块的编译后的字节码文件，该字节码文件以 .pyc 为后缀，是跨平台的。

**Package 包**

计算机科学中有一句名言：「只有再多加一层间接，没有解决不了的问题」。当模块过多之后，Python 中又引入了包（Package）来组织模块。简言之，模块是对函数和变量的一层间接封装，包又是对模块的一层间接封装。

如下图所示：

![](/assets/屏幕快照_2018-01-05_下午5.48.59.png)

**注意**：*每一个包目录下面都会有一个__init__.py的文件，这个文件是必须存在的，否则，Python就把这个目录当成普通目录，而不是一个包。__init__.py可以是空文件，也可以有Python代码，因为__init__.py本身就是一个模块，而它的模块名就是它所在的那个上一级目录的目录名。*

如果想要使用 sound 包下的 effects 包下的 echo 模块中的内容，可以有如下几种方式：
方法一：

```python
import sound.effects.echo
sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)
```
方法二：

```python
from sound.effects import echo
echo.echofilter(input, output, delay=0.7, atten=4)
```

方法三：

```python
from sound.effects.echo import echofilter
echofilter(input, output, delay=0.7, atten=4)
```


