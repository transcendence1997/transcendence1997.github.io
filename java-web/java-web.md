# JavaWeb

## 数据库

- MySQL的数据库以文件夹的形式存储，`.frm`是表文件，`.MYD`是数据文件，两者组合起来就可以展示二维表

- SQL的`--` 注释后必须加空格

- SQL中null值的比较不能用`=`，`!=`，需要使用`is`，`is not`

- SQL中like查询：`_`代表单个任意字符

- SQL中null值不参与所有聚合函数运算

- MySQL事务默认自动提交，`SELECT @@autocommit`用来查看事务的默认提交方式（1为自动提交，0为手动提交，手动提交意味着执行完一条update语句需要再执行commit语句才能让修改生效），`SET @@autocommit`修改事务的默认提交方式

- `com.mysql.jdbc.Driver`类的静态代码块里面调用了`DriverManager.registerDriver()`注册驱动

- JDBC的关键使用步骤：用DriverManager获取Connection，用Connection获取Statement，用Statement执行SQL

## MyBatis

- Maven中导入MyBatis的同时也要导入JDBC

- MyBatis的关键使用步骤：通过加载核心配置文件获取SqlSessionFactory，通过SqlSessionFactory获取SqlSession（这里可以设置事务为自动提交），用SqlSession获取XxxMapper接口（自己根据数据库表名定义这个接口，而且这个接口有对应的配置文件XxxMapper.xml，里面定义了SQL语句，也就是调用接口方法需要执行的SQL语句）的对象，调用XxxMapper接口的对象的方法执行SQL

- MyBatis核心配置文件中，配置各个标签须遵循前后顺序

- MyBatis的Mapper配置文件中，要定义resultMap以解决数据库和代码字段名称不一致的问题，参数占位符用`#{}`可以防止SQL注入，`${}`用于表名或列名不固定的情况，如果方法里面要接受多个参数，那么需要用`@Param(SQL占位符名称)`区分这个方法里的参数传到哪个占位符

- set和where标签里面嵌套if可以用来处理动态字段

- insert语句要配置主键返回`useGeneratedKeys="true" keyProperty="id"`

- delete语句用foreach标签完成批量删除

- MyBatis会将数组参数封装为名称为"array"的key对应的value，可以用`@Param`注解改变这个key的名称（对于）

- 如遇多个参数：MyBatis会将这多个参数封装进Map集合，其中key有默认名称，为增强可读性，可用`@Param`注解设定key的名称

- 如遇单个参数：如果是POJO或Map类型，那么配置文件中SQL的占位符中可以直接属性名/键名；除此之外，MyBatis会将这个参数封装进Map集合，其中key有默认名称，为增强可读性，可用`@Param`注解设定key的名称

- 对于简单的SQL语句，可以不用写在配置文件中，而是写在注解（在接口的方法名之上）中

## 前端

- 表单项数据要想被提交，必须指定其name属性

- 表单的method：1. get：请求参数拼接在url后边，url长度限制为4kB；2. post：请求参数会在http请求协议的请求体中，请求参数无限制

- 用label标签实现点击文字的效果

- JSON的键需要加双引号，JavaScript对象的键不需要加双引号

- js里面的`JSON.parse()`可将JSON字符串转为js对象，用`JSON.stringify()`将js对象转为JSON字符串

## 后端

- JavaWeb三大组件：Servlet，Filter，Listener

- http的两种请求方式：1. GET：没有请求体，资源路径及参数存放在请求行中，参数有大小限制；2. POST: 有请求体，资源路径放在请求行中，参数放在请求体中，参数没有大小限制

- 服务器软件的作用就是接收HTTP请求，解析请求，并发送HTTP响应

- Web项目用Maven打成war包，然后放到Tomcat的webapps目录下部署

- Servlet是一个接口，他的实现类的对象由Tomcat服务器创建，通过配置路径（注解或xml）来访问这个对象，访问的时候会调用里面重写的serve方法来提供服务

- Servlet路径的扩展名匹配不能加斜杠

- Servlet路径如果是"/"，那么Tomcat中的默认Servlet（他的路径也是"/"）会被覆盖，从而导致静态资源无法访问

- 请求转发是一种在服务器内部的资源跳转方式（在资源A处理了一部分，然后转发到资源B接着处理），用`request.getRequestDispatcher(路径名).forward(request, response)`实现转发

- 请求转发通过Request对象的set，remove，getAttribute方法共享数据

- 重定向：后端发送给前端一个状态码为302的响应，并附上一个地址，前端收到后就会跳转到该地址，用`response`的`sendRedirect`方法可以实现

- 重定向两次请求不能在多个资源使用request共享数据

- 重定向可以跳转到服务器内部或外部的资源，但请求转发只能跳转到服务器内部资源

- 请求转发不会使浏览器地址发生变化，重定向会

- 路径问题：如果给浏览器使用，需要加虚拟目录（例如重定向、前端超链接）；如果给服务端使用，就不需要加虚拟目录（例如请求转发）

- `request.getContextPath()`可以获取虚拟目录的值

- 响应头中需要设置content type（里面可以设置响应数据格式和字符集），从而让浏览器解析数据

- 使用JSP需要在Maven中导入相关坐标

- JSP的原理：Tomcat将jsp文件转成Servlet，通过不同类型的JSP脚本可以将Java代码插入到Servlet的不同位置（`_jspService`方法内，`out.print`语句中，成员位置）

- JSP+Servlet：Servlet负责逻辑处理，再请求转发到JSP；JSP负责展示，用EL表达式获取域（page，request，session，application）中数据，JSTL（要Maven引入依赖）用来简化Java代码书写

- MVC模式：Model，业务模型，处理业务（JavaBean）；View，视图，界面展示（JSP）；Controller，控制器，处理请求，调用模型和视图（Servlet）

- 三层架构：数据访问层（MyBatis，Hibernate）：对数据库的CRUD；业务逻辑层（Spring）：组合数据访问层中基本功能，形成复杂的业务逻辑功能；表现层（SpringMVC，Structs2）：接收请求，封装数据，调用业务逻辑层，响应数据（Controller，View）

- Servlet代码不能复用，所以要有Service层

- 三层架构是对MVC模式的实现：表现层对应Controller和View，Model对应业务逻辑层和数据访问层

- 会话：用户打开浏览器，访问web服务器的资源，会话建立，直到有一方断开连接，会话结束。一次会话可以包含多次请求和响应。

- 会话跟踪：一种维护浏览器状态的方法，服务器需要识别多次请求是否来自同一浏览器，以便在同一次会话的多次请求间共享数据（HTTP协议是无状态的）

- Cookie是客户端会话跟踪技术，将数据保存到客户端，以后每次请求都携带Cookie数据进行访问

- 一个Cookie就是一个键值对，由服务端创建（`new Cookie()`）并发送（`response.addCookie()`），服务端也可以获取（`request.getCookies()`）

- Cookie的实现是基于HTTP协议：HTTP响应头里面的`set-cookie`字段告诉浏览器要设置Cookie，浏览器发出的请求头里面的`cookie`字段用来携带发给服务端的Cookie

- 浏览器在**内存**中存储了每个网站（服务端）发过来的Cookie，在浏览器设置中可以查看，当浏览器关闭，内存释放，则Cookie被销毁

- Cookie也可以实现持久化：用`setMaxAge(int seconds)`方法，若参数为负数（默认值），则Cookie仍放在内存中，若参数为0，则删除对应的Cookie，做参数为正数，则将Cookie写入硬盘，到时间自动删除

- Cookie存中文要用URL编码

- Session是服务端会话跟踪技术，将数据保存在服务端，后端用`request.getSession()`获取Session对象，用Session的方法可以设置键值对，值可以是任意对象，不一定是字符串

- Session是基于Cookie实现的：服务端会用Cookie将Session的id发给浏览器，后面浏览器的请求里的Cookie都会携带这个Session id

- Session钝化：在服务器正常关闭后，Tomcat会自动将Session数据写入硬盘的文件中

- Session活化：再次启动服务器后，从文件中加载数据到Session中，而且文件会被删除掉

- 浏览器关闭后再去访问同一个网页，获取到的Session不是同一个，这样关闭掉的浏览器就会产生很多不用的Session，因此默认情况下，Session无操作30分钟（失效时间可以在项目的web.xml或tomcat的web.xml配置）自动销毁，也可以调用`session.invalidate()`手动销毁（可以实现登出功能）

- Cookie最大3KB，Session无大小限制

- JSP中可用EL表达式获取Cookie：`${cookie.key.value}`

- 验证码展示：在img标签里面的src属性里面写一个Servlet路径，把验证码图片放到这个Servlet的response的outputstream中，刷新验证码可以给这个路径后面添加一个每次都不一样的参数，例如时间

- Filter接口的核心方法是`doFilter(ServletRequest request, ServletResponse response, FilterChain chain)`，用`@WebFilter`配置Filter拦截资源的路径，Filter一般用于做一些通用的操作

- Filter的执行流程：放行前逻辑（可以对request的数据进行处理，此时response还没有数据），放行`chain.doFilter(request, response)`（放行后访问对应资源资源访问完成后，还会回到Filter中执行放行后逻辑），放行后逻辑（可以对response的数据进行处理）

- 过滤器链的执行顺序类似于栈

- 注解配置的Filter，优先级按照过滤器类名自然排序

- 实现登录功能时，跟登录和注册相关的资源要放行

- Listener可以在application（ServletContext），session，request三个对象创建、销毁、增删改属性时自动执行代码，有八种Listener接口，创建一个类去实现里面的方法（会被自动调用），类上加`@WebListener`注解

- 用HTML+AJAX可以替换JSP，英文AJAX可以给服务器发送请求，并获取服务器响应的数据

- Axios对原生的AJAX代码进行封装，简化书写，需要引进js文件

- axios会把js对象自动转为JSON字符串发给后端

- 后端导入fastjson，然后就可以用`JSON.toJSONString()`把java对象转为JSON字符串，用`JSON.parseObject(String, Class)`把JSON字符串转为java对象

### 面试前背诵

- HTTP请求格式，GET和POST的区别

- HTTP响应格式，状态码的分类，常见状态码
