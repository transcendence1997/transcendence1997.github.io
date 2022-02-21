# Java基础

### JRE和JDK

JRE = Java Runtime Environment，是Java程序的运行时环境，包含JVM和运行时所需要的核心类库。

JVM保证了Java的跨平台性。

我们想要**运行**一个已有的Java程序，那么只需安装JRE即可。

JDK是Java程序开发工具包，包含JRE和开发人员使用的工具。

开发工具：编译工具（javac.exe）、运行工具（java.exe）

我们想要**开发**一个全新的Java程序，必须安装JDK。

### 语法

- switch语句：要加break，表达式可以是byte，short，int，char，枚举，String。
- 成员变量在堆内存（对象在堆内存中）中，有默认的初始化值；局部变量在栈内存中，没有默认的初始化值，必须先定义、赋值，才能使用。
- 面向对象的三大特征：封装、继承、多态。
- 如果定义了构造方法，系统将不再提供无参构造方法。
- String的构造方法：`String()`（创建空白字符串）, `String(char[] chs)`, `String(byte[] bys)`