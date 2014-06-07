easytrace
=========

Java 命令行诊断工具

目前该工具代码暂不开源，原因如下：  
1、由于处于初期的开发和小面积试用阶级，代码还需整理。  
2、对于代码的结构还需进一步调整，以达到方便的扩展性。  

当完成以上工作后，会把所有代码进行开源。

# 简介
easytrace 是一款Java的运行时诊断工具（采用动态字节码注入技术），可以在不停止程序的情况下查看Java程序运行时状况，而且对目标进程基本无副作用。**easytrace 着重解决的是需使用编码的方式获取才能解决的问题，或者疑难问题。**


# 功能
* 动态方法跟踪功能，可针对调用方法，查看当时的返回对象、this对象、传入参数的值、当时刻某类static属性值。支持同时监控多个方法，并可对监控内容可以进行过滤。
* 强大的取值表达式，用法类似用EL表达式取值。让你轻松监控到你所需要的值。
* static 属性查看功能，可单独查看当前时刻某类中static 属性值。
* 查看当前JVM的状况，每个线程cpu占用情况、gc的次数和时间，JVM的内存状况等等。
* 查看某个线程的当前的调用堆栈。
* 查看类的所有属性功能，这个功能主要为是配合使用动态跟踪方法时，能更方便的查看某类的属性值。
* 查看具体类的类装载器层次和来源路径功能，这个在多类加载器的程序比较有用。比如ClassCastException异常和ClassNotFoundException异常时有用。
* Class 字节码导出功能，这个功能可能比较少用，主要用在运行期修改字节码的时候，想知道修改的内容时，可用该功能导出当时运行时的Class字节码。


# 支持
* JDK1.6+ （1.7、1.8版本未测试）
* 本地诊断，不支持远程方式

# 特点
* 命令行诊断（非Btrace的脚本方式）
* 强大的取值功能，让你轻松的获取你想获取的值
* 诊断后对程序无残留代码段（Btrace 脚本执行后有残留代码）
* 安全性和易用性高（对于异常的情况，大多数都会使注入程序端的easytrace代码中断和恢复原有更改，从而保证目标程序的安全和无残留）
* 文件小、无依赖jar（所有需要的jar包都已经打进jar中，或者自己实现）

# 安装
无需安装，直接下载后，运行即可。

·····

详细的指南可查看：https://github.com/zhxing/easytrace/wiki/%E7%94%A8%E6%88%B7%E6%8C%87%E5%8D%97
诊断示例可查看：https://github.com/zhxing/easytrace/wiki/%E8%AF%8A%E6%96%AD%E7%A4%BA%E4%BE%8B
高级用法可查看：https://github.com/zhxing/easytrace/wiki/%E9%AB%98%E7%BA%A7%E7%94%A8%E6%B3%95

# 版本
**v0.1**
* 第一个版本

**v0.2**
* 新增了trace的多个方法监控，并优化了内容显示（同一线程内，多方法监控显示在同个内容中）；新增了trace命令的文字过滤功能

**v0.3**
* 新增trace 命令的父类、<init>构造方法的匹配
* 新增trace 命令监控多个方法，如果在同个线程内且为调用关系，则会在同时显示该调用关系
* 新增trace 命令监控方法，包名、类名、方法名的后缀*匹配
* 新增top命令
* 新增thread 命令
* bugfix/重写了trace命令部分逻辑，优化了性能

# 参考项目 
* [Btrace](https://kenai.com/projects/btrace)：参考了其客户端服务器端交互逻辑（第一设想是对Btrace进行改造成命令行版本，但发现其改造比较麻烦。）
* [HouseMD](https://github.com/zhongl/HouseMD)：参考了其众多有用的功能，并对其自定义改造（本身想对其进行改造，但1、不熟scala，不能对HouseMD进行定制  2、定制需求较多和原本设想不相符 ，所以只是参考其功能实现）
* [jvmtop](http://code.google.com/p/jvmtop/)：参考了其功能
