# 第 8章	 面向对象编程

## 8.1 面向对象编程简介

面向对象编程是相对于面向过程编程而言的。

面向过程编程是通过处理逻辑将一个个的函数串起来，当项目变大后，代码会极其难以维护，Bug 数也会极大增加。

面向对象编程更像是采用了一种系统论的方式来编程，着重于研究对象与对象之间的内在连接关系。

面向对象编程将数据和函数封装在一个类（Class）的概念里，每一个类就是对要通过编程来解决问题的世界里的一个要素的一种抽象。比如，我们要编写一个学生信息管理系统，学生就会是一种类，教师也是一种类。

除了类这个概念，在面向对象编程里，还有对象（Object）这个概念。一个对象也被称为一个类的实例（Instance）。在面向对象编程里，我们更多的时候是在操作对象，每个对象都有它的属性（Attribute）和方法（Method）。属性和方法在类的定义里会预先定义好，然后，针对每个具体的对象，属性会被赋予具体的值或只是读取该值，方法会被调用来实现某种行为。

举个例子，在面向对象编程里，如果我们要做个宠物医院管理系统，狗就会被定义成一种类，而具体要处理的张三家的狗和李四家的狗都属于一个个具体的对象。另外，张三家的狗和李四家的狗都有名字和毛发颜色等，这些数据就属于属性，狗可以叫也可以被接种疫苗，这些都属于行为也就是面向对象编程里的方法。

## 8.2  类和实例

### 8.2.1 创建 Dog 类

**属性**

属性分为类属性和实例属性，分别用来描述类和实例。类属性是所有类共享的，用得较少。上例中的以 self 为前缀的 name 和 age 就属于实例属性。

**self**

以 self 为前缀的变量，在类中的所有方法中都可以使用，也被称为实例变量或实例属性。

**class**

class 是定义类的关键词。

**文档字符串**

在类的定义里且在所有的函数上面的三引号开始的字符串是类的文档字符串，描述整个类。

**\_\_init\_\_ 方法**

该方法是类的初始化方法，当我们实例化一个类的对象时，在申请完内存之后，紧接着就会调用该方法对实例化对象进行初始化。__init__ 方法的第一个参数永远是 self，表示当前实例本身，剩余的参数，根据类的设计自行定义。

有了 __init__ 方法之后，在进行实例化时，就需要传入与 __init__ 函数匹配的参数，第一个参数 self 不需要传入。

示例： dry_dog.py

```python
class Dog():      
    '''这是一个模拟小狗特征和行为的类'''       
    
    def __init__(self, name, age):          
        '''初始化属性 name 和 age'''          
        self.name = name          
        self.age = age       
    
    def sit(self):          
        '''模拟小狗蹲下的命令'''          
        print(self.name + '蹲下了')       
    
    def stand(self):          
        '''模拟小狗站立的命令'''          
        print(self.name + '站立起来了')       
    
    def jump(self):          
        '''模拟小狗跳起来的命令'''          
        print(self.name + '跳起来了')
```

**方法**

类中的方法用来定义类的实例所具备的行为，如上例中的 sit、stand 和 jump 都属于方法。

类中的方法其实就是在类中定义的函数，它的第一个参数永远是当前实例变量 self，并且，调用时不用传递该 self 参数。其他情况类中的方法跟普通函数没有任何差别。

### 8.2.2 根据 Dog 类创建并使用实例

示例： 039_dog_class_use_demo.py

 ```python
 Dog 类所在的模块导入 Dog 类  
 from dry_02_dog import Dog   
 
 # 实例化 dog1 对象，在实例化的过程会调用 Dog 类中的 __init__ 函数  
 dog1 = Dog('豆豆', 3)   
 
 # 访问实例属性  
 print('访问实例属性 name: ', dog1.name)   
 
 # 调用方法  
 dog1.sit()  
 dog1.jump()
 ```
 
 ## 8.3  访问限制
 
 示例： dry_03_car.py
 
 ```python
 class Car():      
     '''这是普通的汽车类'''       
     
     def __init__(self, brand, model, year):  
         '''初始化描述汽车的属性'''          
         self.brand = brand          
         self.model = model          
         self.year = year          
         # 初始化时，可以为某些属性指定初始默认值，如下，设置里程表初始值为 0          
         # 以单下划线开始的属性为保护属性          
         # 以双下划线开始的属性为私有属性          
         # 但是 Python 语言里并没有实际的 protected、pravite 界定          
         self._odometer = 0          
         self._oil_tank = 60       
     
     def description(self):          
         '''打印汽车的描述信息'''          
         print('这台汽车是', self.year, '年的', self.brand, self.model)       
         
     def read_odometer(self):          
         '''打印汽车的里程记录'''          
         print('这辆车已经跑了', str(self._odometer), '公里')       
         
     def update_odometer(self, mileage):          
         '''将里程表的里程数设置为 mileage'''          
         if mileage < self._odometer:      
             print('不能将里程表里程数往回调！')  
             return          
         self._odometer = mileage       
         
     def _increase_odometer(self, kilometers):  
         '''在现有的里程数基础上增加 kilometers 公里'''
         self._odometer += kilometers       
         
     def fill_gas(self, liter):          
         '''给汽车加油'''          
         if (self._oil_tank + liter > 60):  
             print('不能加这么多油！油箱最多可以加 60 L，现在油箱已经有', self._oil_tank, '升了')              
             return          
         self._oil_tank += liter          
         print('汽车加了', liter, '升油')       
         
     # 以单下划线开始的函数，是内部函数，尽管，类的外部也能调用 
     # 以双下划线开始的函数，是私有函数，类的外部和子类都不能调用
     def _consume_gas(self, kilometer):          
         '''汽车根据公里数有对应的油耗'''          
         liter = kilometer * 8 / 100 # 按照 100 公里消耗 8 L 油计算          
         self._oil_tank -= liter       
         
     def run(self, kilometers):          
         '''汽车跑了 kilometers 公里'''          
         if (kilometers * 8 / 100 > self._oil_tank):
             print('油箱里的油，跑不了那么远了，请先加油！')  
             return  
         self._increase_odometer(kilometers)
         self._consume_gas(kilometers)      
         print('汽车跑了', kilometers, '公里')
 ```
 
 示例： 040_car_class_access_demo.py
 
 ```python
 from dry_03_car import Car   
 
 myCar = Car('奥迪', 'A6', 2018)  
 myCar.description()   
 
 myCar.run(100)  
 myCar.read_odometer()   
 
 myCar.run(150)  
 myCar.read_odometer()   
 
 myCar.run(300)  
 myCar.read_odometer()   
 
 myCar.run(250)  
 myCar.fill_gas(100)  
 myCar.fill_gas(30)
    
 myCar.read_odometer()  
 myCar._increase_odometer(100)  
 myCar.read_odometer()
 ```
 
 **保护属性和私有属性**
 
 在 Python 中没有 Java 等其他面向对象语言里明确的 Public、Protected和Private等访问限制符来限制属性的访问权限。
 
 在 Python 中以单下划线开始的属性，可以理解成保护属性，但是在类的外面，依然可以访问该属性，只能从形式上和习惯上让其他的代码阅读者明白该属性旨在类的内部和子类中使用。
 
 在 Python 中以双下划线开始的属性，是私有属性，在类的外面和子类中正常情况都无法访问。
 
 **getter 方法和 setter 方法**
 
 **注意**：*上例中的方法 _increase_odometer 类似于保护属性的理解，我们应该只在类的内部去调用该方法，但是在类的外部依然能够调用。如果是以双下划线开始的方法，被称为私有方法，私有方法在类的外部和子类中，没法正常调用，只能在类的内部使用。*
 
 如果，我们定义了私有属性或保护属性，由于在类的外部无法访问或不希望访问，我们就可以在类的内部实现 getter 和 setter 方法，分别实现属性的读和写的操作。如上例中，我们针对 _odometer 的 getter 方法 read_odometer 和 setter 方法 update_odometer。
 
 **Python 解释器对私有属性的处理**
 
 上面已经提到，在 Python 中并不存在真正意义上的私有属性和私有方法。对与一个私有属性 `__var`，Python 解释器会从命名上将其转换成 `_classname__var`，用这个名字，我们依然能够访问到该私有属性。但是，请不要这样操作！
 
 ## 8.4 继承（Is-a）
 
 如上例，我们定义了一个 Car 的类，用来对汽车的属性和行为进行抽象，当有一天，我们需要处理电动汽车的时候，会发现电动汽车的很多属性和行为跟汽车一样，但也有自己新的属性，新的行为，这种情况我们就可以用继承来实现。从抽象的角度来考虑，继承描述的是一种类与类之间纵向的关系。
 
 示例： dry_03_car.py
 
 ```python
 class Car():  	
     -- skip --  
 class ElectricCar(Car):      
     '''这是个电动汽车类，继承自普通的汽车类'''      
     def __init__(self, brand, model, year):      
         '''先初始化父类的属性，再初始化电动汽车特有的属性'''
         super().__init__(brand, model, year)
         self._battery_range= 300       
         
     # 子类新增的方法      
     def battery_info(self):          
         '''打印电池续航信息'''          
         print('电池现在的续航里程数是', self._battery_range)       
         
     def charge(self, kilometers):          
         '''给电动汽车充电'''          
         if self._battery_range + kilometers > 300:
             print('不能充这么多电！电动汽车总续航里程是 300 公里，现在还能跑', self._battery_range,'公里')      
             return          
         self._battery_range += kilometers  
         print('充完电，你的电池续航能力增加了', kilometers, '公里')       
         
     def _consume_electric(self, kilometers):  
         '''电动汽车消耗电能，减少续航里程'''
         self._battery_range -= kilometers       
         
     # 重写父类的方法      
     def fill_gas(self, liter):          
         '''电动汽车不能加油'''          
         print('电动汽车不能加油！')       
         
     def run(self, kilometers):          
         '''电动汽车跑了 kilometers 公里'''          
         if self._battery_range - kilometers <= 0:
             print('电动汽车跑不了那么远了，请先充电！')
             return 
         self._increase_odometer(kilometers)
         self._consume_electric(kilometers)  
         print('电动汽车跑了', kilometers, '公里')
 ```
 
 **继承语法**
 
 我们继续在 dry_03_car.py 模块中增加一个新的类 ElectricCar， 它继承自 Car 类，继承的语法是：class ElectricCar(Car):
 
 最后的园括号内，标明新类 ElectricCar 继承自 Car 类。
 
 **super() 函数**
 
 super() 函数是一个特殊函数，可以将父类和子类关联起来，借以在子类中调用父类的方法。
 
 我们在 ElectricCar 类的初始化方法中，有这样一句代码 
 
 ```python
 super().__init__(brand, model, year)
 ```
 
 **给子类添加新属性和新方法**
 
 ElectricCar 类中的 _battery_range属性就是基于父类的基础添加的新的属性。
 
 battery_info、charge 和 _consume_electric 是在子类中添加的新的方法
 
 **重写父类的方法**
 
 由于电动汽车没法加油，并且在行驶过程中也不会消耗油，所以，父类的 fill_gas 方法和 run 方法在子类中进行了重新实现，也被称为重写。
 
 ## 8.5 复合（Has-a）
 
 上一节我们提到的继承，是一种类与类之间的纵向关系，表示的是一种 Is-a 的关系，比如我们可以说 ElectricCar is a Car。
 
 但是，有时候，我们也需要一种横向的类与类之间的关系，比如当 ElectricCar 类中，当关于电池的属性和行为越来越多后，我们可以把电池单独抽象出来一个类 Battery，然后，Battery 类的一个实例作为 ElectricCar 类中的一个属性。这就是复合。它表示的是一种 Has-a 的关系，比如，我们可以说 ElectricCar has a battery。
 
 示例：dry_03_car.py
 
 ```python
 class Car():  	
     -- skip --  
 class Battery():      
     '''这是电动车的电池类'''      
     def __init__(self, battery_range=300):
         self._battery_range = battery_range       
         
     def battery_info(self):          
         '''打印电池续航信息'''          
         print('电池现在的续航里程数是', self._battery_range)       
         
     def charge(self, kilometers):          
         '''给电动汽车充电'''          
         if self._battery_range + kilometers > 300:
             print('不能充这么多电！电动汽车总续航里程是 300 公里，现在还能跑', self._battery_range,'公里')      
             return          
         self._battery_range += kilometers  
         print('充完电，你的电池续航能力增加了', kilometers, '公里')       
         
     def consume_electric(self, kilometers):      
         '''消耗电池，减少续航里程'''  
         self._battery_range -= kilometers       
         
     def if_enough(self, kilometers):          
         '''是否能够支持给定的里程'''          
         if self._battery_range <= kilometers:  
             return False          
         else:              
             return True    
             
 class ElectricCar(Car):      
     '''这是个电动汽车类，继承自普通的汽车类'''      
     def __init__(self, brand, model, year):      
         '''先初始化父类的属性，再初始化电动汽车特有的属性'''
         super().__init__(brand, model, year)
         self.battery = Battery()       
         
     # 重写父类的方法      
     def fill_gas(self, liter):          
         '''电动汽车不能加油'''          
         print('电动汽车不能加油！')       
         
     def run(self, kilometers):          
         '''电动汽车跑了 kilometers 公里'''          
         if not self.battery.if_enough(kilometers):
             print('电动汽车跑不了那么远，请先充电！')
             return 
         self._increase_odometer(kilometers)
         self.battery.consume_electric(kilometers)
         print('电动汽车跑了', kilometers, '公里')
 ```
 
 



