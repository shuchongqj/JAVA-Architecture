
#  JVM 概述
   JVM 全称是Java Virtual Machine，Java 虚拟机，也就是在计算机上再虚拟一个计算机，这和我们使用 VMWare 不一样，那个虚拟的东西你是可以看到的，
这个JVM 你是看不到的，它存在内存中。我们知道计算机的基本构成是：运算器、控制器、存储器、输入和输出设备，那这个JVM 也是有这成套的元素，运算器是
当然是交给硬件CPU 还处理了，只是为了适应“一次编译，随处运行”的情况，需要做一个翻译动作，于是就用了JVM 自己的命令集，这与汇编的命令集有点类似，
每一种汇编命令集针对一个系列的CPU，比如8086 系列的汇编也是可以用在8088 上的，但是就不能跑在8051 上，而JVM 的命令集则是可以到处运行的，因为JVM 
做了翻译，根据不同的CPU，翻译成不同的机器语言。JVM 中我们最需要深入理解的就是它的存储部分，存储？硬盘？NO，NO， JVM 是一个内存中的虚拟机，那它
的存储就是内存了，我们写的所有类、常量、变量、方法都在内存中，这决定着我们程序运行的是否健壮、是否高效，接下来的部分就是重点介绍之

# JVM 的组成部分

## 从平面的角度看虚拟机结构

<p align="center">
  <img src="https://farm5.staticflickr.com/4858/45592512544_f127a15c9d_o.png">
  <br/>
</p>

## 从立体的角度看虚拟机结构

<p align="center">
  <img src="https://farm5.staticflickr.com/4838/32434212018_340a49ffab_o.jpg">
  <br/>
</p>

## 虚拟机的启动

<p align="center">
  <img src="https://farm5.staticflickr.com/4816/46266423832_16f0c92df3_o.png">
  <br/>
</p>

## 整个JVM 分为四部分:

### 1. Class Loader 类加载器
       
       根据给定的全限定名类名(如java.lang.Object)来装载class 文件的内容到Runtime data area 中的methodarea(方法区域)。Javsa 程序员可以extends
       java.lang.ClassLoader 类来写自己的Class loader, Class Loader 只管加载，只要符合文件结构就加载，至于说能不能运行，则不是它负责的，那是
       由Execution Engine 负责的。

### 2. Runtime data area 运行数据区
   
### 3. Execution Engine 执行引擎

       执行引擎也叫做解释器(Interpreter)，负责解释命令，提交操作系统执行, 执行classes 中的指令。任何JVM specification 实现(JDK)的核心
       是Execution engine， 换句话说：Sun 的JDK和IBM 的JDK 好坏主要取决于他们各自实现的Execution engine 的好坏。每个运行中的线程都有一
       个Execution engine 的实例
       
### 4. Native Interface 本地接口
       与native libraries 交互，是其它编程语言交互的接口。
 
**整个JVM 框架由加载器加载文件，然后执行器在内存中处理数据，需要与异构系统交互是可以通过本地接口进行，瞧，一个完整的系统诞生了**
 
 
