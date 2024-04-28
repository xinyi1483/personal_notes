





# IDEA 插件推荐





## 1. Lombok（⭐⭐⭐）

只需要加上 @Data 注解就可以使用，不需要写 get、set、toString 方法



### 1.1 Delombok

因为 Lombok 对插件有强依赖，团队中一人装了，其他人不装代码无法运行，而 Delombok 就是用来解决这个问题的

- 保留 Lombok 的优点的同时，保证代码完整性
- 拜托对 Lombok 插件的依赖，不强迫队友安装插件



## 2. mybatis

### 2.1、mybatis 代码提示和代码检测（付费插件：⭐）

MyBatisCodeHelperPro：支持mapper互跳，方法自动生成，代码自动生成



### 2.2、mybatis 日志拼接 (⭐⭐)

MyBatis Log Plugin：可以将控制台打印的SQL拼接成直接可用的SQL



### 2.3 . mapper文件跳转 (⭐⭐⭐)

Free Mybatis plus

在dao层方法跳转到对应mapper文件中sql语句的映射







## 3. Maven

### 3.1 maven 依赖分析

Maven Helper：提供 pom 文件的包依赖分析和调试





## 4. AI 代码工具 

### 4.1. Codota（⭐）

代码智能提示插件



![20240427215720](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427215720.jpg)



### 4.2 aiXcoder

aiXcoder：一款国产代码开发工具，提供了比较强大的代码补全、预测的功能，它的宗旨就是让我们少些代码，能自动生成的绝不手写

![20240427215919](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427215919.webp)





### 4.3 Github Copilot

- 官网：https://github.com/features/copilot/
- 说明：Open AI 在 GPT-3 的基础上通过对 GitHub 的开源代码进行学习的, 得到了Codex模型



![20240427220248](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427220248.png)





### 4.4 CodeGeeX 【国产】

- 官网：https://www.codegeex.cn/
- 说明：CodeGeeX是一个具有130亿参数的多编程语言代码生成预训练模型





## 5. 翻译工具

### 5.1 Translation（⭐⭐⭐）

英文不好的人的福音，灰常牛逼

- 取变量名的时候可以直接快捷键翻译并替换 ctrl+shift+x
- 单词翻译 ctrl+shift+y









## 其他插件

### 1 . CodeGlance

代码迷你缩放图插件

![20240427220043](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427220043.png)



### 2. Material Theme UI

切换主题风格



### 3. Alibaba Cloud Toolkit

快速部署到服务器，超级牛逼



### 4. Json Parser

JSON 工具，用于验证和格式化 JSON 字符串的轻量级插件





### 5. JUnitGenerator

可自动生成测试代码







### 6. RESTfultoolkit

根据 URL 查找 controller 





### 9. 阿里巴巴代码规范检查插件（⭐）

​		阿里巴巴代码规范检查插件

Alibaba Java Coding Guidelines





### 10. 格式化代码插件

​	Save Actions 格式化代码插件，会自动给未修改的变量添加 final 修饰，变量添加this





### 11. 彩虹括号（⭐⭐）

Rainbow Brackets，彩虹括号插件





### 12. 单元测试(⭐⭐)

JUnitGenerator V2.0



### 14. 快捷键提示

Key promoter X：是 IDEA 的快捷键提示插件，这是我个人非常喜欢的一个功能，它让我快速的记忆了很多操作的快捷键。当你点击某个功能且该功能有快捷键时，会提示当前操作的快捷方式。



### 15. UI 界面

Material Theme UI：使用插件后界面图标样式都会变的很漂亮。































# IDEA设置



### 1、取消tab页单行显示

![20240427215948](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427215948.jpg)





### 2、创建代码模板

​	LiveTemplates

![20240427215805](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427215805.jpg)





### 3、自动导包

​		AutoImport：自动导包



<img src="https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427215442.jpg" alt="001-AutoImport" style="zoom:80%;" />







### 4、代码改变时，目录颜色跟着改变

​		VersionControl

![20240427215849](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427215849.jpg)









### 5、idea显示方法信息

settings->Editor->Code Completion->Show the documentation popup in 500 ms

![20240427220014](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427220014.jpg)









### 6、设置idea项目编码

file -> settings -> Editor -> File Encodings

![20240427220115](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427220115.png)







### 7、显示方法注释

![20240427220139](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427220139.png)







### 8、开启热部署

配置idea自动编译

![20240427220208](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427220208.png)



![20240427220228](https://cdn.jsdelivr.net/gh/xinyi1483/image@main/2024/20240427220228.png)



pom.xml 导入热部署的包（子模块里面导入）

```xml
<!-- 热部署 -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <scope>runtime</scope>
    <optional>true</optional>
</dependency>
```



pom.xml 导入热部署的插件（父项目里面配置）

```xaml
<build>
    <finalName>SpringCloud</finalName>
    <plugins>
        <!-- 热部署 -->
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <configuration>
                <fork>true</fork>
                <addResources>true</addResources>
            </configuration>
        </plugin>
    </plugins>
</build>
```





















