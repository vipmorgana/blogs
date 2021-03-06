# Python之路 - 面向对象
<!-- TOC -->

- [Python之路 - 面向对象](#python之路---面向对象)
    - [前言  🍀](#前言--🍀)
    - [类与实例  🍀](#类与实例--🍀)
    - [属性与方法  🍀](#属性与方法--🍀)
    - [构造函数  🍀](#构造函数--🍀)
    - [命名空间  🍀](#命名空间--🍀)
    - [属性(静态和动态)与类的关系  🍀](#属性静态和动态与类的关系--🍀)
    - [对象交互与类的组合  🍀](#对象交互与类的组合--🍀)

<!-- /TOC -->
## 前言  🍀

编程范式

编程是程序员用 特定的语法 + 数据结构 + 算法组成的代码来告诉计算机如何执行任务的过程 , 而实现一个任务的方式有很多种不同的方式 ,  对这些不同的编程方式的特点进行归纳总结得出来的编程方式类别，即为编程范式

- 面向过程编程  Procedural Programming

面向过程编程就是程序从上到下一步步执行 , 基本设计思路就是程序一开始是要着手解决一个大的问题 , 然后把一个大问题分解成很多个小问题或子过程 , 这写子过程再执行的过程再继续分解直到小问题足够简单到可以在一个小步骤范围内解决

在Python中 , 我们通过把大段代码拆成函数 , 通过一层一层的函数调用 , 就可以把复杂任务分解成简单的任务 , 这种分解可以称之为面向过程的程序设计 . 函数就是面向过程的程序设计的基本单元

- 函数式编程  Functional Programming

函数式编程就是一种抽象程度很高的编程范式 , 纯粹的函数式编程语言编写的函数没有变量 , 函数式编程的一个特点就是 , 允许把函数本身作为参数传入另一个函数 , 还允许返回一个函数  , Python对函数式编程提供部分支持 . 由于Python允许使用变量 , 因此 , Python不是纯函数式编程语言

- 面向对象编程  Object Oriented Programming

面向对象编程是利用"类"和"对象"来创建各种模型来实现对真实世界的描述 , 使用面向对象编程的原因一方面是因为它可以使程序的维护和扩展变得更简单 , 并且可以大大提高程序开发效率 , 另外 , 基于面向对象的程序可以使它人更加容易理解你的代码逻辑 , 从而使团队开发变得更从容

## 类与实例  🍀

类的语法

```python
class 类名:
    pass
```

一个栗子🌰

```python
# 创建一个人的'类',首字母要大写
class Person(object):
    # 构造函数,初始化属性
    def __init__(self,name):
        self.name = name
	# 人可以吃饭
    def eat(self):
    	print("I am eatting")
# 创造了一个叫做'Lyon'的人        
p = Person('Lyon')
# 执行吃饭功能
p.eat()
# 执行结果: I am eatting
```

* 类 (class)  

类就是 `对现实生活中一类具有共同特征事物的抽象` 

类起到一个模板的作用 , 当我们创建一个类时 , 就相当于创建了一个初始的'模型' , 我们可以通过这个'模型' 来创建出一个个具有相同特征或功能的事物 , 来帮助我们更好的处理问题

在上述栗子中类名Person 后有一个` (object) ` , 这是新式类的写法 , 而在python3.x 以上的版本中 , 默认为新式类 , 所以也可直接 ` class Person: ` 

我们创建类时 , 都默认继承了object类 , object详解见后期文章

* 实例 (instance)

我们知道类是一个抽象 , 既然是抽象那就是不可操作的 , 所以我们如果进行操作 , 就需要将这一抽象的概念变成具体的事物 , 这个过程我们称为实例化

实例化: ` 由抽象的类转换成实际存在的对象的过程 `

实例: ` 由类进行实例化所得到的对象 `  , 上述栗子中的 ` p ` 就是一个实例

## 属性与方法  🍀

属性是实体的描述性质或特征 , 比如人有名字 , 年龄 , 性别等 . 当然还有人所能做的事情也是一种属性 , 比如吃饭 , 睡觉 , 喝水等 . 对于这两种属性 , 一种是表示特征的 , 叫做静态属性 , 另一种则是表示功能的 , 叫做动态属性

在Python中 , 我们将***静态属性*** 就称为` 属性 `  , 将***动态属性*** 就称为` 方法  `  , 并且以变量来表示属性 , 以函数表示方法 , 见下图:

![object_attr](http://oux34p43l.bkt.clouddn.com/object_attr.png?imageMogr2/blur/1x0/quality/75|watermark/2/text/bHlvbi55YW5nQHFxLmNvbQ==/font/YXBhcmFqaXRh/fontsize/560/fill/Izk0ODI4Mg==/dissolve/100/gravity/SouthEast/dx/10/dy/10)

*PS:类中的函数已经不叫函数了 , 而叫做方法* 


调用方式: 类名 . 属性名

```python
class Person:
    # 类变量
    role = 'student'
    # 构造函数
    def __init__(self,name):
        # 实例变量
        self.name = name
```


调用方式: 类名 . 方法名( )

```python
class Person:
    # 普通方法
    def eat(self):
        pass
```

***特殊的类属性***

| 属性名            | 说明                |
| -------------- | ----------------- |
| \_\_dict\_\_   | 查看类或对象成员 , 返回一个字典 |
| \_\_name\_\_   | 查看类的名字            |
| \_\_doc\_\_    | 查看类的描述信息 , 即注释部分  |
| \_\_base\_\_   | 查看第一个父类           |
| \_\_bases\_\_  | 查看所有父类 , 返回一个元组   |
| \_\_module\_\_ | 查看类当前所在模块         |
| \_\_class\_\_  | 查看对象通过什么类实例化而来    |

PS:对于属性和方法 , 在网上分类各种各样的都有 , 比如字段 , 还有菜鸟教程中的一些 , 其实本质上都是一个东西

## 构造函数  🍀

在上述例子中 , 可以看到有一个\_\_init\_\_ 方法 , 这个方法叫做构造方法 , 用于初始化属性 , 所以如果我们要设置属性 , 那么构造方法是必须要的

> ***self*** 

我们直接通过实例来说明

```python
class Foo:
    def __init__(self,name):
        self.name = name
    def func(self):
        print(id(self))
a = Foo('Lyon')
# 打印实例a的内存地址
print(id(a))
# 调用类中的func方法,即打印self的内存地址
a.func()
'''
执行结果:
1703689404544
1703689404544
结果分析:
我们发现a的内存地址和self的内存地址是一样的,也就是说self其实就是实例本身
那么在我们进行实例化的时候,self.name = name 就是给实例添加一个name属性,该属性的值就是我们在实例化时传入的'Lyon'
所以如果我们需要给对象添加属性的话,可以直接通过 对象.属性名 = 属性值 的方式进行添加
'''
```

将上栗子中的构造函数再换个姿势看看

```python
a = Foo('Lyon')
# 等价于如下,用类名调用类中的方法
Foo.__init__(a,'Lyon')
# Python解释器会帮我们自动触发__init__方法,所以再如下
Foo(a,'Lyon')
```

## 命名空间  🍀

在函数中 , Python解释器在执行时 , 会将函数名称依次加载到命名空间 , 类当然也一样

我们创建一个类时 , Python解释器一执行就会创建一个类的命名空间 , 用来存储类中定义的所有名称( 属性和方法 ) , 而我们进行实例化时 , Python解释器又会为我们创建一个实例命名空间 , 用来存放实例中的名称

当我们利用 ` 类名. 名称 `  来访问对象属性 ( 静态与动态 ) 时 , Python解释器会先到该对象的命名空间中去找**该名称**  , 找不到就再到类 ( 该对象实例化之前的类 ) 的命名空间中去找 , 最后如果都没找到 , 那么就抛出异常了 

访问属性实例

```python
class A(object):
    """
    这是一个类
    """
    pass
a = A()
# 访问实例a的__doc__属性
print(a.__doc__)
'''
执行结果:

    这是一个类
    
'''
```

解释说明: 对于实例a本身是肯定没有\_\_doc\_\_ 属性的 , 这毋庸置疑 , 因为我们根本就没有使用构造函数来增加实例属性 . 根据执行结果显示 , 我们是访问到了这个类中的\_\_doc\_\_ 属性 , 那么你会说这个类也没看见 \_\_doc\_\_ 属性啊 , 其实类A是有的 , 因为它继承了object类 , 至于object类是什么 , 它里面有什么 ? 看后续文章吧

## 属性(静态和动态)与类的关系  🍀

由于Python是动态语言 , 所以Python的赋值机制都是通过动态绑定来实现的

> **类属性共享给所有对象**

先实例后说明

```python
class Foo:
    # 定义一个类变量,特意用的容器类型来说明
    name = ['Lyon']
# 实例化
a = Foo()
b = Foo()
# 访问a,b中的name属性
print('实例a中的name属性:', a.name)
print('实例b中的name属性:', b.name)
# 查看a,b,Foo中name属性的内存地址
print(id(a.name))
print(id(b.name))
print(id(Foo.name))
print('------------------')
# 修改类变量
Foo.name = 'a'
# 再次访问a,b中的name属性
print('实例a中的name属性:', a.name)
print('实例b中的name属性:', b.name)
# 修改a中的name属性? 不,是新增
a.name = ['Lyon']
# 再次查看a,b中name属性的内存地址
print(id(a.name))
print(id(b.name))
'''
执行结果:
实例a中的name属性: ['Lyon']
实例b中的name属性: ['Lyon']
2247471754696
2247471754696
2247471754696
------------------
实例a中的name属性: a
实例b中的name属性: a
2247471792392
2247471754696
'''
```

说明: 

1. 特意使用容器类型来进行实验 , 因为在Python中容器类型内存地址一样只有一个原因 , 那就是两者作用的是同一个对象 
2. 我们第一步查看内存地址时 , a, b, Foo三者中的name属性的内存地址是一样的 , 实例可以通过 ` 实例.类变量名 ` 的方式进行访问 , 并且所有实例都共享类属性name
3.  ` a.name = ['Lyon'] `  这一步其实并不是修改a中的name属性 , 要知道name属性是类的并不是实例的 , 执行这一步会为实例a加上一个新的同名name属性 , 由于赋值绑定会将原来访问类属性name的通道破坏掉 , 但是并不会影响b对类属性name的访问

> **类中的方法是绑定到所有对象的** 

先实例后说明

```python
class Foo:
    def func(self):
        pass
a = Foo()
b = Foo()
# 打印a,b中func的内存地址
print(a.func)
print(b.func)
# id返回的是10进制表示的内存地址,转换成16进制
print(hex(id(a)))
print(hex(id(b)))
'''
执行结果:
<bound method Foo.func of <__main__.Foo object at 0x000001A7D2F74080>>
<bound method Foo.func of <__main__.Foo object at 0x000001A7D3759898>>
0x1a7d2f74080
0x1a7d3759898
'''
```

说明:

1. 方法名与内存地址存在一个映射关系 , 通过执行结果我们可以发现 , a.func所在的内存地址与a的内存地址是一样的 , 则说明func绑定到了a中
2. a.func 与b.func 的内存地址是不一样的 , 因为每一个实例都开辟了自己内存空间 , func绑定进去的位置自然不一样

> **实例本身的属性是实例独有的**

我们通过类创建一个实例 , 就会在内存中新开辟一块内存空间来存放这个实例的所有属性 , 实例属性一旦创建 , 基本跟类就没有什么太大的关系了 . 如果要修改实例属性那么就只能通过实例来进行修改了 , 并且实例与实例之间也是互不干扰的

如下图中 , 类与实例 , 实例与实例 都开辟了自己的内存空间

![memory_space](http://oux34p43l.bkt.clouddn.com/memory_space?imageMogr2/blur/1x0/quality/75|watermark/2/text/bHlvbi55YW5nQHFxLmNvbQ==/font/YXBhcmFqaXRh/fontsize/560/fill/Izk0ODI4Mg==/dissolve/100/gravity/SouthEast/dx/10/dy/10)

## 对象交互与类的组合  🍀

对象交互

```python
class Person:
    def __init__(self, name):
        self.name = name
    def attack(self,per):
        print("{} attacked {}".format(self.name, per.name))
lyon = Person("Lyon")
kenneth = Person("kenneth")
lyon.attack(kenneth)
# 执行结果: Lyon attacked kenneth
```

类的组合

传参时组合

```python
class BirthDate:
    def __init__(self, year, month, day):
        self.year = year
        self.month = month
        self.day = day
class Person:
    def __init__(self, name, birthdate):
        self.name = name
        self.birthdate = birthdate
p = Person('Lyon', BirthDate(2000, 1, 1))
```

定义时组合

```python
class BirthDate:
    def __init__(self, year, month, day):
        self.year = year
        self.month = month
        self.day = day
class Person:
    def __init__(self, name, year, month, day):
        self.name = name
        self.birthdate = BirthDate(year, month, day)
p = Person('Lyon', 2000, 1, 1)
```











