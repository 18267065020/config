# config


## java配置

java jdk下载官网：[java jdk](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

系统变量->JAVA_HOME C:\Program Files\Java\jdk-10

Path变量 最后添加 %JAVA_HOME%\bin;   %JAVA_HOME%\jre\bin;

## maven

maven目录 conf/settings.xml

maven 系统配置 M2_HOME D:\java\apache-maven-3.3.9

Path变量 最后添加 %M2_HOME%\bin

设定本地maven仓库
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

