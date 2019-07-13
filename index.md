# 垂垂加油
## Springboot + Mybatis整合

* 第一步  创建Spring Initializr项目
1. File->New->Project(or Module)
2. 选择Spring Initializr，然后next，配置应该暂时不用管，继续next
3. 选择需要的依赖：Web->Web,SQL->MySQL,SQL->JDBC,SQL->Mybatis,下一步
4. 设置路径，就设置到当前的项目下就行了。
5. finish
* 第二步  搭建主要结构和配置文件（以book为例）
1. 在com.example包下面分别创建service、controller、entity和dao（mapper）包
2. entity下面定义book类
3. dao包下定义一个BookMapper的接口，在内部定义一个返回值为List<Book>的findAll方法，类上面加上@Repository注解
```
@Reposity
public interface BookMapper{
    List<Book> findAll();   //方法就是这一句
}
```
4. service包下面创建一个BookService接口，写一个同上的方法。再在包下创建一个impl包，在里面定义一个BookServiceImpl类，实现BookService接口，使用@Service注解，里面用@Autowried引入一个BookMapper对象，重写接口的方法，方法内部用bookMapper调用findAll方法

```
@Service
public class BookServiceImpl implements BookService {

    @Autowired
    private BookMapper bookMapper;

    @Override
    public List<Book> findAll() {
        return bookMapper.findAll();
    }
}
```
5. 在controller定义一个BookController类，在里面定义一个BookController类，使用@RestController注解，里面用@Autowried引入一个BookService对象，定义一个方法，里面使用bookService调用findAll
注意controller这里面，有一个注解是@RequestMapping，里面的参数就是到时候网址需要访问的地址，如果在类上面设置了，则该类里面所有方法都要在这个地址后面，如类上注解了("/book"),方法上面注解了("/list")，网址就需要/book/list才可以访问这个方法

```
@RestController
@RequestMapping("/book")
public class BookController {

    @Autowired
    private BookService bookService;

    @RequestMapping("/list")
    public List<Book> findAll(){
        List<Book> books = bookService.findAll();
        return books;
    }
}
```
6. 配置文件
删除application.properties,创建application.yml和application-dev.yml
appliction.yml
    
```
spring:
  profiles:
    active: dev
```
application-dev.yml

```
server:
  port: 8080

spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/bookman
    username: root
    password: msldxy

mybatis:
  mapper-locations: classpath:com/example/mapping/*Mapper.xml
  type-aliases-package: com.example.entity

#showSql
logging:
  level:
    com:
      example:
        mapper : debug
```
其中datasource下面的几个参数是自己数据库的参数，可以根据之前的jdbc的几个参数填过来。

在resources目录下创建文件夹com/example/dao,再在这下面创建文件BookMapper.xml
```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.example.dao.BookMapper">

    <select id="findAll" resultType="com.example.entity.Book">
        select * from book
    </select>

</mapper>
```
7. 在DemoApplication的主类上面加上@MapperScan("com.example.dao")注解
8. 运行DemoAplication
9. 打开浏览器，访问localhost:8080/book/list


## 闲谈
一般创建项目，java下面都是创建一个包，通常情况下都是域名反着，比如如果百度公司的，就用com.baidu。当然了，我自己用的的com.msldxy(说不定以后还真会有呢#{手动狗头})
然后再在这个包下面创建各个包，有
* entity(domain)主要用于封装实体
* dao(mapper)   dao层即持久层，主要用于对数据库的操作
* service       service业务层，主要用于处理业务逻辑等
* controller    控制层(其实我也不知道叫啥hhhhh随便叫的)，这个层主要用于和前端的交互

以上的几个组件，前端访问会通过controller，调用service的方法，而service处理业务逻辑，再将需要进行数据库操作的方法来调用dao的方法，dao层只有接口，相应的方法在resources下面对应的*Mapper.xml映射文件中，映射文件中，mapper的属性namespace是对应Mapper类的路径。里面有select、update等与数据库对应操作的标签,注意标签的id一定要和Mapper中对应的方法名一致，标签内就是数据库的语句了


### emmmmm大概先说这么多吧，将就着看一看，如果有什么不懂的就问，希望你能不被淘汰鸭
