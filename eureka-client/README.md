# eureka client启动关键点

1、服务器要启动，不然连不上

**注：** yml中的地址和浏览器中的地址不同，要小心

2、添加pom文件,也可以使用`spring-cloud-starter-netflix-eureka-server`

```
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
    </dependency>
```

3、main启用函数上添加注解@EnableEurekaClient
