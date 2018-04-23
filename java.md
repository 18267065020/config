# config


## java配置

java jdk下载官网：[java jdk](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

系统变量->JAVA_HOME C:\Program Files\Java\jdk-10

Path变量 最后添加 %JAVA_HOME%\bin;   %JAVA_HOME%\jre\bin;

测试安装配置是否成功 java -version

## maven

maven 下载官网地址:[maven](https://maven.apache.org/download.cgi)

maven 系统变量配置 M2_HOME D:\java\apache-maven-3.3.9

Path变量 最后添加 %M2_HOME%\bin

测试安装配置是否成功 mvn -version

maven目录 conf/settings.xml 设定本地maven仓库
``<localRepository>D:\java\apache-maven-3.3.9\repo</localRepository>``

阿里云线上仓库

    <mirrors>
    <mirror>
    <id>alimaven</id>
    <name>aliyun maven</name>
    <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
    <mirrorOf>central</mirrorOf>
    </mirror>
    </mirrors>


## spring boot

pom.xml配置

注：parent中的版本号是spring boot的版本号，需要不同版本的spring boot更换版本号

    <parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>1.5.9.RELEASE</version>
    </parent>

      <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
      </dependency>

      <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
      </dependency>

