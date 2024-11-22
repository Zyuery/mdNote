# 1、创建项目

先通过Spring Initialzr创建好一个springboot项目

# 2、搭建数据库

建库语句（SQL语句）

```sql
CREATE DATABASE test
  CHARACTER SET utf8mb4
  COLLATE utf8mb4_general_ci;
```

建表语句（SQL语句）

```sql
CREATE TABLE user
(
    uid int(10) primary key NOT NULL AUTO_INCREMENT,
    uname varchar(30) NOT NULL,
    password varchar(255) NOT NULL,
    UNIQUE (uname)
);

```

# 3、环境配置

## 3.1maven配置

然后在IDEA中配置好maven路径

![image-20240703163946469](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20240703163946469.png)

## 3.2 数据库配置

先创建好数据库与java spring boot项目的连接。

![image-20240703165358707](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20240703165358707.png)



用户名和密码都是root

记得要在resource的application.properties里配置数据库的url

![image-20240703182157859](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20240703182157859.png)

```
spring.application.name=login_app
spring.datasource.url=jdbc:mysql://localhost:3306/database_learn
spring.datasource.username=root
spring.datasource.password=root
```



# 4、项目搭建

## 4.0 概论

**结构图**

![image.png](https://cdn.nlark.com/yuque/0/2024/png/26411187/1713671184591-1eaa108f-8494-406e-8d36-cc3f69e033e3.png?x-oss-process=image%2Fformat%2Cwebp)

![项目架构图](https://img-blog.csdnimg.cn/img_convert/037f6b505759d4a0a80b6f76705bdc9a.png)

**项目结构**

![image-20240704183120165](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20240704183120165.png)

## 4.1 搭建Dao层

  **数据持久层**是的目的是在**java对象与数据库之间建立映射**，也就是说它的作用是将某一个Java类对应到数据库中的一张表。

---

  在我们的项目中，就将创建一个实体类User映射到数据库的user表，表中的每个字段对应于实体类的每个属性。而之前配置的JPA的作用就是帮助我们完成类到数据表的映射。

---

* **repository**: 存放一些数据访问类（也就是一些能操纵数据库的类）的包，比如存放能对user表进行增删改查的类

- **domain**：存放实体类的包，比如User类，其作为对应数据库user表的一个实体类

**domain**
===

在domain中创建User.java

* **@Table(name = “user”**) 说明此实体类对应于数据库的user表
* **@Entity** 说明此类是个实体类
```java
package org.example.login_app.domain;

import jakarta.persistence.*;

@Table(name = "user")//说明此实体类对应于数据库的user表
@Entity//说明此类是个实体类
public class User {
    // 注意属性名要与数据表中的字段名一致
    // 主键自增int(10)对应long
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private long uid;
    public long getUid() {
        return uid;
    }
    public void setUid(long uid) {
        this.uid = uid;
    }
    @Column(name="uname")
    // 用户名属性varchar对应String
    private String uname;

    public String getUname() {
        return uname;
    }
    public void setUname(String uname) {
        this.uname = uname;
    }
    @Column(name="password")
    // 密码属性varchar对应String
    private String password;
    public String getPassword() {
        return password;
    }
    public void setPassword(String password) {
        this.password = password;
    }
}
```

注意：上述的uname、password属性的set和get方法，可以通过右键—生成—getter and setter直接实现。

# **repository**

在repository包中创建UserDao接口

添加一些**访问数据库的方法**(这里添加的是根据用户名查询用户方法)

* **@Repository**：说明这是接口文件

* **extends JpaRepository<User, Integer>**接口要继承`JpaRepository`，这样JPA就能帮助我们完成对数据库的映射，也就是说接口里写的方法只要符合格式可以不需要实现SQL语句就能直接用了。

如果JPA没有提供你想要的方法，可以自定义SQL语句

```java
package org.example.login_app.repository;

import org.example.login_app.domain.User;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository

public interface UserDao extends JpaRepository<User, Integer> {
    User findByUname(String uname);
    User findByUnameAndPassword(String uname, String password);
}
```

## 4.2 搭建service层

![image-20240703170737066](C:\Users\zengyue\AppData\Roaming\Typora\typora-user-images\image-20240703170737066.png)

**业务逻辑层**的作用是处理业务逻辑。

---

比如在本项目中，我们就在业务逻辑层实现登录注册的逻辑，像是判断是否有用户名重复，密码是否正确等逻辑

- service: 存放业务逻辑接口的包
- serviceImpl: 存放业务逻辑实现类的包，其中的类实现service中的接口

我们也可以直接在service包里直接把类声明（UserService接口）和类实现都写好（UserServicelmpl类）

# service

**UserService接口**

```java
package org.example.login_app.service;

import org.example.login_app.domain.User;

public interface UserService {
    User loginService(String uname, String password);
    User registService(User user);
}
```

**UserServicelmpl类**

* **implements UserService**代表该类是UserService接口的具体实现

### 4.2.1  添加implements UserService

- 添加`implements UserService`

  此时会报错，但没关系，只是因为方法还没实现。

  ![img](https://img-blog.csdnimg.cn/img_convert/5c8aec0c392694702280880d4676986e.png)

- 鼠标悬停在红色波浪线自动生成需要实现的方法（也可以手动一个个写）

  ![生成方法](https://img-blog.csdnimg.cn/img_convert/abc87bfabc58511acc6b59bb1227c0f3.png)

  ![s](https://img-blog.csdnimg.cn/img_convert/731d0aca52902f537e1621309dd82456.png)

- 生成方法后的样子

  ![生成方法后的样子](https://img-blog.csdnimg.cn/img_convert/274eb566e3252a5edc74d8bf7e71e6a8.png)

### 4.2.2 实现登录业务逻辑

  - 因为要用到UserDao中的方法，所以先通过`@Resource`注解帮助我们实例化UserDao对象
- 登录业务逻辑代码
  
```java
  @Resource
  private UserDao userDao;
  @Override
  public User loginService(String uname, String password) {
      // 如果账号密码都对则返回登录的用户对象，若有一个错误则返回null
      User user = userDao.findByUnameAndPassword(uname, password);
      // 重要信息置空
      if(user != null){
          user.setPassword("");
      }
      return user;
  }
```

### 4.2.3 实现注册业务逻辑

  * 注册业务逻辑代码

  ```java
  @Override
  public User registService(User user) {
      //当新用户的用户名已存在时
      if(userDao.findByUname(user.getUname())!=null){
          // 无法注册
          return null;
      }else{
        //返回创建好的用户对象(带uid)
          User newUser = userDao.save(user);
        if(newUser != null){
              newUser.setPassword("");
          }
          return newUser;
      }
  }
  ```

###     4.2.4 添加`@Service`注解

​      ![](https://img-blog.csdnimg.cn/img_convert/ab32b72bca6764bc8341c6dd882081c4.png)

###     4.2.5 最终UserServiceImpl完整代码

```java
package org.example.login_app.service.servicelmpl;

import jakarta.annotation.Resource;
import org.example.login_app.domain.User;
import org.example.login_app.repository.UserDao;
import org.example.login_app.service.UserService;
import org.springframework.stereotype.Service;

@Service
public class UserServicelmpl implements UserService {
  @Resource
  private UserDao userDao;

    @Override
    public User loginService(String uname, String password) {
        // 如果账号密码都对则返回登录的用户对象，若有一个错误则返回null
        User user = userDao.findByUnameAndPassword(uname, password);
        // 重要信息置空
        if(user != null){
            user.setPassword("");
        }
        return user;
    }

    @Override
    public User registService(User user) {
        //当新用户的用户名已存在时
        if(userDao.findByUname(user.getUname())!=null){
            // 无法注册
            return null;
        }else{
            //返回创建好的用户对象(带uid)
            User newUser = userDao.save(user);
            if(newUser != null){
                newUser.setPassword("");
            }
            return newUser;
        }
    }

}
```

### 4.2.6 utils和config

- **utils:** 存放工具类，一些自己封装的工具
- **config:** 存放配置类，一些配置如登录拦截器，安全配置等

#### 在utils包中创建Result类

  工具类Result的作用是作为返回给前端的统一后的对象。也就是说返回给前端的都是Result对象，只是对象中的属性不太一样，这样方便前端固定接收格式。

---

# utils

  在utils包中创建Result类，最终Result代码

``` java
package org.example.login_app.utils;

public class Result<T> {
    private String code;
    private String msg;
    private T data;

    public String getCode() {
        return code;
    }

    public void setCode(String code) {
        this.code = code;
    }

    public String getMsg() {
        return msg;
    }

    public void setMsg(String msg) {
        this.msg = msg;
    }

    public T getData() {
        return data;
    }

    public void setData(T data) {
        this.data = data;
    }

    public Result() {
    }

    public Result(T data) {
        this.data = data;
    }

    public static Result success() {
        Result result = new Result<>();
        result.setCode("0");
        result.setMsg("成功");
        return result;
    }

    public static <T> Result<T> success(T data) {
        Result<T> result = new Result<>(data);
        result.setCode("0");
        result.setMsg("成功");
        return result;
    }

    public static <T> Result<T> success(T data,String msg) {
        Result<T> result = new Result<>(data);
        result.setCode("0");
        result.setMsg(msg);
        return result;
    }

    public static Result error(String code, String msg) {
        Result result = new Result();
        result.setCode(code);
        result.setMsg(msg);
        return result;
    }
}
```

   可以看出Result是个**模板类**，因此想要返回什么数据类型给前端都行，如`Result`，要是没看懂没关系，看到下面就知道怎么用了。因为里面有很多静态方法，可以直接用`类名.方法名`调用。

## 4.3 搭建Controller层

- **控制层**的作用是接收视图层的请求并调用业务逻辑层的方法。比如视图层请求登录并发来了用户的账号和密码，那么控制层就调用业务逻辑层的登录方法，并将账号密码作为参数传入，在将结果返回给视图层。
  - controller: 存放控制器的包。比如UserController

---

# controller

先在controller包中创建UserController类

再添加`@RestController`与`@RequestMapping("/user")`注解，注入UserService

![img](https://img-blog.csdnimg.cn/img_convert/64f895206f6191ff555378a50a587d84.png)

### 4.3.1 实现登录的控制

这里的`@PostMapping("/login")`表示处理post请求，路由为/user/login

``` java
// POST 方法处理登录请求
    @PostMapping("/login")
    public Result<User> loginController(@RequestParam String uname, @RequestParam String password){
        User user = userService.loginService(uname,password);
        if(user!=null){
            return Result.success(user,"登录成功！");
        }else{
            return Result.error("123","账号或密码错误！");
        }
    }
```

### 4.3.2 实现注册的控制

这里的`@PostMapping("/register")`表示处理post请求，路由为/user/register

```java
// POST 方法处理登录请求
    @PostMapping("/register")
    public Result<User> registController(@RequestBody User newUser){
        User user = userService.registService(newUser);
        if(user!=null){
            return Result.success(user,"注册成功！");
        }else{
            return Result.error("456","用户名已存在！");
        }
    }
```

### 4.3.3 完整的UserController代码

```java
package org.example.login_app.controller;

import jakarta.annotation.Resource;
import org.example.login_app.domain.User;
import org.example.login_app.service.UserService;
import org.example.login_app.utils.Result;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/user")
public class UserController {
    @Resource
    private UserService userService;

    @PostMapping("/login")
    public Result<User> loginController(@RequestParam String uname, @RequestParam String password){
        User user = userService.loginService(uname, password);
        if(user!=null){
            return Result.success(user,"登录成功！");
        }else{
            return Result.error("123","账号或密码错误！");
        }
    }

    @PostMapping("/register")
    public Result<User> registController(@RequestBody User newUser){
        User user = userService.registService(newUser);
        if(user!=null){
            return Result.success(user,"注册成功！");
        }else{
            return Result.error("456","用户名已存在！");
        }
    }
}
```

### 4.3.4 建立视图映射

在controller里新建一个ViewController类

```java
package org.example.login_app.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
@RequestMapping("/user")
public class ViewController {
        // GET 方法返回登录页面
        @GetMapping("/login")
        public String loginPage(Model model) {
            // 可以向模板传递需要的数据
            model.addAttribute("pageTitle", "登录页面");
            return "login"; // 这里返回的是Thymeleaf模板的文件名，比如 login.html
        }
        // GET 方法返回注册页面
        @GetMapping("/register")
        public String registerPage(Model model) {
            // 可以向模板传递需要的数据
            model.addAttribute("pageTitle", "注册页面");
            return "register.html"; // 这里返回的是Thymeleaf模板的文件名，比如 register.html

    }

}
```



## 4.4 处理跨域访问问题

  **跨域问题**可以简单理解成如果你的前端项目的IP地址和端口号和后端的IP地址和端口号不一样，就会导致前端无法获取到数据，这是一个规定。

  而在前后端分离开发的项目中，前后端项目的端口号一般都是不一样的，假设我们这个项目的前端端口号是 8080，后端端口号是 8081，就会造成跨域访问的问题，跨域访问的问题可以在前端解决也可以在后端解决，后端只要加上一个配置文件就行了

# config

在`config`文件下创建全局跨域配置类`GlobalCorsConfig.java`
注意 ：

SpringBoot2.4.0 以后下方 `allowedOrigins` 需要被` allowedOriginPatterns` 代替

```JAVA
package org.example.login_app.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.CorsRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

@Configuration
public class GlobalCorsConfig {
    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")    //添加映射路径，“/**”表示对所有的路径实行全局跨域访问权限的设置
                        .allowedOriginPatterns("*")    //开放哪些ip、端口、域名的访问权限 SpringBoot2.4.0以后allowedOrigins被allowedOriginPatterns代替
                        .allowCredentials(true)  //是否允许发送Cookie信息
                        .allowedMethods("GET", "POST", "PUT", "DELETE")     //开放哪些Http方法，允许跨域访问
                        .allowedHeaders("*")     //允许HTTP请求中的携带哪些Header信息
                        .exposedHeaders("*");   //暴露哪些头部信息（因为跨域访问默认不能获取全部头部信息）
            }
        };
    }
}
```

处理跨域问题是为前后端分离开发做铺垫，这里这样配置好就行了，暂时放着不需要管，等开发前端 Vue 项目时就不会出问题了。

## 4.5 API 层

略，纯后端开发使用postman进行测试。

# 总结

**`domain`**中的**`User.java`**这个实体类，就是写一些与数据库对应的表，并且生成表的属性的get和set方法。

**`repository`**中的**`UserDao.java`**这个接口，就是要写一些访问数据库表的方法（通过表的属性访问表中的具体用户）

**`service`**中的**`UserService.java`**这个接口，就是要写业务逻辑的类声明，而**`UserServicempl.java`**这个类就是要写具体的类实现。这里的业务逻辑指的是通过表中对象进行的操作或者就是直接对表中对象进行操作。

**`controller`**中的**`UserController.java`**这个类，就是要写一些路由映射，将具体路由映射到serice层完成业务逻辑操作。其中用到了Result这个工具类。

**utils**中的**Result.java**这个类是一个模板类，相当于一个工具，使得不论想要返回什么数据类型给前端都行

**config**中的**全局跨域配置类`GlobalCorsConfig.java`** 就是为了解决跨域访问的问题，为前后端分离开发做铺垫。

参考原文链接：[快速上手Springboot项目（登录注册保姆级教程）_springboot登录注册功能-CSDN博客](https://blog.csdn.net/weixin_44043758/article/details/118367899)

