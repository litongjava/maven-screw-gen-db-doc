## maven-screw-gen-db-doc

### 简介

使用maven插件的方式生成数据库文档



### 使用

#### 修改配置

不同的数据库类型和不同的数据库版本,需要使用不同的配置

编辑pom.xml

修改build-->plugins-->plugin-->configuration 中的配置



#### 执行生成命令

需要安装maven或者mavend,下面以mvnd为例进行介绍

```
#进入工程目录
e:
cd E:\code\java\project-ppnt\maven-screw-gen-db-doc
#执行生成命令
mvnd screw:run
```

命令执行执行完成后会在doc目录下生成一个数据库文档的文件

### 配置

#### mysql

##### mysql 8

通常只需要修改jdbcUrl,username,password

```
<plugin>
  <groupId>cn.smallbun.screw</groupId>
  <artifactId>screw-maven-plugin</artifactId>
  <version>1.0.3</version>
  <dependencies>
    <!-- HikariCP -->
    <dependency>
      <groupId>com.zaxxer</groupId>
      <artifactId>HikariCP</artifactId>
      <version>3.4.5</version>
    </dependency>
    <!--mysql driver -->
    <dependency>
      <groupId>mysql</groupId>
      <artifactId>mysql-connector-java</artifactId>
      <version>8.0.20</version>
    </dependency>

    <dependency>
      <groupId>com.oracle.database.jdbc</groupId>
      <artifactId>ojdbc8</artifactId>
      <version>21.5.0.0</version>
    </dependency>
  </dependencies>
  <configuration>
    <!--driver -->
    <driverClassName>com.mysql.cj.jdbc.Driver</driverClassName>
    <!--jdbc url -->
    <jdbcUrl>jdbc:mysql://192.168.3.9:3306/test?serverTimezone=UTC</jdbcUrl>
    <!--username -->
    <username>root</username>
    <!--password -->
    <password>root</password>
    <!--生成文件类型,支持 WORD,HTML,MD-->
    <fileType>WORD</fileType>
    <!--打开文件输出目录 -->
    <openOutputDir>false</openOutputDir>
    <!--生成模板 -->
    <produceType>freemarker</produceType>
    <!--文档名称 为空时:将采用[数据库名称-描述-版本号]作为文档名称 -->
    <!--<docName>测试文档名称</docName> -->
    <!--描述 -->
    <description>数据库说明书</description>
    <!--版本 -->
    <version>1.0.0</version>
    <!--标题 -->
    <title>数据库说明书</title>
  </configuration>
</plugin>
```

#### oracle

##### oracle 12c

```
      <plugin>
        <groupId>cn.smallbun.screw</groupId>
        <artifactId>screw-maven-plugin</artifactId>
        <version>1.0.3</version>
        <dependencies>
          <!-- HikariCP -->
          <dependency>
            <groupId>com.zaxxer</groupId>
            <artifactId>HikariCP</artifactId>
            <version>3.4.5</version>
          </dependency>
          <!--mysql driver -->
          <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.20</version>
          </dependency>

          <dependency>
            <groupId>com.oracle.database.jdbc</groupId>
            <artifactId>ojdbc8</artifactId>
            <version>21.5.0.0</version>
          </dependency>
        </dependencies>
        <configuration>
          <!--driver -->
          <driverClassName>oracle.jdbc.driver.OracleDriver</driverClassName>
          <!--jdbc url -->
          <jdbcUrl>jdbc:oracle:thin:@192.168.3.9:1521/XE</jdbcUrl>
          <!--username -->
          <username>JGWNEW</username>
          <!--password -->
          <password>JGWNEW</password>
          <!--生成文件类型,支持 WORD,HTML,MD-->
          <fileType>HTML</fileType>
          <!--打开文件输出目录 -->
          <openOutputDir>false</openOutputDir>
          <!--生成模板 -->
          <produceType>freemarker</produceType>
          <!--文档名称 为空时:将采用[数据库名称-描述-版本号]作为文档名称 -->
          <!--<docName>测试文档名称</docName> -->
          <!--描述 -->
          <description>数据库说明书</description>
          <!--版本 -->
          <version>1.0.0</version>
          <!--标题 -->
          <title>数据库说明书</title>
        </configuration>
      </plugin>
```



