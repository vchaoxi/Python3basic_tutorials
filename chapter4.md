# 第 4章	 控制语句

## 4.1 if 语句

示例： 005_guess_poker_num_demo.py

```pyton
poker = int(input('请输入你翻到的扑克牌：'))  
guess = int(input('猜一猜对方翻到的扑克牌：'))   

if guess == poker:   
   # 这下面是 if 分支语句的代码块      
   print('Bingo! 恭喜你，猜对了。')      
   print('(精神鼓励一下吧!)')      
   # if 代码块到这里就结束了  
elif guess < poker:      
   # 这下面是 elif 分支语句的代码块      
   print('比你猜的数字要大')  
else:      
   print('比你猜的数字要小')   
   
print('结束!')
```

**注意**：*在 Python 语言里，没有 switch 语句。*

## 4.2 for 语句 - for in

Python 的 for 循环和 C 语言等的 for 循环不太一样，准确地说应该叫 for in，后面跟一个序列，比如 list 或 string，for 循环回去依次迭代后面序列中的每一个对象。

示例1： 006_stat_str_len_demo.py

```python
>>> # 统计字符串长度  
... words = ['cat', 'window', 'improvement']  
>>> for w in words:  
...     print(w, len(w))  
...  
cat 3  
window 6  
improvement 11
```

示例2： 007_print_range_demo.py

```python
>>> for i in range( 5):  
...     print(i)  
...  
0  
1  
2  
3  
4
```

**range() 函数**

```python
>>> list(range(5))  
[0, 1, 2, 3, 4]  
>>> list(range(5, 10))  
[5, 6, 7, 8, 9]  
>>> list(range(0, 10, 3))  
[0, 3, 6, 9]  
>>> list(range(-10, -100, -30))  
[-10, -40, -70] 
  
>>> print(range(10))  
range(0, 10)
```

## 4.3 while 语句

示例： 008_guess_poker_num2_demo.py

```python
poker = int(input('请输入你翻到的扑克牌：'))   

running = True   

while running:  	
   guess = int(input('猜一猜对方翻到的扑克牌：'))  	
   if guess == poker:      		
      # 这下面是 if 分支语句的代码块      	
      print('Bingo! 恭喜你，猜对了。')      		
      print('(精神鼓励一下吧!)')  		
      # 下面这条语句停止 while 循环  		
      running = False 
   elif guess < poker:      		
      print('比你猜的数字要大')  	
   else:      		
      print('比你猜的数字要小')  
else:  	
   print('While 循环结束!')   
      
print('游戏结束!')
```

**注意**：*在 Python 语言里 for 和 while 循环可以有 else 子句。*

## 4.4 break 语句

示例1： 009_print_str_len_demo.py

```python
while True:      
   s = input("请输入字符串, 输入'quit'，则结束程序: ")      
   if s == 'quit':          
      break      
   # 四种常用方法，但个人都不推荐      
   print('字符串 \'{}\' 的长度是: {}'.format(s, str(len(s))))      
   print('字符串 ' + "\'" + s + "\'" + ' 的长度是:', len(s))      
   print('字符串 \'%s\' 的长度是: %d' % (s, len(s)))
   print('字符串', "\'"+s+"\'", '的长度是:', len(s))      
   # 建议下面极简编码风格      
   print('字符串', s, '的长度是:', len(s))  
print('结束')
```

示例2： 010_print_prime_num_demo.py

```python
for n in range(2, 10):      
   for x in range(2, n):          
      if n % x == 0:              
         print(n, '=', x, '*', n//x)              
         break      
   else:          
      # 内层循环迭代穷尽后走到这里，break 不会到这里
      print(n, '是一个素数')
```

## 4.5 continue 语句

示例1： 011_nickname_len_check_demo.py

```python
while True:      
   nickname = input("请输入昵称, 输入'quit'，则结束程序: ")
   if nickname == 'quit':          
      break      
   if len(nickname) < 3:          
      print('昵称长度太短，请继续输入: ')          
      continue      
   print('昵称', nickname, '长度合格')
```

示例2： 012_even_odd_check_demo.py

```python
for num in range(2, 10):      
   if num % 2 == 0:          
      print(num, '是一个偶数')          
      continue      
   print(num, '是一个奇数')
```

## 4.6 pass 语句

Python 语言里 pass 是空语句，pass 语句不做任何事情，一般用做分支占位语句或空函数体占位语句，是为了保持程序结构的完整性和思路的流畅性。

示例： 013_pass_demo.py

```python
str = 'o0oo0o0o00oooo00o0 o0oo0o0o00oooo00o0 o0oo0o0o00oooo00o0'  
count = 0  
for c in str:      
   if c == '0':          
      pass      
   count += 1   
print('字符串里共有', count, '个O')
```

