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

- 权限修饰符

  | 修饰符    | 同一个类中 | 同一个包中子类无关类 | 不同包的子类 | 不同包的无关类 |
  | --------- | ---------- | -------------------- | ------------ | -------------- |
  | private   | Y          |                      |              |                |
  | 默认      | Y          | Y                    |              |                |
  | protected | Y          | Y                    | Y            |                |
  | public    | Y          | Y                    | Y            | Y              |

- 状态修饰符final修饰的成员方法不可被重写，但子类可以用；final修饰的变量（成员变量或局部变量）是常量，不能再次被赋值；final修饰的类不能被继承；final修饰引用类型的变量只是地址不能变，里面的内容可以变

- 可以通过对象名访问static成员，但建议用类名访问；非静态成员方法可以访问静态或非静态的成员，静态的成员方法只能访问静态成员

- 多态：同一个对象，在不同时刻表现出来的不同形态；多态的前提和体现：有继承、实现关系，有方法重写，有父类引用指向子类对象

- 多态中成员访问特点：成员变量：编译看左边，执行看左边；成员方法：编译看左边，执行看右边；因为成员方法有重写，而成员变量没有

- 一个没有方法体的方法应该定义为抽象方法，一个有抽象方法的类应该定义为抽象类，抽象类里面也可以有非抽象方法，也可以没有抽象方法，抽象类中可以有成员变量（可以是变量，也可以是常量），抽象类可以有构造方法（但不能实例化，只是用于子类访问父类数据的初始化）

- 实现接口用关键字`implements`，接口中的成员变量默认为`public static final`，接口中没有构造方法，接口中的成员方法只能是抽象的，且默认为`public abstract`

- 一个类可以同时继承别的类和实现接口，一个类如果没有父类，那么它默认继承了`Object`类，一个类可以同时实现多个接口，接口可以继承（extends）接口，且可以继承多个接口

- 内部类可以直接访问外部类的成员，包括私有；外部类要访问内部类的成员必须创建对象；内部类可以是成员内部类，也可以是局部内部类；

- 外界创建成员内部类的对象：`Outer.Inner oi = new Outer().new Inner();`；但是内部类一般定义为`private`，不希望外界直接访问内部类

- 外界无法直接访问局部内部类，局部内部类也可以访问方法内的局部变量

- 匿名内部类的前提：存在一个类（具体类抽象类都可以）或者接口；格式：`new 类名或者接口名() {重写方法};`，本质是一个继承了该类或实现了该接口的子类的匿名对象

- `System.exit(int status)`终止当前运行的JVM，非零表示异常终止

- `System.currentTimeMillis()`返回当前时间（以毫秒为单位），可用来记录运行时间

- `Arrays.sort(数组)`用于排序，`Arrays.toString(数组)`转字符串

- 工具类的设计思想：构造方法用private修饰，成员用public static修饰

- 推荐使用`Integer.valueOf(int i)`和`Integer.valueOf(String s)`返回一个`Integer`对象

- `String.valueOf(int i)`可将int转为String

- `i.intValue()`可将Integer转为int

- 可以建立一个`SimpleDateFormat`对象（指定pattern），用`format(Date date)`和`parse(String source)`来格式化或解析Date

- `Calendar.getInstance()`返回一个Calendar对象，Calendar对象可用`get(Calendar.YEAR)`获取指定日历字段的值，用`add(int field, int amount)`将指定的时间量添加或减去给定的日历字段，用`set(int year, int month, int date)`设置当前日历的年月日

- `Throwable`是`Error`和`Exception`的父类，`Error`是严重问题，不需要处理；`Exception`表示程序本身可以处理的问题；`Exception`分为`RuntimeException`和非`RuntimeException`，`RuntimeException`在编译期是不检查的，出现问题后，需要我们会来修改代码；非`RuntimeException`编译期就必须处理，否则程序不能通过编译

- 如果程序出现了问题，我们没有做任何的处理，最终JVM会做默认的处理：把异常的名称，异常原因及异常出现的位置等信息输出在了控制台，程序停止执行

- try catch可以到catch中寻找匹配的异常类，找到后进行异常的处理，执行完毕后，程序还可以继续往下执行

- 运行时异常（非受检异常）：RuntimeException类及其子类，无需显式处理，也可以和编译时异常一样处理；编译时异常（受检异常）：其他的异常，必须显式处理，否则无法通过编译

- 并不是所有的情况我们都有权限进行异常处理，这是可以在方法的括号后面添加`throws 异常类名`抛出异常，在调用者中进行处理

- `throw new Exception();`用来在方法体内抛出异常

- List接口和Set接口继承自Collection接口，Collection的常用方法包括add，remove，contains，isEmpty（前面这些都返回boolean），clear（返回void），size，可通过iterator()遍历Collection

- List的特有方法包括`void add(int index, E element)`, `E remove(int index)`, `E set(int index, E element)`, `E get(int index)`

- iterator的next方法会先检查实际修改次数（ArrayList的成员变量）与预期修改次数（初始化iterator时的实际修改次数）是否相等，如果不相等，就抛出ConcurrentModificationException

- List有一个`listIterator()`允许沿任一方向遍历列表，在迭代期间修改列表，并获取列表中迭代器的当前位置，特有方法包括previous, hasPrevious, add（这个方法会把实际修改值赋值给与其修改值）

- Collection继承了Iterable，实现Iterable允许对象成为增强型for语句的目标，Iterable里面有个方法`iterator()`，增强for内部原理是一个Iterator迭代器，也就是说会有ConcurrentModificationException

- LinkedList有一些特有功能：addFrist, addLast, getFirst, getLast, removeFirst, removeLast

- Set不包含重复元素（遇到重复的元素不会加进去），没有带索引的方法，不能使用普通for循环遍历，可以用增强for循环遍历，对顺序不做保证

- 哈希值是JDK根据对象的地址或者字符串或者数字算出来的int类型的数值，Object类中的`hashCode()`方法可以获取对象的哈希值，默认情况下，不同对象的哈希值是不相同的，String重写了`hashCode()`，不同String可能会有相同哈希值

- LinkedHashSet由哈希表（保证元素不重复）和链表（保证元素有序，及元素的存储和取出顺序一致）实现，具有可预测的迭代次序

- TreeSet元素有序，这里的顺序不是只存储和取出的顺序，而是按照一定的规则进行排序，具体排序方式取决于构造方法，`TreeSet()`根据元素自然顺序（让元素所属的类实现Comparable接口）进行排序，`TreeSet(Comparator comparator)`根据指定的比较器（元素不需要实现Comparable）进行排序，没有带索引的方法，不能使用普通for循环遍历，只能用增强for和iterator遍历

- `Comparable`的使用：`public class Student implements Comparable<Student>`，重写`compareTo`，如果`compareTo`返回0会被TreeSet认为是重复元素

- 用匿名内部类写Comparator: `new Comparator<Student>() {...}`，里面重写`public int compare(Student s1, Student s2)`

- Collection不指定泛型默认类型为Object

- 泛型类`public class Generic<T> {...}`

- 泛型方法（假设类没有定义为泛型类）`public <T> void show(T t) {...}`，调用的时候直接`g.show(123);`类型会自动识别

- 泛型接口`public interface Generic<T>`，其实现类`public class GenericImpl<T> implements Generic<T>`