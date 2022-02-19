# Spring Security

### 如何用Spring Security实现用户认证和授权

1. 创建 `LoginUser` 类实现 `UserDetails`，这个类中包含了用户名、密码、权限（列表）信息。
2. 实现 `UserDetailsServiceImpl` 中的 `loadUserByUsername`：根据传进来的 `username` 从数据库中查询用户信息（密码和权限），查到之后把这些信息封装在一个 `LoginUser` 对象中。
3. 创建配置类 `SecurityConfig` 继承 `WebSecurityConfigurerAdapter`：（1）在里面配置 `PasswordEncoder` 为 `BCryptPasswordEncoder`；（2）注入 `AuthenticationManager`；（3）配置各个接口的权限，在controller中也要加上注解。
4. 前端调用登录接口，传入用户名和密码，后端登录接口完成如下操作：（1）用传入的用户名和密码创建一个 `UsernamePasswordAuthenticationToken`，调用 `authenticationManager` 的 `authenticate` 方法（`authenticate` 方法的参数就是这个用户名密码的token）；（2）`authenticate` 方法会调用刚才写的方法从数据库中查询用户信息，如果这个方法返回的值非空，可以从它的返回对象中获取一个 `LoginUser` 对象，里面包含了用户的信息，在Redis中保存一个（用户id，`LoginUser`）的映射；（3）根据查询到的用户id创建一个JWT，将这个JWT、用户名、用户权限信息（前端需要用到）返回给前端。
5. 定义 `JwtAuthenticationTokenFilter` 类继承 `OncePerRequestFilter`，重写 `doFilterInternal` 方法：从前端发来的请求中获取JWT（如果不带JWT就放行），解析JWT获得用户id（解析失败就抛异常），从Redis中查询用户信息，将这些用户信息存入 `SecurityContextHolder`（后面的filter会从 `SecurityContextHolder` 中获取用户信息）。
6. 在 `SecurityConfig` 类中：把 `jwtAuthenticationTokenFilter` 添加到 `UsernamePasswordAuthenticationFilter` 的前面。
7. 实现退出登录接口：从 `SecurityContextHolder` 中获取用户信息，通过用户id删除Redis中相应的映射。

