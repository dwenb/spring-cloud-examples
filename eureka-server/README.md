# eureka server关键点

1、添加pom文件，网上教程只需引入下面一个包，但是本人以sdkman切换版本，实际测试jdk7、8、9、11均需引入第二步的包

```
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
    </dependency>
```

2、在main启动函数上添加注解`@EnableEurekaServer`

2、如果报错`java.lang.TypeNotPresentException: Type javax.xml.bind.JAXBContext not present`手动引入下列包

```
  <dependency>
        <groupId>javax.xml.bind</groupId>
        <artifactId>jaxb-api</artifactId>
        </dependency>
    <dependency>
        <groupId>org.glassfish.jaxb</groupId>
        <artifactId>jaxb-runtime</artifactId>
    </dependency>
```