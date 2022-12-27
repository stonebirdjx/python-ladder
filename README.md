<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [前言](#%E5%89%8D%E8%A8%80)
- [pip换源安装](#pip%E6%8D%A2%E6%BA%90%E5%AE%89%E8%A3%85)
- [HelloWorld](#helloworld)
- [小刀弑牛](#%E5%B0%8F%E5%88%80%E5%BC%91%E7%89%9B)
- [python文件编码](#python%E6%96%87%E4%BB%B6%E7%BC%96%E7%A0%81)

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

# python文件编码

python默认utf-8文件编码格式，如果不使用默认编码，则要声明文件的编码，文件的 *第一* 行要写成特殊注释。句法如下：

```bash
# -*- coding: cp1252 -*-
# -*- coding: UTF-8 -*- 
# coding=utf-8   注意：=号两边不要空格。
```

