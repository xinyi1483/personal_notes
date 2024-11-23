

## 1、总父工程



```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>bigdata</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>

        <!-- Java 版本号 -->
        <java.version>8</java.version>

        <!--设置Maven的Java的版本，或者使用不同的 JDK 版本编译-->
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
        <encoding>UTF-8</encoding>
    </properties>

    <!--父工程：pom-->
    <packaging>pom</packaging>

    <!--
        dependencyManagement：写在这里面的坐标，字母块不会直接引入，子模块只是不用写版本号
        dependencies：写在这里面的坐标，直接给所有子模块引入，子模块不用写任何东西
    -->
    <dependencyManagement>
        <dependencies>

        </dependencies>
    </dependencyManagement>


    <dependencies>

    </dependencies>

</project>

```





# 疑难解答



## 1.手动导入jar包到maven

1. 下载 jar 包到桌面
2. 在下载的 jar 包所在位置打开 cmd
3. 在 cmd 窗口运行下面的命令

```shell
# -DgroupId: maven 坐标里的 groupId
# -DartifactId: maven 坐标里的 artifactId
# -Dversion: maven 里的 version
# -Dfile: jar 包名称
mvn install:install-file -DgroupId=cn.dev33 -DartifactId=sa-token-spring-boot-starter -Dversion=1.34.0 -Dpackaging=jar -Dfile=sa-token-spring-boot-starter-1.34.0.jar
```















