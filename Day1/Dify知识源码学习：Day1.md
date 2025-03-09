## Dify知识源码学习：1

本系列旨在学习目前主流的AI Workflow工具 Dify的python源码

项目地址：[langgenius/dify.](https://github.com/langgenius/dify)



![structure](img\structure.png)

在wrapper.py这个python文件中定义了RecyclableContextVar这个类

![recyableContextVar](img\recyableContextVar.png)

其中该类是对python内置的contextVar的一个封装，目的是在使用Gunicorn时，用于解决上下文变量数据丢失的问题

其中，作者定义了

```python
_thread_recycles
```

用于跟踪回收次数



一共提供了三个类方法：

```
increment_thread_recycles
增加线程回收计数器。如果当前线程是第一次被回收，则初始化为0；否则递增计数器。
```

```
get
获取上下文变量的值。检查线程是否已被回收，并根据情况返回实际值或默认值。
```

```python
set
设置上下文变量的值。确保在设置新值之前，更新计数器与线程回收计数器同步。
```

详情代码请自己前往官方地址拉取官方代码进行查看



理解：个人认为是通过引入线程回收计数器和更新计数器，再每次回收线程的时候，能够确保上下文变量是被正确的引用的。通过比较回收计数器和更新计数器的值相差情况来判断是更新还是回出现的问题。

当我们遇到类似的问题，也可以才看Dify官方的解法









以上内容只限于个人理解，由于个人水平的问题，写出来的内容可能存在诸多问题，虚心向各位大佬讨教

我是Harry，一个刚毕业的小白，对于代码有着十足的热爱，热衷于把自己学习的知识和内容分享出来