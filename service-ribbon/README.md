# ribbon关键点

1、引入pom包

```
    <dependency>                                                            
        <groupId>org.springframework.cloud</groupId>                        
        <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId> 
    </dependency>                                                           
    <dependency>                                                            
        <groupId>org.springframework.boot</groupId>                         
        <artifactId>spring-boot-starter-web</artifactId>                    
    </dependency>                                                           
    <dependency>                                                            
        <groupId>org.springframework.cloud</groupId>                        
        <artifactId>spring-cloud-starter-ribbon</artifactId>                
    </dependency>                                                                                                                   
```

2、man启动函数上添加注解@EnableEurekaClient和@EnableDiscoveryClient

3、新建注入

```
    @Bean@LoadBalanced
    RestTemplate restTemplate(){
        return  new RestTemplate();
    }
```

4、配置yml属性

```
    eureka:
      client:
        service-url:
          defaultZone: http://localhost:8765/eureka/
    
    server:
      port: 8764
    
    spring:
      application:
        name: service-ribbon
```

# 断路器关键点

1、在ribbon基础上添加依赖包

```
    <dependency>                                                     
        <groupId>org.springframework.cloud</groupId>                 
        <artifactId>spring-cloud-starter-netflix-hystrix</artifactId>
    </dependency>                                                    
```

2、main启动函数上添加@EnableHystrix注解

3、添加@HystrixCommand注解创建熔断器功能，新加两处，一个注解，一个注解的回调函数

```
    @HystrixCommand(fallbackMethod = "hiError")
```
```
    public String hiError(String name){
            return "hi, "+ name+", sorry, error!";
        }
```

此时启动程序，当服务中断时会自动调用回调方法，开启多个客户端后停用做效果对比（负载后是交替请求，中断服务后该请求报404，然后地址会被移除）


