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
- 以双引号给出的字符串，无论在代码中出现几次，JVM都只会建立一个String对象，并在字符串池中维护
- `boolean endsWith(String suffix)`判断字符串是否以某个后缀结尾
- `StringBuilider`是一个可变字符串类，构造方法可以是无参，也可以带一个`String`参数，用`append(任意类型)`添加数据，用`reverse()`反转，用`length()`返回长度，用`toString()`转换为String，String用构造函数转换成StringBuilder
- `List`的`set(int index, E element)`可修改元素，返回被修改的元素（修改前），`remove(Object o)`若不存在会返回false，`remove(int index)`不越界会返回删除的元素，越界会发生异常
- 继承：体现“is a”的关系，使子类拥有父类的属性和方法，还可在子类中重新定义、追加属性和方法，关键字为`extends`，父类的私有成员子类不能继承
- 子类方法中访问变量的查找顺序：子类局部范围找，子类成员范围找，父类成员范围找，如果都没有就报错（不考虑父亲的父亲）
- `super`用法与`this`相似：`this`代表本类对象的引用，`super`为父类对象引用；这两个关键字可以访问成员变量，构造方法，成员方法，父类和子类的同名成员变量可以用`super`和`this`区分
- 每一个子类构造方法的第一条默认语句都是`super()`，如果父类没有无参构造方法，会报错，这时候应该显式调用父类带参构造方法
- 通过子类对象访问一个方法：子类成员范围找，父类成员范围找，如果都没有就报错（不考虑父亲的父亲）
- 子类可以重写父类的方法，如有需要可用`super`显式调用父类方法；`@Override`注解可检查重写方法的方法声明的正确性；私有方法不能被重写，重写的子类方法应该至少比父类方法更接近public
- 子类不能继承多个父类，但可以多层继承
- 包其实就是文件夹，对类进行分类管理，定义格式`package 包名;`
- 带包的Java类编译和执行：方式一，`javac Helloworld.java`，然后手动建包（建文件夹），把`HelloWorld.class`放到文件夹下，最后`java com.xxx.HelloWorld`；方式二，`javac -d . HelloWorld.java`自动建包（建文件夹），然后`java com.xxx.HelloWorld`
- 使用不同包下的类时，使用的时候要写类的全路径，可以用`import 包名.类名;`简化