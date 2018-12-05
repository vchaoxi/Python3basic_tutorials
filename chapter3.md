# 第 3章	 操作符、表达式和语句

## 3.1 常用操作符（运算符）

**+ (加)**

**- (减) 减号或负号**

*** (乘)**

**** (乘方) **

** / (除)** 

**// (向下取整的除)**

**% (取模)** 

**<< (左移) **

**>> (右移)**

**& (按位与)**

**| (按位或)**

**^ (按位异或)**

**~ (按位取反)**

**< (小于)**

**> (大于)**

**<= (小于或等于)**

**>= (大于或等于)**

**== (等于)**

**!= (不等于)**

**not (布尔取反)**

**and (布尔与)**

**or (布尔或)**

## 3.2 操作符的优先级

下表中优先级从上往下依次增加，同一行具有相同的优先级

|运算符|描述|
|-|-|
|lambda|Lambda表达式|
|or|布尔“或”|
|and|布尔“与”|
|not x|布尔“非”|
|in, not in|成员测试|
|is, is not|同一性测试|
|&gt, &lt , &lt =, >=, !=, == |比较|
|&#124|按位或|
|^|按位异或|
|&|按位与|
|>>, <<|移位|
|+，-|加法与减法|
|*, /, %|乘法、除法取余|
|+x, -x|正负号|
|-x|按位翻转|
|**|指数|
|x.attribute|属性参考|
|x[index]|下标|
|x[index.index]|寻址段|
|f(arguments...)|函数调用|
|(expression,...)|绑定或元组显示|
|[expression,...]|列表显示|
|{key:datum,...}|字典显示|
|'expression,...'|字符串转换|

不需要记忆，不确定时可以用 () 调整优先级

## 3.2 表达式

**用操作符连接变量、常量或对象而构成的有值的算式就是表达式**

## 3.3 语句

语句分为简单语句和复合语句

简单语句是指一逻辑行的代码。例如表达式语句、赋值语句和return语句等

复合语句是指包含、影响或控制一组语句的代码。例如if、try 等语句等

表达式本身可以作为表达式语句，也能作为赋值语句的右值或if语句的条件等，所以表达式可以作为语句的组成部分，但不是必须成分




  	  