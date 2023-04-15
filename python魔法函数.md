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
  - [`__match_args__`(self, args)  -- 模式匹配](#__match_args__self-args-----%E6%A8%A1%E5%BC%8F%E5%8C%B9%E9%85%8D)
- [比较](#%E6%AF%94%E8%BE%83)
  - [`__lt__`(self, other) -- 小于](#__lt__self-other----%E5%B0%8F%E4%BA%8E)
  - [`__le__`(self, other) -- 小于等于](#__le__self-other----%E5%B0%8F%E4%BA%8E%E7%AD%89%E4%BA%8E)
  - [`__eq__`(self, other) -- 等于](#__eq__self-other----%E7%AD%89%E4%BA%8E)
  - [`__ne__`(self, other) -- 不等于](#__ne__self-other----%E4%B8%8D%E7%AD%89%E4%BA%8E)
  - [`__gt__`(self, other) -- 小于](#__gt__self-other----%E5%B0%8F%E4%BA%8E)
  - [`__ge__`(self, other) -- 小于等于](#__ge__self-other----%E5%B0%8F%E4%BA%8E%E7%AD%89%E4%BA%8E)
- [自定义属性访问](#%E8%87%AA%E5%AE%9A%E4%B9%89%E5%B1%9E%E6%80%A7%E8%AE%BF%E9%97%AE)
  - [`__getattr__`(self, *name*) -- 访问实例属性](#__getattr__self-name----%E8%AE%BF%E9%97%AE%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7)
  - [`__getattribute__`(*self*, *name*) - -- 访问实例属性](#__getattribute__self-name------%E8%AE%BF%E9%97%AE%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7)
  - [`__setattr__`(*self*, *name*, *value*)  -- 设置实例属性](#__setattr__self-name-value-----%E8%AE%BE%E7%BD%AE%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7)
  - [`__delattr__`(*self*, *name*)  -- 删除实例属性](#__delattr__self-name-----%E5%88%A0%E9%99%A4%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7)
  - [:point_right:`__dir__`(*self*) -- 被调用的列表](#point_right__dir__self----%E8%A2%AB%E8%B0%83%E7%94%A8%E7%9A%84%E5%88%97%E8%A1%A8)
  - [`__get__`(*self*, *instance*, *owner=None*) -- 获取实例属性值](#__get__self-instance-ownernone----%E8%8E%B7%E5%8F%96%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7%E5%80%BC)
  - [`__set__`(*self*, *instance*, *value*) -- 设置实例属性值](#__set__self-instance-value----%E8%AE%BE%E7%BD%AE%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7%E5%80%BC)
  - [`__delete__`(*self*, *instance*) -- 删除实例属性值](#__delete__self-instance----%E5%88%A0%E9%99%A4%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7%E5%80%BC)
  - [:point_right:`__slots__`  -- 声明数据成员](#point_right__slots__-----%E5%A3%B0%E6%98%8E%E6%95%B0%E6%8D%AE%E6%88%90%E5%91%98)
- [自定义类创建](#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%B1%BB%E5%88%9B%E5%BB%BA)
  - [:point_right:`__init_subclass__`(*cls*) -- 子类初始化调用](#point_right__init_subclass__cls----%E5%AD%90%E7%B1%BB%E5%88%9D%E5%A7%8B%E5%8C%96%E8%B0%83%E7%94%A8)
  - [:point_right:`__set_name__`(*self*, *owner*, *name*) -- 将类属性的名称绑定到类对象上。](#point_right__set_name__self-owner-name----%E5%B0%86%E7%B1%BB%E5%B1%9E%E6%80%A7%E7%9A%84%E5%90%8D%E7%A7%B0%E7%BB%91%E5%AE%9A%E5%88%B0%E7%B1%BB%E5%AF%B9%E8%B1%A1%E4%B8%8A)
  - [:point_right:metaclass -- 元类](#point_rightmetaclass----%E5%85%83%E7%B1%BB)
  - [:point_right:`__mro_entries__`(*self*, *bases*) -- 控制调用顺序](#point_right__mro_entries__self-bases----%E6%8E%A7%E5%88%B6%E8%B0%83%E7%94%A8%E9%A1%BA%E5%BA%8F)
  - [:point_right:`__prepare__`(name, bases, **kwds) -- 属性和方法的定义顺序](#point_right__prepare__name-bases-kwds----%E5%B1%9E%E6%80%A7%E5%92%8C%E6%96%B9%E6%B3%95%E7%9A%84%E5%AE%9A%E4%B9%89%E9%A1%BA%E5%BA%8F)
- [自定义实例及子类检查](#%E8%87%AA%E5%AE%9A%E4%B9%89%E5%AE%9E%E4%BE%8B%E5%8F%8A%E5%AD%90%E7%B1%BB%E6%A3%80%E6%9F%A5)
  - [:point_right:`__instancecheck__`(*self*, *instance*) -- 当前类型检查行为](#point_right__instancecheck__self-instance----%E5%BD%93%E5%89%8D%E7%B1%BB%E5%9E%8B%E6%A3%80%E6%9F%A5%E8%A1%8C%E4%B8%BA)
  - [:point_right:`__subclasscheck__`(*self*, *subclass*) -- 子类检查行为](#point_right__subclasscheck__self-subclass----%E5%AD%90%E7%B1%BB%E6%A3%80%E6%9F%A5%E8%A1%8C%E4%B8%BA)
- [模拟泛型类型](#%E6%A8%A1%E6%8B%9F%E6%B3%9B%E5%9E%8B%E7%B1%BB%E5%9E%8B)
  - [:point_right:`__class_getitem__`(*cls*, *key*) -- 创建泛型类时自定义类的行为](#point_right__class_getitem__cls-key----%E5%88%9B%E5%BB%BA%E6%B3%9B%E5%9E%8B%E7%B1%BB%E6%97%B6%E8%87%AA%E5%AE%9A%E4%B9%89%E7%B1%BB%E7%9A%84%E8%A1%8C%E4%B8%BA)
- [模拟可调用](#%E6%A8%A1%E6%8B%9F%E5%8F%AF%E8%B0%83%E7%94%A8)
  - [:point_right:`__call__`(*self*[, *args...*]) -- 将对象当作函数调用时行为](#point_right__call__self-args----%E5%B0%86%E5%AF%B9%E8%B1%A1%E5%BD%93%E4%BD%9C%E5%87%BD%E6%95%B0%E8%B0%83%E7%94%A8%E6%97%B6%E8%A1%8C%E4%B8%BA)
- [模拟容器类型](#%E6%A8%A1%E6%8B%9F%E5%AE%B9%E5%99%A8%E7%B1%BB%E5%9E%8B)
  - [:point_right:`__len__`(*self*) -- 获取对象长度](#point_right__len__self----%E8%8E%B7%E5%8F%96%E5%AF%B9%E8%B1%A1%E9%95%BF%E5%BA%A6)
  - [`__length_hint__`(*self*) -- 获取预估长度](#__length_hint__self----%E8%8E%B7%E5%8F%96%E9%A2%84%E4%BC%B0%E9%95%BF%E5%BA%A6)
  - [:point_right:`__getitem__`(*self*, *key*) -- 通过key获取元素值](#point_right__getitem__self-key----%E9%80%9A%E8%BF%87key%E8%8E%B7%E5%8F%96%E5%85%83%E7%B4%A0%E5%80%BC)
  - [:point_right:`__setitem__`(*self*, *key*, *value*) --  通过key设置元素值](#point_right__setitem__self-key-value-----%E9%80%9A%E8%BF%87key%E8%AE%BE%E7%BD%AE%E5%85%83%E7%B4%A0%E5%80%BC)
  - [:point_right:`__delitem__`(*self*, *key*) -- 删除元素](#point_right__delitem__self-key----%E5%88%A0%E9%99%A4%E5%85%83%E7%B4%A0)
  - [:point_right:`__missing__`(*self*, *key*) -- key不存在时处理](#point_right__missing__self-key----key%E4%B8%8D%E5%AD%98%E5%9C%A8%E6%97%B6%E5%A4%84%E7%90%86)
  - [:point_right:`__iter__`(*self*) -- 返回一个迭代器对象](#point_right__iter__self----%E8%BF%94%E5%9B%9E%E4%B8%80%E4%B8%AA%E8%BF%AD%E4%BB%A3%E5%99%A8%E5%AF%B9%E8%B1%A1)
  - [:point_right:`__reversed__`(*self*) -- 反向迭代行为](#point_right__reversed__self----%E5%8F%8D%E5%90%91%E8%BF%AD%E4%BB%A3%E8%A1%8C%E4%B8%BA)
  - [:point_right:`__contains__`(*self*, *item*) -- 检查是否包含对象](#point_right__contains__self-item----%E6%A3%80%E6%9F%A5%E6%98%AF%E5%90%A6%E5%8C%85%E5%90%AB%E5%AF%B9%E8%B1%A1)
- [with 语句上下文管理器](#with-%E8%AF%AD%E5%8F%A5%E4%B8%8A%E4%B8%8B%E6%96%87%E7%AE%A1%E7%90%86%E5%99%A8)
  - [:point_right:`__enter__`(*self*)](#point_right__enter__self)
  - [:point_right:`__exit__`(*self*, *exc_type*, *exc_value*, *traceback*)](#point_right__exit__self-exc_type-exc_value-traceback)
- [异步协程](#%E5%BC%82%E6%AD%A5%E5%8D%8F%E7%A8%8B)
  - [:point_right:`__await__`(*self*) -- 可等待对象](#point_right__await__self----%E5%8F%AF%E7%AD%89%E5%BE%85%E5%AF%B9%E8%B1%A1)
  - [:point_right:`__aiter__`(*self*)](#point_right__aiter__self)
  - [:point_right:`__anext__`(*self*)](#point_right__anext__self)
- [异步上下文](#%E5%BC%82%E6%AD%A5%E4%B8%8A%E4%B8%8B%E6%96%87)
  - [`__aenter__`(*self*)](#__aenter__self)
  - [`__aexit__`(*self*, *exc_type*, *exc_value*, *traceback*)](#__aexit__self-exc_type-exc_value-traceback)
- [模拟数字类型](#%E6%A8%A1%E6%8B%9F%E6%95%B0%E5%AD%97%E7%B1%BB%E5%9E%8B)

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

## `__match_args__`(self, args)  -- 模式匹配

实例在进行模式匹配（pattern matching）时的行为

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __match_args__(self, args):
        if len(args) == 2 and args[0] == self.name and args[1] == self.age:
            return True
        else:
            return False

# 创建一个 Person 对象
person = Person("John", 30)

# 使用模式匹配语法进行匹配
match_result = match person:
    case ("John", 30):
        print("Name and age match.")
    case _:
        print("No match.")

# 输出:
# Name and age match.
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

# 自定义属性访问

"属性"指的是名称为所有者类 `__dict__`中的特征属性的键名的属性。

## `__getattr__`(self, *name*) -- 访问实例属性

当默认属性访问因引发 AttributeError 而失败时被调用 (可能是调用` __getattribute__`() 时由于 name 不是一个实例属性或 self 的类关系树中的属性而引发了 AttributeError；或者是对 name 特性属性调用 `__get__`() 时引发了 AttributeError)。

```python
class ObjectDict(dict):
    def __init__(self, *args, **kwargs):
        super(ObjectDict, self).__init__(*args, **kwargs)

    def __getattr__(self, name):
        value =  self[name]
        if isinstance(value, dict):
            value = ObjectDict(value)
        return value

if __name__ == '__main__':
    od = ObjectDict(asf={'a': 1}, d=True)
    print(od.asf) #{'a':1}
    print(od.asf.a) # 1
    print(od.d) # true
```

## `__getattribute__`(*self*, *name*) - -- 访问实例属性 

此方法会无条件地被调用以实现对类实例属性的访问。如果类还定义了 `__getattr__`()，则后者不会被调用，除非 `__getattribute__`() 显式地调用它或是引发了 AttributeError。

```python
class StoneBird(object):
    def __init__(self,name):
        self.name = name
    def __getattribute__(self,obj):
        return object.__getattribute__(self,obj)
sb = StoneBird("stone")
print(sb.name) # stone
```

## `__setattr__`(*self*, *name*, *value*)  -- 设置实例属性

在一个属性被尝试赋值时被调用。这个调用会取代正常机制（即将值保存到实例字典）。 *name* 为属性名称， *value* 为要赋给属性的值。

```python
class StoneBird(object):
    def __init__(self, name, alias):
        self.name = name
        self.alias = alias

    def __setattr__(self, key, value):
        # 需要用的__dict__属性
        # self.__dict__[key] = value  
        super().__setattr__(key, value)  # 二者在一定在不存在 __getattrbute__ 时，效果是一样的
        # self.key = value  # 如果还这样调用会出现无限递归的情况
sb = StoneBird("stone","bird")
sb.age = 18
```

## `__delattr__`(*self*, *name*)  -- 删除实例属性

类似于 `__setattr__`() 但其作用为删除而非赋值。此方法应该仅在 del obj.name 对于该对象有意义时才被实现。

```python
class StoneBird:
    def __delattr__(self, name):
        print "deleting `{}`".format(str(name))
        del self.__dict__[name]
        print "`{}` deleted".format(str(name))
```

## :point_right:`__dir__`(*self*) -- 被调用的列表

此方法会在对相应对象调用 dir() 时被调用。返回值必须为一个序列。 dir() 会把返回的序列转换为列表并对其排序。

```python
class StoneBird():
    def __dir__(self):
        return [1,2,3]

print(dir(StoneBird())) # [1,2,3]
```

## `__get__`(*self*, *instance*, *owner=None*) -- 获取实例属性值

```python
class MyDescriptor:
    def __get__(self, instance, owner):
        print("正在获取属性值")
        return instance._value  # 从实例中访问属性值

class MyClass:
    def __init__(self, value):
        self._value = value  # 将值存储为属性

    # 将描述器定义为类属性
    my_descriptor = MyDescriptor()

obj = MyClass("Hello")
print(obj.my_descriptor)  # 正在获取属性值
# 输出：Hello
```

## `__set__`(*self*, *instance*, *value*) -- 设置实例属性值

```bash
class MyDescriptor:
    def __set__(self, instance, value):
        print("正在设置属性值")
        if value < 0:
            raise ValueError("属性值不能为负数")
        instance._value = value  # 设置属性值

class MyClass:
    def __init__(self, value):
        self._value = value  # 将值存储为属性

    # 将描述器定义为类属性
    my_descriptor = MyDescriptor()

obj = MyClass(10)
obj.my_descriptor = 20  # 正在设置属性值
print(obj.my_descriptor)  # 20

obj.my_descriptor = -5  # 正在设置属性值
# 抛出 ValueError: 属性值不能为负数
```

## `__delete__`(*self*, *instance*) -- 删除实例属性值

```python
class MyDescriptor:
    def __delete__(self, instance):
        print("正在删除属性")
        raise AttributeError("属性不可删除")

class MyClass:
    def __init__(self, value):
        self._value = value  # 将值存储为属性

    # 将描述器定义为类属性
    my_descriptor = MyDescriptor()

obj = MyClass(10)
del obj.my_descriptor  # 正在删除属性
# 抛出 AttributeError: 属性不可删除
```

## :point_right:`__slots__`  -- 声明数据成员

`__slots__ `允许我们显式地声明数据成员（如特征属性）并禁止创建` __dict__ `和 `__weakref__` (除非是在 __slots__ 中显式地声明或是在父类中可用。)

通过在类中定义 `__slots__` 属性，可以指定类的实例只能拥有特定的属性，从而限制了实例的属性数量和类型，以提高性能和节省内存空间

```python
class MyClass:
    __slots__ = ['attr1', 'attr2']

    def __init__(self, attr1, attr2):
        self.attr1 = attr1
        self.attr2 = attr2

obj = MyClass(10, 20)
print(obj.attr1)  # 输出 10
print(obj.attr2)  # 输出 20

obj.attr3 = 30  # 引发 AttributeError: 'MyClass' object has no attribute 'attr3'
```

# 自定义类创建

## :point_right:`__init_subclass__`(*cls*) -- 子类初始化调用

用于定义一个类被子类继承时的行为,当所在类派生子类时此方法就会被调用。

```python
class BaseClass:
    def __init_subclass__(cls, **kwargs):
        # 检查子类的类名是否以 "Child" 开头
        if not cls.__name__.startswith("Child"):
            raise ValueError("子类的类名必须以 'Child' 开头")
        super().__init_subclass__(**kwargs)

class ChildClass(BaseClass):
    pass

class AnotherChildClass(BaseClass):
    pass
```

## :point_right:`__set_name__`(*self*, *owner*, *name*) -- 将类属性的名称绑定到类对象上。

```python
class MyDescriptor:
    def __set_name__(self, owner, name):
        print("类属性名：", name)
        print("类对象：", owner)

class MyClass:
    my_attr = MyDescriptor()
```

## :point_right:metaclass -- 元类

默认情况下，Python 使用 `type` 元类作为所有类的默认元类。

使用 `metaclass` 可以实现一些高级的功能，例如：

- 自动注册类到某个注册表
- 对类的属性和方法进行验证和自动转换
- 自动生成类的文档、日志或其他元信息
- 实现特定的编程模式或设计模式

```python
class MyMetaClass(type):
    def __new__(cls, name, bases, dct):
        # 在类创建时执行的定制化操作
        # cls：元类自身
        # name：类名
        # bases：父类元组
        # dct：类的属性字典
        print(f"创建类：{name}")
        return super().__new__(cls, name, bases, dct)

class MyClass(metaclass=MyMetaClass):
    pass

# 输出：
# 创建类：MyClass
# 当我们定义 MyClass 类时，Python 会调用 MyMetaClass 的 __new__ 方法来创建 MyClass 类，并输出 "创建类：MyClass"。
```

## :point_right:`__mro_entries__`(*self*, *bases*) -- 控制调用顺序

`__mro_entries__` 可以让开发者自定义 MRO 解析顺序，从而控制方法的调用顺序。

```python
class A:
    def foo(self):
        print("A's foo")

class B:
    def foo(self):
        print("B's foo")

class C(A, B):
    def foo(self):
        print("C's foo")

    @classmethod
    def __mro_entries__(cls):
        # 控制方法解析顺序
        return (B, A, cls)

c = C()
c.foo()  # 输出：B's foo

```

## :point_right:`__prepare__`(name, bases, **kwds) -- 属性和方法的定义顺序

类的属性和方法的定义顺序是重要的，因为它们在实例化和调用时的顺序会影响其行为。`__prepare__` 方法允许开发者自定义类创建时的命名空间字典，从而控制属性和方法的定义顺序。

```python
class OrderedMeta(type):
    def __prepare__(cls, name, bases):
        # 返回一个有序字典作为类的命名空间
        return collections.OrderedDict()

class MyClass(metaclass=OrderedMeta):
    def method3(self):
        pass

    def method1(self):
        pass

    def method2(self):
        pass

    attribute1 = 1
    attribute3 = 3
    attribute2 = 2

my_obj = MyClass()
print(dir(my_obj))
# 输出：
# ['attribute1', 'attribute3', 'attribute2', 'method1', 'method2', 'method3', ...]   
```

# 自定义实例及子类检查

## :point_right:`__instancecheck__`(*self*, *instance*) -- 当前类型检查行为

```python
class MyInt:
    def __init__(self, value):
        self.value = value

    def __instancecheck__(self, instance_type):
        # 自定义类型检查行为，只有当待检查类型为 int 类型时返回 True
        return instance_type is int

# 创建一个 MyInt 对象
my_int = MyInt(42)

# 使用 isinstance() 检查类型
print(isinstance(my_int, int))  # 输出：True
print(isinstance(my_int, str))  # 输出：False

```

## :point_right:`__subclasscheck__`(*self*, *subclass*) -- 子类检查行为

```python
class MyInt:
    pass

class MyFloat:
    pass

class MyNumber:
    def __subclasscheck__(self, subclass):
        # 自定义子类检查行为，只有当待检查类是 MyInt 或 MyFloat 类时返回 True
        return subclass in [MyInt, MyFloat]

# 检查类之间的继承关系
print(issubclass(MyInt, MyNumber))   # 输出：True
print(issubclass(MyFloat, MyNumber)) # 输出：True
print(issubclass(int, MyNumber))      # 输出：False
```

# 模拟泛型类型

## :point_right:`__class_getitem__`(*cls*, *key*) -- 创建泛型类时自定义类的行为

```python
class MyList:
    def __class_getitem__(cls, item):
        # 自定义泛型类行为，创建一个新的类并返回
        class GenericList:
            def __init__(self):
                self.items = []
            
            def append(self, value):
                self.items.append(value)
            
            def __str__(self):
                return str(self.items)
        
        return GenericList

# 创建泛型类实例
IntList = MyList[int]
str_list = IntList()
str_list.append(1)
str_list.append(2)
str_list.append(3)
print(str_list) # 输出：[1, 2, 3]
```

# 模拟可调用

## :point_right:`__call__`(*self*[, *args...*]) -- 将对象当作函数调用时行为

```python
class CallablePerson:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def __call__(self, *args, **kwargs):
        print(f"{self.name} is being called with args: {args}, kwargs: {kwargs}")

# 创建 CallablePerson 对象
person = CallablePerson("Alice", 30)

# 将对象当作函数调用
person("arg1", arg2="value2")
```

#  模拟容器类型

## :point_right:`__len__`(*self*) -- 获取对象长度

用于在对对象使用 `len()` 函数时自定义对象的行为。`len()` 函数用于获取对象的长度，通常用于字符串、列表、元组、字典等可序列化的对象。

```python
class MyList:
    def __init__(self):
        self.items = []
    
    def append(self, item):
        self.items.append(item)
    
    def __len__(self):
        return len(self.items)

# 创建 MyList 对象
my_list = MyList()

# 添加元素到列表中
my_list.append(1)
my_list.append(2)
my_list.append(3)

# 获取列表的长度
print(len(my_list))  # 输出: 3
```

## `__length_hint__`(*self*) -- 获取预估长度

获取对象长度的估计值时自定义对象的行为。`__length_hint__` 方法通常用于提供一个对象的近似长度，而不是精确的长度。

```python
class MyList:
    def __init__(self):
        self.items = []
    
    def append(self, item):
        self.items.append(item)
    
    def __length_hint__(self):
        return len(self.items) + 10

# 创建 MyList 对象
my_list = MyList()

# 添加元素到列表中
my_list.append(1)
my_list.append(2)
my_list.append(3)

# 获取列表的长度的估计值
print(len(my_list))  # 输出: 13
```

## :point_right:`__getitem__`(*self*, *key*) -- 通过key获取元素值

当使用方括号 `[]` 访问对象的元素时，Python 会调用对象的 `__getitem__` 方法来处理索引操作。

```python
class MyList:
    def __init__(self):
        self.items = []
    
    def append(self, item):
        self.items.append(item)
    
    def __getitem__(self, index):
        return self.items[index]

# 创建 MyList 对象
my_list = MyList()

# 添加元素到列表中
my_list.append(1)
my_list.append(2)
my_list.append(3)

# 访问列表的元素
print(my_list[0])  # 输出: 1
print(my_list[1])  # 输出: 2
print(my_list[2])  # 输出: 3
```

## :point_right:`__setitem__`(*self*, *key*, *value*) --  通过key设置元素值

```PYTHON
class MyList:
    def __init__(self):
        self.items = []
    
    def append(self, item):
        self.items.append(item)
    
    def __getitem__(self, index):
        return self.items[index]
    
    def __setitem__(self, index, value):
        self.items[index] = value

# 创建 MyList 对象
my_list = MyList()

# 添加元素到列表中
my_list.append(1)
my_list.append(2)
my_list.append(3)

# 访问列表的元素
print(my_list[0])  # 输出: 1

# 修改列表的元素
my_list[1] = 4

# 输出修改后的列表
print(my_list[1])  # 输出: 4
```

## :point_right:`__delitem__`(*self*, *key*) -- 删除元素

当使用 `del` 关键字删除对象的元素时，Python 会调用对象的 `__delitem__` 方法来处理删除操作。

```python
class MyList:
    def __init__(self):
        self.items = []
    
    def append(self, item):
        self.items.append(item)
    
    def __getitem__(self, index):
        return self.items[index]
    
    def __setitem__(self, index, value):
        self.items[index] = value
    
    def __delitem__(self, index):
        del self.items[index]

# 创建 MyList 对象
my_list = MyList()

# 添加元素到列表中
my_list.append(1)
my_list.append(2)
my_list.append(3)

# 输出列表的元素
print(my_list[1])  # 输出: 2

# 删除列表的元素
del my_list[1]

# 输出删除后的列表
print(my_list[1])  # 抛出 IndexError 异常
```

## :point_right:`__missing__`(*self*, *key*) -- key不存在时处理

```python
class MyDict(dict):
    def __missing__(self, key):
        # 在缺失的键上返回默认值
        return f'{key} does not exist'

# 创建 MyDict 对象
my_dict = MyDict()

# 添加键值对到字典中
my_dict['a'] = 1
my_dict['b'] = 2

# 访问存在的键
print(my_dict['a'])  # 输出: 1

# 访问不存在的键，调用 __missing__ 方法
print(my_dict['c'])  # 输出: c does not exist
```

## :point_right:`__iter__`(*self*) -- 返回一个迭代器对象

`__iter__` 方法应返回一个迭代器对象，该对象应实现了 `__next__` 方法，用于获取下一个迭代值。如果没有更多的值可供迭代，`__next__` 方法应抛出 `StopIteration` 异常。

```python
class MyIterable:
    def __init__(self, start, end):
        self.start = start
        self.end = end

    def __iter__(self):
        return self

    def __next__(self):
        if self.start > self.end:
            raise StopIteration
        else:
            self.start += 1
            return self.start - 1

# 创建 MyIterable 对象
my_iterable = MyIterable(1, 5)

# 使用 for 循环进行迭代
for num in my_iterable:
    print(num)
```

## :point_right:`__reversed__`(*self*) -- 反向迭代行为

用于定义一个对象的反向迭代行为。当一个对象使用 `reversed()` 函数进行反向迭代时，Python 会调用该对象的 `__reversed__` 方法来获取一个反向迭代器（reversed iterator）对象，然后通过调用反向迭代器对象的 `__next__` 方法来获取下一个值，直到反向迭代结束。

```python
class MyReversible:
    def __init__(self, start, end):
        self.start = start
        self.end = end

    def __iter__(self):
        return self

    def __next__(self):
        if self.start > self.end:
            raise StopIteration
        else:
            self.start += 1
            return self.start - 1

    def __reversed__(self):
        return MyReversible(self.end, self.start)

# 创建 MyReversible 对象
my_reversible = MyReversible(1, 5)

# 使用 reversed() 函数进行反向迭代
for num in reversed(my_reversible):
    print(num)
```

## :point_right:`__contains__`(*self*, *item*) -- 检查是否包含对象

当使用 `in` 运算符检查一个对象是否包含某个元素时，Python 会调用该对象的 `__contains__` 方法来判断是否包含该元素。

```python
class MyContainer:
    def __init__(self, items):
        self.items = items

    def __contains__(self, item):
        return item in self.items

# 创建 MyContainer 对象
my_container = MyContainer([1, 2, 3, 4, 5])

# 使用 in 运算符进行成员包含检查
print(3 in my_container)  # 输出 True
print(6 in my_container)  # 输出 False
```

#  with 语句上下文管理器

## :point_right:`__enter__`(*self*)

## :point_right:`__exit__`(*self*, *exc_type*, *exc_value*, *traceback*)

```python
class MyContext:
    def __enter__(self):
        print("Entering the context")
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Exiting the context")
        return False

    def do_something(self):
        print("Doing something in the context")


# 使用 with 语句创建上下文管理器对象
with MyContext() as my_context:
    my_context.do_something()

# 输出:
# Entering the context
# Doing something in the context
# Exiting the context
```

# 异步协程

## :point_right:`__await__`(*self*) -- 可等待对象

`__await__` 方法应返回一个迭代器对象，该迭代器对象必须实现以下两个方法：

- `__iter__()`: 返回迭代器对象自身。
- `__next__()`: 返回下一个可等待对象，或者引发 `StopAsyncIteration` 异常表示迭代

```python
async def new_sleep():
    await asyncio.sleep(2)

class Waiting:
    def __await__(self):
        return new_sleep().__await__()
```

## :point_right:`__aiter__`(*self*)

## :point_right:`__anext__`(*self*)

```python
import asyncio


class Asynchronous_Iterator:
    ''' Iterate over an asynchronous source. n Iterations.'''
    
    def __init__(self, n):
        self.current = 0
        self.n = n

    def __aiter__(self):
        return self

    async def __anext__(self):
        await asyncio.sleep(1)
        print(f"get next element {self.current}")
        self.current += 1
        if self.current > self.n:
            raise StopAsyncIteration
        return self.current - 1


async def main():
    async for i in Asynchronous_Iterator(3):
        print(f"next element {i}")


asyncio.run(main())
```

# 异步上下文

异步上下文管理器是一个对象，它实现了 `__aenter__` 和 `__aexit__` 方法，可以在异步上下文中使用 `async with` 语句进行管理。在进入异步上下文时，`__aenter__` 方法会被调用；在退出异步上下文时，`__aexit__` 方法会被调用。

## `__aenter__`(*self*)

## `__aexit__`(*self*, *exc_type*, *exc_value*, *traceback*)

```python
import asyncio
class AContext:
    def __init__(self):
        print("in init")

    async def __aenter__(self):
        print("in aenter")
    async def __aexit__(self, exc_type, exc_val, exc_tb):
        print("in aexit")

async def main():
    async with AContext() as ac:
        print("in with", ac)

if __name__ == '__main__':
    print("start")
    asyncio.run(main())
```

#  模拟数字类型

object.**__add__**(*self*, *other*)

object.**__sub__**(*self*, *other*)

object.**__mul__**(*self*, *other*)

object.**__matmul__**(*self*, *other*)

object.**__truediv__**(*self*, *other*)

object.**__floordiv__**(*self*, *other*)

object.**__mod__**(*self*, *other*)

object.**__divmod__**(*self*, *other*)

object.**__pow__**(*self*, *other*[, *modulo*])

object.**__lshift__**(*self*, *other*)

object.**__rshift__**(*self*, *other*)

object.**__and__**(*self*, *other*)

object.**__xor__**(*self*, *other*)

object.**__or__**(*self*, *other*)

object.**__radd__**(*self*, *other*)

object.**__rsub__**(*self*, *other*)

object.**__rmul__**(*self*, *other*)

object.**__rmatmul__**(*self*, *other*)

object.**__rtruediv__**(*self*, *other*)

object.**__rfloordiv__**(*self*, *other*)

object.**__rmod__**(*self*, *other*)

object.**__rdivmod__**(*self*, *other*)

object.**__rpow__**(*self*, *other*[, *modulo*])

object.**__rlshift__**(*self*, *other*)

object.**__rrshift__**(*self*, *other*)

object.**__rand__**(*self*, *other*)

object.**__rxor__**(*self*, *other*)

object.**__ror__**(*self*, *other*)

object.**__iadd__**(*self*, *other*)

object.**__isub__**(*self*, *other*)

object.**__imul__**(*self*, *other*)

object.**__imatmul__**(*self*, *other*)

object.**__itruediv__**(*self*, *other*)

object.**__ifloordiv__**(*self*, *other*)

object.**__imod__**(*self*, *other*)

object.**__ipow__**(*self*, *other*[, *modulo*])

object.**__ilshift__**(*self*, *other*)

object.**__irshift__**(*self*, *other*)

object.**__iand__**(*self*, *other*)

object.**__ixor__**(*self*, *other*)

object.**__ior__**(*self*, *other*)

object.**__neg__**(*self*)

object.**__pos__**(*self*)

object.**__abs__**(*self*)

object.**__invert__**(*self*)

object.**__complex__**(*self*)

object.**__int__**(*self*)

object.**__float__**(*self*)

object.**__index__**(*self*)

object.**__round__**(*self*[, *ndigits*])

object.**__trunc__**(*self*)

object.**__floor__**(*self*)

object.**__ceil__**(*self*)
