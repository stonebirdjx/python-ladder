<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [基本定制](#%E5%9F%BA%E6%9C%AC%E5%AE%9A%E5%88%B6)
  - [:point_right:`__new__`(cls[, ...]) -- 创建新实例](#point_right__new__cls-----%E5%88%9B%E5%BB%BA%E6%96%B0%E5%AE%9E%E4%BE%8B)
  - [:point_right:`__init__`(self[, ...]) -- 初始化类](#point_right__init__self-----%E5%88%9D%E5%A7%8B%E5%8C%96%E7%B1%BB)
  - [:point_right:`__del__`(self) -- 在实例将被销毁时调用](#point_right__del__self----%E5%9C%A8%E5%AE%9E%E4%BE%8B%E5%B0%86%E8%A2%AB%E9%94%80%E6%AF%81%E6%97%B6%E8%B0%83%E7%94%A8)
  - [:point_right:`__repr__`(self) -- 用字符串的方式输出](#point_right__repr__self----%E7%94%A8%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E6%96%B9%E5%BC%8F%E8%BE%93%E5%87%BA)
  - [`__str__`(self) -- 用字符串的方式输出](#__str__self----%E7%94%A8%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E6%96%B9%E5%BC%8F%E8%BE%93%E5%87%BA)
  - [`__bytes__(self)` --  对象的字节串输出](#__bytes__self-----%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%AD%97%E8%8A%82%E4%B8%B2%E8%BE%93%E5%87%BA)
  - [`__format__`(self, format_spec) -- 格式化输出](#__format__self-format_spec----%E6%A0%BC%E5%BC%8F%E5%8C%96%E8%BE%93%E5%87%BA)
  - [`__hash__`(self) -- 计算hash值](#__hash__self----%E8%AE%A1%E7%AE%97hash%E5%80%BC)
  - [:point_right:`__bool__`(self) -- 真值检查](#point_right__bool__self----%E7%9C%9F%E5%80%BC%E6%A3%80%E6%9F%A5)
- [比较](#%E6%AF%94%E8%BE%83)
  - [`__lt__`(self, other) -- 小于](#__lt__self-other----%E5%B0%8F%E4%BA%8E)
  - [`__le__`(self, other) -- 小于等于](#__le__self-other----%E5%B0%8F%E4%BA%8E%E7%AD%89%E4%BA%8E)
  - [`__eq__`(self, other) -- 等于](#__eq__self-other----%E7%AD%89%E4%BA%8E)
  - [`__ne__`(self, other) -- 不等于](#__ne__self-other----%E4%B8%8D%E7%AD%89%E4%BA%8E)
  - [`__gt__`(self, other) -- 小于](#__gt__self-other----%E5%B0%8F%E4%BA%8E)
  - [`__ge__`(self, other) -- 小于等于](#__ge__self-other----%E5%B0%8F%E4%BA%8E%E7%AD%89%E4%BA%8E)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

> 魔法方法让类拥有一些额外的属性

# 基本定制

## :point_right:`__new__`(cls[, ...]) -- 创建新实例

`__new__()` 是一个静态方法，创建一个 *cls* 类的新实例。

如果 `__new__() ` 在构造对象期间被发起调用并且它返回了一个 cls 的实例，则新实例的 __init__() 方法将以 __init__(self[, ...]) 的形式被发起调用，其中 self 为新实例而其余的参数与被传给对象构造器的参数相同。

> __new__()必须有返回值，返回实例化出来的实例。常用于单例类

```python
class Singleton(object):
    _instance = None

    def __new__(cls, age:str, name:str):
        if not cls._instance:
            cls._instance = object.__new__(cls) # super的__new__只有一个参数
        return cls._instance
        
        def __init__(self,age,name):
            self.age = age
            self.name = name

s1 = Singleton('h',"18")
s2 = Singleton('j',"19") # 返回s1

print(s1 == s2) # True
```

## :point_right:`__init__`(self[, ...]) -- 初始化类

在实例 (通过 `__new__()`) 被创建之后，返回调用者之前调用。其参数与传递给类构造器表达式的参数相同。

因为对象是由 __new__() 和 __init__() 协作构造完成的 (由 __new__() 创建，并由 __init__() 定制)，

>  所以 __init__() 返回的值只能是 None，否则会在运行时引发 TypeError。

```python
class Stonebird(object):
    def __init__(self,name,age) -> None:
        self.__name = name
        self.__age  = age

s = Stonebird("stone",18)
```

## :point_right:`__del__`(self) -- 在实例将被销毁时调用

如果一个基类具有 `__del__()` 方法，则其所派生的类如果也有 `__del__()` 方法，就必须显式地调用它以确保实例基类部分的正确清除。

```Python
class Item:
    def __init__ (self, name, price):
        self.name = name
        self.price = price
    # 定义析构函数
    def __del__ (self):
        print('del删除对象')

i = Item('stone', '18')
del i  # del删除对象

print('Done')
```

## :point_right:`__repr__`(self) -- 用字符串的方式输出

由 repr() 内置函数调用以输出一个对象的“官方”字符串表示。返回值必须是一个字符串对象。

__repr__：是由repr()内置函数调用，用来输出一个对象的“官方”字符串表示。返回值必须是字符串对象，此方法通常被用于调试。内置类型 object 所定义的默认实现会调用 object.__repr__()。

print(cls())时输出 

```Python
class Stonebird:
    def __init__ (self, name, price):
        self.name = name
        self.price = price
    
    def __repr__(self) -> str:
         return self.name
    
    def __str__(self) -> str:
        return self.name
    
s = Stonebird("stone", 18)
print(s) # stone
```

## `__str__`(self) -- 用字符串的方式输出

__str__：通过str(object)以及内置函数format()和print()调用以生成一个对象的“非正式”或格式良好的字符串表示。返回值必须是字符串对象。

```Bash
>>> print(repr('4'))
'4'
>>> 
>>> print(str('4'))
4
```

## `__bytes__(self)` --  对象的字节串输出

通过 bytes 调用以生成一个对象的字节串表示。这应该返回一个 bytes 对象。

```python
class Stonebird:
    def __init__(self) -> None:
        pass

    def __bytes__(self) -> bytes:
        return b'test'

print(bytes(Stonebird())) # b'test'
```

## `__format__`(self, format_spec) -- 格式化输出

通过 [`format()`](https://docs.python.org/zh-cn/3.11/library/functions.html#format) 内置函数、扩展、[格式化字符串字面值](https://docs.python.org/zh-cn/3.11/reference/lexical_analysis.html#f-strings) 的求值以及 [`str.format()`](https://docs.python.org/zh-cn/3.11/library/stdtypes.html#str.format) 方法调用以生成一个对象的“格式化”字符串表示。 *format_spec* 参数为包含所需格式选项描述的字符串。

```python
class Stonebird:
    def __init__ (self, name):
        self.name = name

    
    def __format__(self, code):
        return 'x: {}, y: {}'.format(self.name, code)
        # 使用变量format 
        # return 'x: {x}, y: {y}'.format(x = self.name, y = code) 
    
print(format(Stonebird("stone"),"haha")) # x: stone, y: haha
```

## `__hash__`(self) -- 计算hash值

通过内置函数 [`hash()`](https://docs.python.org/zh-cn/3.11/library/functions.html#hash) 调用以对哈希集的成员进行操作，属于哈希集的类型包括 [`set`](https://docs.python.org/zh-cn/3.11/library/stdtypes.html#set)、[`frozenset`](https://docs.python.org/zh-cn/3.11/library/stdtypes.html#frozenset) 以及 [`dict`](https://docs.python.org/zh-cn/3.11/library/stdtypes.html#dict)。`__hash__()` 应该返回一个整数。

```python
class Stonebird:
    def __init__ (self, name, price):
        self.name = name
        self.price = price
    
    def __hash__(self) -> int:
        return hash((self.name, self.price)) # 一个参数
    
s = Stonebird("stone", 18)
print(hash(s))  # -7134643804844694873
```

## :point_right:`__bool__`(self) -- 真值检查

此方法以实现真值检测以及内置的 bool() 操作；应该返回 False 或 True。如果未定义此方法，则会查找并调用 `__len__`() 并在其返回非零值时视对象的逻辑值为真。如果一个类既未定义` __len__`() 也未定义 `__bool__`() 则视其所有实例的逻辑值为真。

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __bool__(self):
        if self.age < 18 or self.age > 65:
            return False
        return True

if __name__ == '__main__':
    person = Person('Jane', 16)
    print(bool(person))  # False
```

# 比较

## `__lt__`(self, other) -- 小于

`x<y` 调用 `x.__lt__(y)`

```python
class weight:
  def __init__(self, weight):
    self. weight= weight
  def __lt__(self,other):
    return self.weight < other.weight
a=weight(50)
b=weight(60)
print(a<b)  # True
```

## `__le__`(self, other) -- 小于等于

`x<=y` 调用 `x.__le__(y)`

```python
class weight:
  def __init__(self, weight):
    self. weight= weight
  def __le__(self,other):
    return self.weight<=other.weight
a=weight(50)
b=weight(60)
print(a <= b) # True
```

## `__eq__`(self, other) -- 等于

`x==y` 调用 `x.__eq__(y)`

```python
class weight:
  def __init__(self, weight):
    self. weight= weight
  def __eq__(self,other):
    return self.weight == other.weight
a=weight(50)
b=weight(60)
print(a = b) # False
```

## `__ne__`(self, other) -- 不等于

`x!=y` 调用 `x.__ne__(y)`

```python
class weight:
  def __init__(self, weight):
    self. weight= weight
  def __ne__(self,other):
    return self.weight != other.weight
a=weight(50)
b=weight(60)
print(a != b)  # True
```

## `__gt__`(self, other) -- 小于

`x>y` 调用 `x.__gt__(y)`

```python
class weight:
  def __init__(self, weight):
    self. weight= weight
  def __gt__(self,other):
    return self.weight < other.weight
a=weight(50)
b=weight(60)
print(a < b) # False
```

## `__ge__`(self, other) -- 小于等于

`x>=y` 调用 `x.__ge__(y)`。

```python
class weight:
  def __init__(self, weight):
    self. weight= weight
  def __ge__(self,other):
    return self.weight <= other.weight
a=weight(50)
b=weight(60)
print(a <= b) # False
```

