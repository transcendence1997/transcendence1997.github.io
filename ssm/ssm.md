## Spring Framework

- 使用Spring可以充分解耦，这体现在：使用IoC容器管理Bean（控制反转，IoC），在IoC容器内将有依赖关系的bean进行关系绑定（依赖注入，DI），结果就是使用对象时不仅可以从IoC容器中直接获取，并且获取到的bean已经绑定了所有依赖关系

- 使用Spring要在Maven中导入依赖spring-context

- 在Spring的配置文件中，配置容器要管理的bean（要配类而不是接口），然后把这个文件作为参数创建一个AppicationContext接口的对象（`new ClassPathXmlApplicationContext(filename)`），这样就获取到了IoC容器对象，通过这个容器对象的方法`getBean()`获取Bean

- 如果Bean A依赖另一个Bean B，需要在Bean A中提供一个set方法用来设定B的实现类（这个set方法是给容器调用的），然后再配置文件中对Bean A配置对Bean B的依赖

- Spring创建的Bean默认是单例的，也可以用scope配置为非单例的

- Bean的三种实例化方法，在配置文件中配置：使用无参构造方法；使用工厂类的静态方法（静态工厂）；使用FactoryBean+工厂类的非静态方法（实例工厂，有个简化版是实现FactoryBean接口并使用其中非静态方法`getObject()`）

- Bean的生命周期控制操作：可以在配置文件中配置Bean初始化时，销毁前所要执行的方法，要想看到销毁时的方法执行，需要在jvm退出前关闭context（显式调用close方法，或者registerShutDownHook）；不用配置文件的话，也可以通过把Bean的类去实现`InitializingBean`和`DisposableBean`接口并重写其中的方法`afterPropertiesSet()`（在对象的属性设置完后才执行）和`destroy()`

- Bean的初始化过程：创建对象（内存分配），执行构造方法，执行属性注入（set操作），执行bean初始化方法

- 依赖注入的方式：按方法分为setter注入（配置文件中用property）和构造器注入（配置文件中用constructor-arg），按数据类型分为引用数据类型注入（配置文件中用ref）和简单数据类型（配置文件中用value）

- IoC容器可以实现依赖自动装配，就是根据bean所依赖的资源在容器中自动查找并注入到bean中，在配置文件里用bean标签的autowire属性指定自动装配方式（按类型，按名称等）

- 自动装配优先级低于setter注入与构造器注入，同时出现时自动装配失效

- 配置文件配置依赖注入也可以注入集合类型的数据：数组，List，Set，Map，Properties
