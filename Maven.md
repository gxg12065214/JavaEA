## Maven介绍
### 什么是maven？
 maven是专门用来构建和管理Java相关项目的工具。
### Maven的用处：
##### 1. 使用maven管理的Java项目都有相同的结构
    1.1 有一个pom.xml用于维护当前项目都用了那些jar包
    1.2 所有的Java代码都放在src/main/java下面
    1.3 所有的测试代码都放在src/test/java下面
![909a013db5f60effca04e145c2d93d88.png](http://note.youdao.com/yws/res/422/WEBRESOURCE5fb360552098d6efcf3efa06f8447bb7)
##### 2.可以统一维护jar包
    比如说有几个Java项目，这些项目都不是maven风格。那么这几个项目就会各自维护各自的jar包。但是其中有一些jar包是相同的。而maven风格的项目，首先把所有的jar包都放在“仓库”里，然后哪个项目需要用到这个jar包，只需要给出jar包的名称和版本号就行了。这样jar包就实现了共享。
## Maven的下载与配置
    官网的下载地址为：http://maven.apahe.org/download.cgi


## Maven仓库
    所谓的仓库就是用于存放项目需要的jar包。
maven采用一个仓库，多个项目的方式，让多个项目共享一个仓库里的jar包。
### 使用阿里云下载路径
---
**修改在mirrors下新加一个阿里云的镜像地址：**<br>
修改位置为第160-165行：

    <mirror>
        <id>alimaven</id>
        <mirrorOf>central</mirrorOf>
        <name>aliyun maven</name>
        <url>http://maven.aliyun.com/nexus/content/repositories/central/</url>
    </mirror>
## Maven风格的Java项目
maven作为一种工具，可以创建标准化的Maven风格Java项目。但在实际工作中，几乎很少有机会直接通过Maven命令行来创建Java项目，通常都是在IDEA中，通过集成maven的方式来创建Java项目。