<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [前言](#%E5%89%8D%E8%A8%80)
- [pip换源安装](#pip%E6%8D%A2%E6%BA%90%E5%AE%89%E8%A3%85)
- [HelloWorld](#helloworld)
- [小刀弑牛](#%E5%B0%8F%E5%88%80%E5%BC%91%E7%89%9B)
- [小记一下](#%E5%B0%8F%E8%AE%B0%E4%B8%80%E4%B8%8B)
- [match语句](#match%E8%AF%AD%E5%8F%A5)
- [函数参数](#%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0)
- [Lambda 表达式](#lambda-%E8%A1%A8%E8%BE%BE%E5%BC%8F)
- [python的else语句](#python%E7%9A%84else%E8%AF%AD%E5%8F%A5)
- [自定义异常](#%E8%87%AA%E5%AE%9A%E4%B9%89%E5%BC%82%E5%B8%B8)
- [Python 作用域和命名空间](#python-%E4%BD%9C%E7%94%A8%E5%9F%9F%E5%92%8C%E5%91%BD%E5%90%8D%E7%A9%BA%E9%97%B4)
- [多重继承](#%E5%A4%9A%E9%87%8D%E7%BB%A7%E6%89%BF)
- [弱引用](#%E5%BC%B1%E5%BC%95%E7%94%A8)
- [虚拟环境和包](#%E8%99%9A%E6%8B%9F%E7%8E%AF%E5%A2%83%E5%92%8C%E5%8C%85)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 前言
每个人都是python大师

🙊如果能成为python的cookbook就好了🙈

整理知识，传播智慧，好好学习，天天向上。

# pip换源安装

```bash
pip install scrapy -i http://mirrors.aliyun.com/pypi/simple/  --trusted-host mirrors.aliyun.com

# 永久修改: linux修改~/.pip/pip.conf, windows修改C:\Users\xx\pip\pip.ini
```

阿里云 http://mirrors.aliyun.com/pypi/simple/
中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple/
豆瓣(douban) http://pypi.douban.com/simple/
清华大学 https://pypi.tuna.tsinghua.edu.cn/simple/

# HelloWorld

```python
def hello_world():
    print("hello, world")
    print("你好, 世界")

if __name__ == '__main__':
    hello_world()
```

完成并运行上面代码，你现在已经是一个python程序员 了

🍻扬帆起航

# 小刀弑牛

[官方入门地址](https://docs.python.org/zh-cn/3/tutorial/index.html)

> 入门重要途径，切勿心急，建议手敲一遍
>
> 如果你是没有其他语言基础的初学者，建议学习2-3遍。

# 小记一下

换行，代码太长可以用 \ 换行 ,Python 会忽略代码里 []、{} 和 () 中的换行

```python
s = "stone" + \
"bird"
```

特殊前缀类型

```bash
r'str'   -> 代表普通字符
b'str'  -> byte类型
u'str'  -> unicode 编码
f'Results of the {year} {event}' -> 格式化输出
```

*代表是元组tuple、**代表字典dict 

```bash
`*args`,`**kwargs`
```

python默认utf-8文件编码格式，如果不使用默认编码，则要声明文件的编码，文件的 *第一* 行要写成特殊注释。句法如下：

```bash
# -*- coding: cp1252 -*-
# -*- coding: UTF-8 -*- 
# coding=utf-8   注意：=号两边不要空格。
```

原始字符串，不希望前置 `\` 的字符转义成特殊字符，可以使用 *原始字符串*，在引号前添加 `r` 即可

```python
print('C:\some\name')
print(r'C:\some\name') 

# 或者使用三引号""""""
s = """stone
bird
"""
```

负数索引,索引还支持负数，用负数索引时，从右边开始计数

```python
word = 'Python'
print(word[0])
print(word[-1])
```

切片 ，可以有步长

```bash
s[start:end:step]
```

python路径

```python
print(sys.path) #查看python路径
import os
import sys
#获得.py文件所在的绝对路径，包括文件名
py_path = os.path.abspath(__file__)  
#获得.py所在的文件夹的绝对路径
py_file_path = os.path.dirname(os.path.abs(__file__)) 
#获得py_file_path的上一级文件夹的绝对路径
py_pre_file_path = os.path.dirname(os.path.dirname(os.path.abs(__file__))) 
#将路径动态的添加到环境变量中
sys.path.append(py_pre_file_path)
```

# match语句

python3.10以上，类似于golang的switch

```python
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case 418:
            return "I'm a teapot"
        case 401 | 403 | 404:
    		return "Not allowed"
        case _:
            return "Something's wrong with the internet"
```

注意最后一个代码块：“变量名” `_` 被作为 *通配符* 并必定会匹配成功。 如果没有 case 语句匹配成功，则不会执行任何分支。

模式的形式类似解包赋值，并可被用于绑定变量：

```python
# point is an (x, y) tuple
match point:
    case (0, 0):
        print("Origin")
    case (0, y):
        print(f"Y={y}")
    case (x, 0):
        print(f"X={x}")
    case (x, y):
        print(f"X={x}, Y={y}")
    case _:
        raise ValueError("Not a point")
```

枚举

```python
from enum import Enum
class Color(Enum):
    RED = 'red'
    GREEN = 'green'
    BLUE = 'blue'

color = Color(input("Enter your choice of 'red', 'blue' or 'green': "))

match color:
    case Color.RED:
        print("I see red!")
    case Color.GREEN:
        print("Grass is green")
    case Color.BLUE:
        print("I'm feeling the blues :(")
```

# 函数参数

默认值参数

```python
def get_name(name:str):
    pass
```

关键词参数：`kwarg=value` 形式的关键字参数也可以用于调用函数。函数示例如下

```python
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    pass
```

特殊参数：函数定义中未使用 `/` 和 `*` 时，参数可以按位置或关键字传递给函数。

```python
def combined_example(pos_only, /, standard, *, kwd_only):
    print(pos_only, standard, kwd_only)
```

#  Lambda 表达式

lambda 关键字用于创建小巧的匿名函数。`lambda a, b: a+b` 函数返回两个参数的和。Lambda 函数可用于任何需要函数对象的地方。在语法上，匿名函数只能是单个表达式。在语义上，它只是常规函数定义的语法糖。与嵌套函数定义一样，lambda 函数可以引用包含作用域中的变量：

```python
def make_incrementor(n):
    return lambda x: x + n

f = make_incrementor(42)
f(0) #42
f(1) #43
```

还可以把匿名函数用作传递的实参

```python
pairs = [(1, 'one'), (2, 'two'), (3, 'three'), (4, 'four')]
pairs.sort(key=lambda pair: pair[1])
# [(4, 'four'), (1, 'one'), (3, 'three'), (2, 'two')]
```

# python的else语句

for…else、while…else、

```python
for n in range(10):
    if n == 5 :
        break
        print(n)
else:
    print("11")

# for和whlie执行了break 就不会执行else
```

try..except…else等语法

```python
try:
    a = 10
    raise Exception("hjah")
except Exception as e:
    print(e)
else:
    print("nothing")

# try里面的else有异常情况下不会执行。
```

**总的来说，for、while、try语句中 的else， 在正常结束时才执行**，而在if..else语句中是if语句判断为假（有毛病）才执行else，这一点要区分开来

# 自定义异常

创建新的异常很简单——定义新的类，让它继承自 `Exception` 

```python
class CustomError(Exception):
    def __init__(self,ErrorInfo):
        super().__init__(self) #初始化父类
        self.errorinfo=ErrorInfo
    def __str__(self):
        return self.errorinfo
    
if __name__ == '__main__':
    try:
        raise CustomError('客户异常')
    except CustomError as e:
        print(e)
```

# Python 作用域和命名空间

**作用域** 是命名空间可直接访问的 Python 程序的文本区域。 “可直接访问” 的意思是，对名称的非限定引用会在命名空间中查找名称。

作用域虽然是静态确定的，但会被动态使用。执行期间的任何时刻，都会有 3 或 4 个命名空间可被直接访问的嵌套作用域：

- 最内层作用域，包含局部名称，并首先在其中进行搜索
- the scopes of any enclosing functions, which are searched starting with the nearest enclosing scope, contain non-local, but also non-global names
- 倒数第二个作用域，包含当前模块的全局名称
- 最外层的作用域，包含内置名称的命名空间，最后搜索

以及 [`global`](https://docs.python.org/zh-cn/3/reference/simple_stmts.html#global) 和 [`nonlocal`](https://docs.python.org/zh-cn/3/reference/simple_stmts.html#nonlocal) 对变量绑定的影响

```python
def scope_test():
    def do_local():
        spam = "local spam"

    def do_nonlocal():
        nonlocal spam
        spam = "nonlocal spam"

    def do_global():
        global spam
        spam = "global spam"

    spam = "test spam"
    do_local()
    print("After local assignment:", spam)
    do_nonlocal()
    print("After nonlocal assignment:", spam)
    do_global()
    print("After global assignment:", spam)

scope_test()
print("In global scope:", spam)
```

# 多重继承

多重继承  若是父类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法。

```python
class sample(speaker,student):
    a =''
    def __init__(self,n,a,w,g,t):
        student.__init__(self,n,a,w,g)
        speaker.__init__(self,n,t)
 
test = sample("Tim",25,80,4,"Python")
test.speak()   #方法名同，默认调用的是在括号中排前地父类的方法
test.__mro__ #类都有一个名为 __mro__ 的属性，它的值是一个元组，按照方法解析顺序列出各个超类，从当前类一直向上，直到object 类。
```

# 弱引用

Python 会自动进行内存管理（对大多数对象进行引用计数并使用 garbage collection 来清除循环引用）。 当某个对象的最后一个引用被移除后不久就会释放其所占用的内存。

此方式对大多数应用来说都适用，但偶尔也必须在对象持续被其他对象所使用时跟踪它们。 不幸的是，跟踪它们将创建一个会令其永久化的引用。 [`weakref`](https://docs.python.org/zh-cn/3/library/weakref.html#module-weakref) 模块提供的工具可以不必创建引用就能跟踪对象。 当对象不再需要时，它将自动从一个弱引用表中被移除，并为弱引用对象触发一个回调。 典型应用包括对创建开销较大的对象进行缓存:

```python
import weakref, gc
class A:
    def __init__(self, value):
        self.value = value
    def __repr__(self):
        return str(self.value)

a = A(10)                   # create a reference
d = weakref.WeakValueDictionary()
d['primary'] = a            # does not create a reference
d['primary']    # 10            # fetch the object if it is still alive  
del a                       # remove the one reference
gc.collect()  # 0              # run garbage collection right away
d['primary']                # entry was automatically removed
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    d['primary']                # entry was automatically removed
  File "C:/python311/lib/weakref.py", line 46, in __getitem__
    o = self.data[key]()
KeyError: 'primary'
```

# 虚拟环境和包

创建虚拟环境

```python
python3 -m venv tutorial-env
```

这将创建 `tutorial-env` 目录，如果它不存在的话，并在其中创建包含 Python 解释器副本和各种支持文件的目录。

虚拟环境的常用目录位置是 `.venv`。 这个名称通常会令该目录在你的终端中保持隐藏，从而避免需要对所在目录进行额外解释的一般名称。 它还能防止与某些工具所支持的 `.env` 环境变量定义文件发生冲突。

在Windows上，运行:

```
tutorial-env\Scripts\activate.bat
```

在Unix或MacOS上，运行:

```
source tutorial-env/bin/activate
```
