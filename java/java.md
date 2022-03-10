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

- TCP发送数据：创建客户端Socket对象`Socket(InetAddress address, int port)`，用Socket的`OutputStream getOutputStream()`方法获取输出流，用OutputStream的`write()`方法写数据，用Socket的方法`public void shutdownOutput()`禁用此Socket的输出流（任何先前写入的数据将被发送，随后是TCP的正常连接中止序列），用Socket的`InputStream getInputStream()`方法获取输入流（读取服务端的反馈数据），最后用Socket的`close()`

- TCP接收数据：创建服务端Socket对象`ServerSocket(int port)`，用`ServerSocket`的`Socket accept()`方法侦听要连接到此套接字并接受它，用`Socket`的`InputStream getInputStream()`方法获取输入流，用`InputStream`的`int read(byte[] b)`方法读数据（读数据的方法是阻塞式的，只要没读到就一直等待），用`Socket`的`OutputStream getOutnputStream()`方法获取输出流（反馈数据给客户端），最后关闭`Socket`和`ServerSocket`对象释放资源

- Lambda表达式的标准格式：`(形式参数)->{代码块}`，参数的类型可以省略；如果参数只有一个，小括号也能省略；如果代码块语句只有一条，那么大括号、分号、return（如果有）可以省略；如果方法带返回值

- Lambda表达式的使用前提：有一个接口，接口中有且仅有一个抽象方法；必须有上下文环境，才能推导出Lambda对应的接口（根据局部变量的赋值得知Lambda对应的接口，或根据调用方法的参数得知Lambda对应的接口）

- 匿名内部类编译之后会产生一个单独的`.class`字节码文件；但Lambda表达式没有一个单独的`.class`字节码文件，它对应的字节码会在运行的时候动态生成

- 接口中的默认方法（Java 8）：`public default void method() {}`，public可省略；默认方法不是抽象方法，不强制被重写，但是可以被重写，重写的时候去掉default关键字

- 接口中的静态方法（Java 8）：`public static void method() {}`，public可省略；不可以用接口实现类或实现类对象调用静态方法，只能用接口名调用

- 接口中的私有方法（Java 9）：`private void method() {}`或`private static void method() {}`，可将默认方法或静态方法中相同的代码段放到私有方法中，默认方法可以调私有方法和私有静态方法，但静态方法只能调私有静态方法

- 方法引用符`::`所在的表达式称为方法引用，用来简化Lambda表达式（可推导就是可省略），

- 引用类方法`类名::静态方法`，Lambda表达式被类方法替代的时候，他的形式参数全部传递给静态方法作为参数

- 引用对象的实例方法`对象::成员方法`，Lambda表达式被对象的实例方法替代的时候，它的形式参数全部传递给该方法作为参数

- 引用类的实例方法`类名::成员方法`，Lambda表达式被类的实例方法替代的时候，它的第一个参数作为调用者，后面的参数全部传递给该方法作为参数

- 引用构造器`类名::new`，Lambda表达式被构造器替代的时候，它的形式参数全部传递给构造器作为参数

- 函数式接口：有且仅有一个抽象方法的接口，注解`@FunctionalInterface`加在接口定义之上就可以限制该接口为函数式接口

- `Runnable`是一个函数式接口，`Comparator<T>`是一个函数式接口

- 函数式接口`Supplier<T>`的方法`T get()`

- 函数式接口`Consumer<T>`的方法`void accept(T t)`对给定的参数执行此操作，还有个默认方法`default Consumer<T> andThen(Consumer after)`返回一个组合的Consumer，依次执行此操作，然后执行after操作（`cons1.andThen(cons2).accept("abc")`会依次调用cons1和cons2的accept方法对字符串进行操作）

- 函数式接口`Predicate<T>`的方法`boolean test(T t)`，还有几个默认方法`default Predicate<T> negate()`，`default Predicate<T> and(Predicate other)`（短路），`default Predicate<T> or(Predicate other)`（短路）

- 函数式接口`Function<T, R>`的方法`R apply(T t)`，还有默认方法`default <V> Function andThen(Function after)`

- Stream流的使用：1.生成流：通过数据源（集合、数组等）生成流；2.中间操作：一个流后面可以跟随零个或多个中间操作，其目的主要是打开流，做出某种程度的数据过滤/映射，然后返回一个新流，交给下一个操作使用；3.终结操作：一个流只能有一个终结操作，这必定是流的最后一个操作

- Stream流的生成方式：Collection体系的集合用默认方法`default Stream<E> stream()`，数组用静态方法`Stream.of(T... values)`

- Stream流的中间操作：`Stream<T> filter(Predicate predicate)`用于对流中的数据进行过滤；`Stream<T> limit(long maxSize)`返回此流中的元素组成的流，截取前指定参数个数的数据；`Stream<T> skip(long n)`跳过指定参数个数的数据，返回由该流的剩余元素组成的流；`Stream<T> distinct()`返回由该流的不同元素（根据`equals`）组成的流；`static <T> Stream<T> concat(Stream a, Stream b)`合并两个流；`Stream<T> sorted(Comparator comparator)`根据comparator（可省略）进行排序；`<R> Stream<R> map(Function mapper)`将给定函数应用于此流元素；`IntStream mapToInt(ToIntFunction mapper)`将给定函数应用于此流元素（`ToIntFunction`接口中的方法`int applyAsInt(T value)`，`IntStream`有一个方法`int sum()`返回此流中元素之和）

- Stream流的终结操作：`void forEach(Consumer action)`对此流中每个元素执行操作；`long count()`返回此流中的元素数

- Stream流的收集操作：`R collect(Collector collector)`可以把流中的数据收集到集合中

- 工具类`Collectors`提供了具体的收集方式：`public static <T> Collector toList()`把元素收集到List集合中，`public static <T> Collector toSet()`把元素收集到Set集合中，`public static Collector toMap(Function keyMapper, Function valueMapper)`把元素收集到List集合中

- 当程序要使用某个类时，如果该类还未被加载到内存中，则系统会通过类的加载，类的连接，类的初始化三个步骤来对类进行初始化，如果不出现意外情况，JVM将会连续完成这三个步骤。

- 类的加载：就是指将class文件读入内存，并为之创建一个java.lang.Class对象，任何类被使用时，系统都会为之建立一个java.lang.Class对象

- 类的连接：验证阶段：用于检验被加载的类是否有正确的内部结构，并和其他类协调一致；准备阶段：负责为类的类变量分配内存，并设置默认初始化值；解析阶段：将类的二进制数据中的符号引用替换为直接引用

- 类的初始化：在该阶段，主要就是对类变量进行初始化

- 类的初始化步骤：假如类还未被加载和连接，则程序先加载并连接该类；假如该类的直接父类还未被初始化，则先初始化其直接父类；加入类中有初始化语句，则系统依次执行这些初始化语句（在执行第二个步骤时，系统对直接父类的初始化步骤也遵循初始化步骤1-3）

- 类的初始化时机：创建类的实例；调用类的类方法；访问类或者接口的类变量，或者为该类变量赋值；使用反射方式强制创建某个类或接口对应的java.lang.Class对象；初始化某个类的子类；直接使用java.exe命令来运行某个主类

- 类加载器的作用：将.class文件加载到内存中，并为之生成对应的java.lang.Class对象

- JVM的类加载机制：全盘负责（当一个类加载器负责加载某个Class时，该Class所依赖的引用和引用的其他Class也将由该类加载器负责载入，除非显式使用另一个类加载器来载入），父类委托（当一个类加载器负责加载某个Class时，先让父类加载器试图加载该Class，只有在父类加载器无法加载该类时才尝试从自己的类路径中加载该类），缓存机制（保证所有加载过的Class都会被缓存，当程序需要使用某个Class对象时，类加载器先从缓存区中搜索该Class，只有当缓存区中不存在该Class对象时，系统才会读取该类对应的二进制数据，并将其转换成Class对象，存储到缓存区）

- ClassLoader是负责加载类的对象；Java运行时具有以下内置类加载器：Bootstrap class loader（虚拟机的内置类加载器，通常表示为null，并且没有父null），Platform class loader（平台类加载器，可以看到所有平台类，平台类包括由平台类加载器或其祖先定义的Java SE平台API，其实现类和JDK特定的运行时类），System class loader（应用程序类加载器，通常用于定义应用程序类路径，模块路径和JDK特定工具上的类）

- 类加载器的继承关系：System的父加载器为Platform，而Platform的父加载器为Bootstrap

- ClassLoader中两个方法：`static ClassLoader getSystemClassLoader()`返回用于委派的系统类加载器，`ClassLoader getParent()`返回父类加载器进行委派

- Java反射机制：在运行时去获取一个类的变量信息和方法信息，然后通过获取到的信息来创建对象，调用方法的一种机制。由于这种动态性，可以极大地增强程序的灵活性，程序不用在编译期就完成确定，在运行期仍然可以扩展

- 获取Class类对象的三种方式：`Student.class`, `new Student().getClass()`, `Class.forName(String className)`（该字符串参数的值是某个类的全路径，也就是完整包名的路径）

- 反射获取构造方法并使用：Class的方法`Constructor<?>[] getConstructors()`返回public的构造方法，`Constructor<?>[] getDeclaredConstructors()`返回所有的构造方法，`Constructor<T> getConstructors(Class<?>... parameterTypes)`返回指定的public构造方法，`Constructor<T> getDeclaredConstructors(Class<?>... parameterTypes)`返回指定的构造方法；使用`Constructor<T>`的`T newInstance(Obj... initargs)`可使用此构造函数；使用`Constructor`的`public void setAccessible(boolean flag)`（值为true时取消访问检查）可使用私有构造方法。

- 反射获取成员变量并使用：Class的方法`Field[] getFields()`返回所有公共成员变量，`Field[] getDeclaredFields()`返回所有成员变量，`Field getField(String name)`返回指定的公共成员变量，`Field getDeclaredField(String name)`返回指定的成员变量；Field的方法`void set(Object obj, Object value)`将指定的对象中由此Field对象表示的字段设置为指定的值；使用`Field`的`public void setAccessible(boolean flag)`（值为true时取消访问检查）可使用私有成员变量。

- 反射获取成员方法并使用：Class的方法`Method[] getMethods()`返回公共成员方法（包括继承过来的），`Method[] getDeclaredMethods()`返回所有成员方法，`Method getMethod(String name, Class<?>... parameterTypes)`返回指定的公共成员方法，`Method getDeclaredMethod(String name, Class<?>... parameterTypes)`返回指定的成员方法；Method的方法`Object invoke(Object obj, Object... args)`在指定对象上调用此方法，传入指定的参数；使用`Method`的`public void setAccessible(boolean flag)`（值为true时取消访问检查）可使用私有成员方法。

- 一个项目包含多个模块，一个模块包含多个包，一个包中包含多个类和接口，模块相互独立，应用程序可根据需要加载必须的模块

- 在模块的src目录下新建一个名为module-info.java的描述性文件，该文件专门定义模块名，访问权限，模块依赖等信息，描述性文件中使用模块导出和模块依赖来进行配置并使用

- 模块中所有未导出的包都是模块私有的，他们不能在模块外被访问；模块导出格式：`exports 包名;`

- 一个模块要访问其他的模块，必须明确指定依赖哪些模块，未明确指定依赖的模块不能访问；模块依赖格式：`requires 模块名;`（写模块名报错，需要按下Alt+Enter提示，然后选择模块依赖）

- 模块服务的使用步骤：

  - 在myOne模块下创建一个包com.itheima_03，在该包下提供一个接口MyService，接口中定义一个抽象方法`void service();`

  - 在包com.itheima_03下创建一个包impl，在该包下提供两个实现类Itheima和Czxy

  - 在myOne这个模块下的描述文件中添加如下配置：`exports com.itheima_03;`, `provides MyService with Itheima;`（指定MyService的服务实现类是Itheima）

  - 在myTwo这个模块下的描述性文件中添加如下配置：`uses MyService;`（声明服务接口）

  - 在myTwo这个模块的类中使用MyService接口提供的服务：

    ```java
    ServiceLoader<MyService> myServices = ServiceLoader.load(MyService.class);
    
    for (MyService my : myServices) {
    	my.service();//会调用Itheima类的实现
    }
    ```

    

