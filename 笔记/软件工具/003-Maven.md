



## 手动下载jar包，导入到maven仓库

```bash
mvn install:install-file 
-Dfile={$jar包地址}
-DgroupId={$jar包的groupid}
-DartifactId={$jar包的依赖}
-Dversion={$版本号}
-Dpackaging=jar

# 示例
mvn install:install-file -Dfile=C:\Users\MI\Desktop\spring-cloud-starter-netflix-hystrix-2.2.9.RELEASE.jar -DgroupId=org.springframework.cloud -DartifactId=spring-cloud-starter-netflix-hystrix -Dversion=2.2.9.RELEASE -Dpackaging=jar

```

