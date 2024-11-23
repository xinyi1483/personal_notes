# 第一章 前期准备

**在线文档网址**

- 官网主页：https://spring.io/projects/spring-cloud
- 版本查看：https://start.spring.io/actuator/info



## 1.前期准备

### 1.1 确定 SpringCloud 和 SpringBoot 版本

- [SpringCloud 版本查看](https://start.spring.io/actuator/info)，查看 SpringBoot和 SpringCloud 的版本对应



### 1.2 依据 SpringBoot 版本确定 JDK 版本

![20240428222724](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/202404282233304.png)



![20240428223127](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/202404282233305.png)



![20240428223236](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/202404282233306.png)





## 2. 新建项目

![image-20240428235758016](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/202404290002432.png)

![image-20240429000035659](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/202404290002433.png)



### 2.1 父项目 pom

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>cn.xinyi1483</groupId>
    <artifactId>music</artifactId>
    <version>1.0-SNAPSHOT</version>

    <!-- 打包方式 -->
    <packaging>pom</packaging>
    <modules>
        <module>cloud-api-commons</module>
        <module>cloud-system</module>
    </modules>

    <properties>
        <maven.compiler.source>21</maven.compiler.source>
        <maven.compiler.target>21</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <springBoot.version>3.2.5</springBoot.version>
        <springCloud.version>2023.0.1</springCloud.version>
        <springCloudAlibaba.version>2023.0.1.0</springCloudAlibaba.version>
        <mysql.version>8.0.33</mysql.version>
        <mybatis.spring.boot.version>3.0.3</mybatis.spring.boot.version>
        <log4j2.version>3.2.5</log4j2.version>
        <cloud.api.commons.version>1.0-SNAPSHOT</cloud.api.commons.version>
    </properties>

    <!-- 锁定版本 -->
    <dependencyManagement>
        <dependencies>
            <!-- spring boot 2.2.2 -->
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>${springBoot.version}</version>
                <type>pom</type>
                <scope>import</scope>
                <exclusions><!-- 去掉springboot默认配置 -->
                    <exclusion>
                        <groupId>org.springframework.boot</groupId>
                        <artifactId>spring-boot-starter-logging</artifactId>
                    </exclusion>
                </exclusions>
            </dependency>

            <!-- spring cloud -->
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>${springCloud.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <!-- spring cloud 阿里巴巴 -->
            <dependency>
                <groupId>com.alibaba.cloud</groupId>
                <artifactId>spring-cloud-alibaba-dependencies</artifactId>
                <version>${springCloudAlibaba.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>

            <!-- mysql -->
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>${mysql.version}</version>
                <scope>runtime</scope>
            </dependency>

            <!-- mybatis -->
            <dependency>
                <groupId>org.mybatis.spring.boot</groupId>
                <artifactId>mybatis-spring-boot-starter</artifactId>
                <version>${mybatis.spring.boot.version}</version>
            </dependency>

            <!--log4j2-->
            <dependency> <!-- 引入log4j2依赖 -->
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-log4j2</artifactId>
                <version>${log4j2.version}</version>
            </dependency>

            <!--导入公共部分实体类cloud-api-commons-->
            <dependency>
                <groupId>cn.xinyi1483</groupId>
                <artifactId>cloud-api-commons</artifactId>
                <version>${cloud.api.commons.version}</version>
            </dependency>

        </dependencies>
    </dependencyManagement>

</project>
```



### 2.2 yaml 配置文件

```yaml
server:
  port: 8001

spring:
  application:
    name: cloud-system
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://192.168.110.23:3306/music?serverTimezone=Asia/Shanghai&useUnicode=true&characterEncoding=utf8&useSSL=false
    username: xinyi1483
    password: xinyi1483
    hikari:
      connection-timeout: 10000
      validation-timeout: 3000
      idle-timeout: 60000
      login-timeout: 5
      max-lifetime: 60000
      maximum-pool-size: 10
      minimum-idle: 5
      read-only: false
mybatis:
  mapper-locations: classpath:mapper/*.xml
  type-aliases-package: cn.xinyi1483.music.po  # 所有 po 所在包
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl

#日志配置 无特殊需求无需更改
logging:
  config: classpath:log4j2.xml

```



#### 2.2.1 spring 禁用 bootstrap 配置文件

在 springboot 2.5 之后的版本，官方禁用了 bootst 配置文件，可以通过下面两种方法进行处理

1.配置 `spring.configimport` 

```yaml
server:
  port: 8001

spring:
  application:
    name: system
  profiles:
    active: dev
  config:
    import:
      - optional:nacos:${spring.application.name}-${spring.profiles.active}.${spring.cloud.nacos.config.file-extension}
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://192.168.110.82:3307/shubao?serverTimezone=Asia/Shanghai&useUnicode=true&characterEncoding=utf8&useSSL=false
    username: shubao
    password: xinyi1483
    hikari:
      connection-timeout: 10000
      validation-timeout: 3000
      idle-timeout: 60000
      login-timeout: 5
      max-lifetime: 60000
      maximum-pool-size: 10
      minimum-idle: 5
      read-only: false
  # nacos 注册中心配置
  cloud:
    nacos:
      discovery:
        enabled: true
        # 服务注册地址
        server-addr: 192.168.110.82:8848
        namespace: efba2a57-9104-4ccf-8165-2ae9dfbbe6d4
      config:
        enabled: true
        server-addr: 192.168.110.82:8848
        # 命名空间
        namespace: efba2a57-9104-4ccf-8165-2ae9dfbbe6d4
        # 分组
        group: shubao
        file-extension: yaml
        prefix: ${spring.application.name}

mybatis:
  mapper-locations: classpath:mapper/*.xml
  type-aliases-package: cn.xinyi1483.shubao.entity  # 所有 po 所在包
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl

#日志配置 无特殊需求无需更改
logging:
  config: classpath:log4j2-dev.xml

```



2.重新引入 bootstrap 依赖

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-bootstrap</artifactId>
</dependency>
```

