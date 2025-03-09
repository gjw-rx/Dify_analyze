今天我们要学习的源码部分为：

Dify/api/models 下的account.py文件

本文件包含了多个数据类的定义信息

accounts表结构

tenants表结构

tenant_account_joins表结构

account_integrates表结构

invitation_codes表结构

具体代码细节可自行官网拉取，官网Github地址已在上一篇文章提供

Account类：

继承UserMixin、Base类

Base（也是dify官方定义的一个基类 会在后面的文章中分析）

通过sqlalchemy.orm 连接数据库

并且Account类中定义了几个方法

is_password_set 检查密码设置

current_tenant 获取当前租户对象 基础方法本篇不做过多介绍。。。

Tenant类



对于account类，作者着重想讲解一下修饰类方法或属性的装饰器

1、 @property 类似java的getter方法 只读

2、current_tenant_id.setter 提供setter方法 可以控制如何设置属性的值

3、@staticmethod 静态方法

4、@classmethod 定义一个类方法 接受的对象是cls 类本身 而不是self 类的实例





根据分析，可以学到在成熟项目定义类变量的时候，都是采取什么样的方式来定义，包括引入ORM框架、使用装饰器。在日常开发中也可以学习这种思想





我是Harry，一个刚毕业的小白，对于代码有着十足的热爱，热衷于把自己学习的知识和内容分享出来