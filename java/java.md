# Java

- JRE = Java Runtime Environment，是Java程序的运行时环境，包含JVM和运行时所需要的核心类库。JVM保证了Java的跨平台性。我们想要**运行**一个已有的Java程序，那么只需安装JRE即可。JDK是Java程序开发工具包，包含JRE和开发人员使用的工具。开发工具：编译工具（javac.exe）、运行工具（java.exe）；我们想要**开发**一个全新的Java程序，必须安装JDK。

- switch语句：要加break，表达式可以是byte，short，int，char，枚举，String。

- 成员变量在堆内存（对象在堆内存中）中，有默认的初始化值；局部变量在栈内存中，没有默认的初始化值，必须先定义、赋值，才能使用。

- 面向对象的三大特征：封装、继承、多态。

- 如果定义了构造方法，系统将不再提供无参构造方法。

- String的构造方法：`String()`（创建空白字符串）, `String(char[] chs)`, `String(byte[] bys)`，`String(byte[] b, int offset, int length)`

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

- 类型通配符：`List<?>` 表示元素类型未知的List，他的元素可以匹配任何的类型，例如`List<?> list = new ArrayList<Integer>;`, `List<?> list = new ArrayList<Number>;`；`List<? extends Number>`表示的类型是Number或其子类型；`List<? super Number>`表示的类型是Number或者其父类型

- 可变参数：

  ```java
  public static int sum(int... a) { //a其实是一个数组；如果一个方法有多个参数，包含可变参数，可变参数要放在最后
      int s = 0;
      for (int i : a) {
          s += i;
      }
      return s;
  }
  ```

- `Arrays.asList("hello", "world")`返回一个大小不可变（可以修改元素，不能添加或删除）的List；`List.of("hello", "world")`返回一个不能增删改的List；`Set.of("hello", "world")`返回一个不能增删的Set

- Map的基本功能：`remove(Object key)`, `clear()`, `containsKey(Object key)`, `containsValue(Object value)`, `isEmpty()`, `size()`, `keySet()`返回Set（可用于遍历）, `values()`返回Collection, `entrySet()`返回Set<Map.Entry<K,V>>（可用于遍历），Map.Entry有`getKey()`和`getValue()`方法

- Collections的常用方法`Collections.sort(List<T> list)`（可以有第二个参数Comparator）, `Collections.reverse(List<?> list)`, `Collections.shuffle(List<?> list)`，返回类型都是void

- File是文件和目录路径名的抽象表示，构造方法：`File(String pathname)`, `File(String parent, String child)`, `File(File parent, String child)`

- File创建功能：`createNewFile()`文件不存在时，创建新空文件（如果存在一个同名的文件夹，也会创建文件失败），如果上级目录不存在，会报异常；`mkdir()`创建目录；`mkdirs()`创建目录，包括任何必须但不存在的父目录，这三个方法都返回boolean

- File判断和获取功能：`isDirectory()`, `isFile()`, `exists()`, `getAbsolutePath()`, `getPath()`（得到封装的路径）, `getName()`, `list()`返回该目录下的文件和目录，结果为`String[]`, `listFiles()`返回该目录下的文件和目录，结果为`File[]`

- File的删除功能`delete()`删除该文件或目录，如果目录不是空文件夹，那么删除不成功

- IO流分为字节流和字符流

- InputStream，OutputStream是抽象类，其子类后缀为父类的名称

- `FileOutputStream(String name)`创建文件输出流以指定的名称写入文件，它做了三件事情：调用系统功能创建文件，创建了字节输出流对象，让字节输出流对象指向创建好的文件，最后要调用`close()`关闭此输出流并释放于此流相关联的任何系统资源；`FileOutputStream(String name, boolean append)`可以实现追加写入

- 字节流写数据的三种方式：`write(int b)`一次写一个字节数据，`write(byte[] b)`写一个字节数组数据（`"abc".getBytes()` 返回byte[]），`write(byte[] b, int off, int len)`从索引off开始写入len个字节

- finally：在异常处理的时候提供finally块来执行所有清除操作，比如IO流中的释放资源，被finally控制的语句一定会执行，除非JVM退出

- `FileInputStream`的读方法：`int read()`一次读一个字节，如果文件到达末尾，返回-1；`int read(byte[] b)`读取最多b.length个字节到该数组，返回实际读取的长度，如果文件到达末尾，返回-1；

- `BufferedOutputStream(OutputStream out)`是缓冲输出流，通过设置这样的输出流，应用程序可以向底层输出流写入字节，而不必为写入的每个字节导致底层系统的调用，`BufferedInputStream(InputStream in)`是字节缓冲输入流，将创建一个内部缓冲区数组，当从流中读取或跳过字节时，内部缓冲区将根据需要从所包含的输入流中重新填充，一次很多字节；字节缓冲流仅提供缓冲区，而真正的读写数据还得依靠基本的字节流对象进行操作，操作方法名称与基本字节流对象一样；字节缓冲流可以节省时间

- 汉字存储：GBK 2字节，UTF-8 3字节，汉字在存储的时候，无论选择哪种编码存储，第一个字节都是负数，`byte[] getBytes(String charsetName)`编码，`new String(byte[] b, String charsetName)`解码

- 字符输入流的抽象类Reader，字符输出流的抽象类Writer，`osw = new OutputStreamWriter(OutputStream out, String charsetName)`创建字符输出流对象（字符集也可以不指定），`osw.write(String str)`；`isr = new InputStreamReader(InputStream in, String charsetName)`创建字符输入流对象，其方法`int read()`读取一个字符，返回值可强制转换为char

- 字符流写数据5种方式：`write(int c)`, `write(char[] cbuf)`, `write(char[] cbuf, int off, int len)`, `write(String str)`, `write(String str, int off, int len)`

- 字符输出流`close()`或`flush()`都会把缓冲区写入文件

- 字符流读数据：`int read()`, `int read(char[] cbuf)`用法和字节流类似

- `FileReader(String fileName)`继承自`InputStreamReader`, `FileWriter(String fileName)`继承自`OutputStreamWriter`，用法都类似

- 字符缓冲流`BufferedReader(Reader in, int sz)`, `BufferedWriter(Writer out, int sz)`

- 字符缓冲流的特有功能：`BufferedWriter`可用`void newLine()`写一行行分隔符，`BufferedReader`可用`String readLine()`读一行文字，结果不包含行终止符，如果文件到达结尾则返回null

- `File`的`listFiles()`方法可以获取该目录下所有文件，返回`File[]`

- IO异常处理的改进方案：

  ```java
  try (FileWriter fr = new FileWriter("x.txt"); 
       FileWriter fw = new FileWriter("xx.txt")) {
      char[] chs = new char[1024];
      int len;
      while ((len = fr.read(chs)) != -1) {
          fw.write(chs, 0, len);
      }
  } catch (IOException e) {
      e.printStackTrace();
  }
  ```

- System类中有两个静态成员变量：`public static final InputStream in`是标准输入流，对应于键盘输入或由主机环境或用户指定的另一个输入源，`public static final PrintStream out`是标准输出流，对应于显示输出或由主机环境或用户指定的另一个输出目标，`PrintStream`继承了`OutputStream`

- ```java
  InputStreamReader isr = new InputStreamReader(System.in); //把字节流转为字符流，实现从键盘读取字符
  BufferedReader br = new BufferedReader(isr); //用字符缓冲流一次从键盘读取一行数据
  ```

- `Scanner sc = new Scanner(System.in);`可以比较方便的实现键盘输入

- 字节打印流`PrintStream`，字符打印流`PrintWriter`，打印流只负责输出数据，不负责读取数据，有自己特有的方法；

- `PrintStream(String fileName)`的特有方法有`print()`和`println()`，它使用`write(97)`和`print(97)`一个输出a，一个输出97

- `PrintWriter(String fileName)或者PrintWriter(Writer out, boolean autoFlush)`的特有方法有`print()`和`println()`，如果`autoFlush`为真，则`println`, `printf`, `format`方法会刷新输出缓冲区

- 对象序列化就是将对象保存到磁盘中，或在网络中传输对象，这种机制就是使用一个字节序列表示一个对象，该字节序列包含：对象的类型、对象的数据和对象中存储的属性等信息，字节序列写到文件之后，相当于文件中持久保存了一个对象的信息，反之，该字节序列还可以从文件中读取回来，重构对象，对它进行反序列化
- `ObjectOutputStream(OutputStream out)`使用方法`void writeObject(Onject obj)`将指定的对象（必须实现Serializable接口）写入
- Serializable是一个标记接口，实现该接口，不需要重写任何方法
- `ObjectInputStream(InputStream in)`使用方法`Object readObject()`读取一个对象
- 用对象序列化流序列化一个对象后，加入修改了对象所属类文件，读取数据会出问题，抛出InvalidClassException异常；可以给该类加上`private static final long serialVersionUID = 42L;`来解决此问题；不想被序列化的成员变量可以加`transient`修饰
- `Properties`是一个Map体系的集合类，可以保存到流中或从流中加载，它的特有方法有`Object setKey(String key, String value)`, `String getProperty(String key)`, `Set<String> stringPropertyNames()`
- `Properties`和IO流结合的方法：`void load(InputStream inStream)`, `void load(Reader reader)`, `void store(OutputStream out, String comments)`, `void store(Writer writer, String comments)`
- 定义一个类继承`Thread`类，重写`run()`方法，但是要用`start()`方法启动线程（该方法用JVM调用`run()`方法），才能实现多线程
- `Thread`类可用`setName(String name)`和`getName()`设置和查看名称
- `Thread`类有一个静态方法`Thread currentThread()`返回当前正在执行的线程对象，可获得main方法所在的线程
- Java使用抢占式调度模型（优先级高的线程获取相对较多的CPU时间片），`Thread`类中的方法`getPriority()`和`setPriority(int newPriority)`可以设置和获取线程优先级，`MIN_PROORITY=1`, `MAX_PRIORITY=10`，默认优先级为5
- `static void sleep(long millis)`使当前正在执行的线程暂停执行指定的毫秒数，`void join()`等待这个线程死亡，`void setDaemon(boolean on)`将此线程标记为守护线程，当运行的线程都是守护线程时，JVM将退出
- sleep使得线程从运行进入阻塞状态，sleep结束后从阻塞转为就绪

- 多线程的另一种实现方式：定义一个MyRunnable类实现Runnable接口并重写run接方法，用一个MyRunnable类的对象作为创建Thread类对象的构造方法的参数，同一个MyRunnable类对象可以在不同Thread的构造中使用

- 相比于继承Thread类，实现Runnable有如下好处：避免了Java单继承的局限性，适合多个相同程序的代码去处理同一个资源的情况，把线程和程序的代码、数据有效分离，较好的体现了面向对象的设计思想

- 同步代码块格式：

  ```java
  synchronized(任意对象作为锁) {
  	多条语句操作共享数据的代码
  }
  ```

- 同步方法：`private synchronized void method()`，它的锁对象是`this`

- 同步静态方法：`static synchronized void method()`，它的锁对象是`类名.class`

- 线程安全的类包括：StringBuffer，Vector，Hashtable，他们的方法加了synchronized，但StringBuilder，ArrayList，HashMap的方法没有加synchronized，因此是线程不安全的。

- `Collections.synchronizedList(new ArrayList<String>())`返回一个线程安全的List

- `Lock`接口提供了方法`lock()`和`unlock()`来获得锁和释放锁，`ReentrantLock`是`Lock`的实现类，为了防止代码块出问题，可以使用：

  ```java
  try {
  	lock.lock();
      代码
  } finally {
      lock.unlock();
  }
  ```

- `Object`类有一些方法：`void wait()`导致当前线程等待，直到另一个线程调用该对象的`notify()`方法或`notifyAll()`方法，`void notify()`唤醒正在等待对象监视器的单个线程，`void notifyAll()`唤醒正在等待对象监视器的所有线程。使用`wait`的方法应该为`syschronized`

- 网络编程三要素：IP地址，端口号，协议

- `InetAddress`类表示IP地址，使用静态方法`getByNmae(String host)`（参数可以为主机名，也可以为IP地址字符串）得到该类的一个对象，使用`getHostName()`获取此IP地址的主机名，使用`getHostAddress()`返回此IP地址字符串

- UDP发送数据步骤：创建`DatagramSocket()`，创建`DatagramPacket(byte[] buf, int length, InetAddress address, int port)`，调用`DatagramSocket`的方法`void send(DatagramPacket p)`发送数据，调用`DatagramSocket`的方法`void close()`关闭发送端

- UDP接收数据步骤：创建`DatagramSocket(int port)`，创建`DatagramPacket(byte[] buf, int length)`用于接收数据，调用`DatagramSocket`对象的`void receive(DatagramPacket p)`接收数据，调用`DatagramPacket`的`byte[] getData()`和`int getLength()`得到数据，调用`DatagramSocket`的方法`void close()`关闭发送端。

- TCP发送数据：创建客户端Socket对象`Socket(InetAddress address, int port)`，用Socket的`OutputStream getOutputStream()`方法获取输出流，用OutputStream的`write()`方法写数据，最后用`Socket`的`close()`

- TCP接收数据：创建服务端Socket对象`ServerSocket(int port)`，用`ServerSocket`的`Socket accept()`方法侦听要连接到此套接字并接受它，用`Socket`的`InputStream getInputStream()`方法获取输入流，用`InputStream`的`int read(byte[] b)`方法读数据，最后关闭`Socket`和`ServerSocket`对象释放资源