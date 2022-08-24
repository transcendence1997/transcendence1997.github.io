## Spring Framework

- 使用Spring可以充分解耦，这体现在：使用IoC容器管理Bean（控制反转，IoC），在IoC容器内将有依赖关系的bean进行关系绑定（依赖注入，DI），结果就是使用对象时不仅可以从IoC容器中直接获取，并且获取到的bean已经绑定了所有依赖关系

- 使用Spring要在Maven中导入依赖spring-context

- 在Spring的配置文件中，配置容器要管理的bean（要配类而不是接口），然后把这个文件作为参数创建一个AppicationContext接口的对象（`new ClassPathXmlApplicationContext(filename)`），这样就获取到了IoC容器对象，通过这个容器对象的方法`getBean()`获取Bean

- 如果Bean A依赖另一个Bean B，需要在Bean A中提供一个set方法用来设定B的实现类（这个set方法是给容器调用的），然后再配置文件中对Bean A配置对Bean B的依赖

- Spring创建的Bean默认是单例的，也可以用scope配置为非单例的
