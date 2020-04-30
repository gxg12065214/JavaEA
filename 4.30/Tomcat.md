### JavaWeb概念
    Java web，是用java技术来解决相关web互联网领域的技术的总称。web包括：web服务器和web客户端两部分。
    java在最早web客户端的应用有java applet程序，不过这种技术在很久之前就已经被淘汰了。java在服务器端的应用非常丰富，
    比如Servlet，jsp和第三方框架等等。java技术对web领域的发展注入了强大的动力
    简单的说，就是使用java语言实现浏览器可以访问的程序内容。称之为Java Web。

javaweb开发是基于请求和响应的：

    请求 ：浏览器（客户端）向服务器发送信息
    响应 ：服务器向（客户端）浏览器回送信息
请求和响应是成对出现的。
    ![请求和响应.png](http://note.youdao.com/yws/res/592/WEBRESOURCEb0468c848b2a445f722edcf4c56324ae)
### Web资源的分类
    所谓web资源即放在Internet网上供外界访问的文件或程序，又根据它们呈现的效果及原理不同，将它们划分为静态资源和动态资源。
    静态web资源：固定不变数据文件（静态网页 HTML、CSS文件、文本、音频、视频）
    静态web技术：HTML+CSS+JavaScript
    动态web资源：一段服务程序，运行后，生成的数据文件
    动态web技术：servlet，jsp，php， .net,ruby、python等等
### 常见的Web服务器
web服务器简介：
    
    Tomcat：由Apache组织提供的一种Web服务器，提供对jsp和Servlet的支持。它是一种轻量级的javaWeb容器（服务器），也是当前应用最广的JavaWeb服务器（免费）。
    Jboss：是一个遵从JavaEE规范的、开放源代码的、纯Java的EJB服务器，它支持所有的JavaEE规范（免费）。
    GlassFish： 由Oracle公司开发的一款JavaWeb服务器，是一款强健的商业服务器，达到产品级质量（应用很少，收费）。
    Resin：是CAUCHO公司的产品，是一个非常流行的应用服务器，对servlet和JSP提供了良好的支持，性能也比较优良，resin自身采用JAVA语言开发（收费，应用比较多）。
    WebLogic：是Oracle公司的产品，是目前应用最广泛的Web服务器，支持JavaEE规范，而且不断的完善以适应新的开发要求，适合大型项目（收费，用的不多，适合大公司）。


### Tomcat介绍
    Tomcat是常见的免费且开源的web服务器。其只要用于中小型项目，只支持Servlet和JSP等少量JavaEE规范（Java web编程接口）。Tomcat这个名字的来历，Tomcat是一种野外的猫科动物，不依赖人类，独立生活。 Tomcat的作者，取这个名字的初衷是希望，这一款服务器可以自力更生，自给自足，像Tomcat这样一种野生动物一般，不依赖其他插件，而可以独立达到提供web 服务的效果。
#### 不使用Tomcat访问html
    不使用tomcat也可以打开html页面，但是可以在浏览器的地址里看到 file:d:/test.html 这样的格式，是通过打开本地文件的形式打开的
    但是我们平时上网看到的html网址一般都是: 
    http://12306.com/index.html 这样的形式。
    这是因为有web服务器的存在
    ![url.png](http://note.youdao.com/yws/res/563/WEBRESOURCEc07aa6f986ff7a6e47c1dc39969d793a)
#### Tomcat的使用
##### 1. 安装
找到你需要用的Tomcat版本对应的zip压缩包，解压到需要安装的目录即可。
##### 2.目录介绍
bin：专门存放tomcat服务器的可执行程序<br>
conf：专门存放tomcat服务器的配置文件<br>
lib：专门存放tomcat服务器的jar包<br>
logs：专门存放tomcat服务器运行时的日志信息<br>
temp:专门存放tomcat运行时产生的临时数据<br>
webapps:专门存放部署的web工程<br>
work：是tomcat工作时的目录，用来存放tomcat运行时jsp翻译为servlet的源码，和session钝化的目录。
##### 3.如何启动和关闭Tomcat服务器
###### windows系统下：
1. 打开Tomcat服务器的第一种方式：找到Tomcat目录下的bin目录下的startup.bat文件，双击，就可以启动Tomcat服务器.
2. 打开Tomcat服务器的第二种方式：打开命令行，cd到Tomcat的bin目录下，敲入命令 catalina run
3. 关闭Tomcat服务器的第一种方式：点击Tomcat服务器的关闭按钮
4. 关闭Tomcat服务器的第二种方式：找到Tomcat的bin目录下双击shutdown.bat文件就可以停止（主要的方式）
###### Macos下：（命令行的方式）
1. 确定好安装jdk
2. 确定好安装tomcat
3. 打开mac终端,切换到tomcat bin目录下
4. 命令：cd apache-tomcat-7.0.88， cd bin
5. 打开tomcat服务器命令：sudo sh startup.sh
6. 关闭tomcat服务器命令：sh ./shutdown.sh

那么如何测试Tomcat服务器是否启动成功？
打开浏览器，在地址栏输入以下地址进行测试：
1. http://localhost:8080
2. http://127.0.0.1:8080
3. http://真实ip:8080
##### 4.常见的启动失败的情况：
双击startup.bat文件，会出现一个小窗口一闪而过。这个失败的原因基本是没有配置好JAVA_HOME环境变量。JAVA_HOME配置的路径只需要配置到jdk的安装目录即可。不需要带上bin目录。
##### 5.如何修改Tomcat的端口号？
mysql默认的端口号为：3306<br>
Tomcat默认的端口号为：8080    
找到Tomcat目录下的conf目录，找到server.xml配置文件。
找到Connector标签，修改port属性为你需要的端口号。端口号的范围：1-65535
修改完端口号，一定要重启Tomcat服务器才能生效。<br>
HTTP协议默认的端口号为：80

##### 6.如何把web工程部署到Tomcat中?
第一种方法：只需要把web工程的目录拷贝到tomcat的web
apps目录下即可。
如何访问Tomcat下的web工程？
只需要在浏览器中输入访问地址，格式如下：
- http：//ip：port/工程名/目录下/文件名
---
第二种方法：找到Tomcat下的conf目录\Catalina\localhost\,创建如下的配置文件：

    <!-- Context表示一个工程的上下文
        path表示工程的访问路径：/abc
        docBase表示你的工程目录在哪里
    -->
    <Context path="/web03" docBase="E:\book"/>
##### 7.手拖html文件到浏览器和在浏览器输入地址访问有何区别？
手拖动html页面到浏览器，这个时候浏览器中的地址如下：
file:///E:/book/index.html
它使用的是file://协议。file协议表示告诉浏览器直接读取file：协议后面的路径，解析在浏览器即可。<br>
如果是在浏览器地址栏中输入访问地址格式如下：http://ip:port/工程名/资源名，如：http:localhost:8080/book/index.html
- http: 表示协议
- localhost是IP地址
- :8080是端口号
- /book是工程名
- /index.html是哪个文件

客户端把请求发送给服务器（Tomcat），服务器收到请求之后，读取你要访问的资源文件，然后回传给客户端要的页面内容。客户端得到index.html页面内容，解析展示在浏览器上。
##### 8.ROOT工程的访问，以及默认index.html页面的访问
- 当我们在浏览器地址栏中输入如下地址时：http://ip:port/ ,即没有工程名的时候，默认访问的是ROOT工程
- 当我们在浏览器地址栏中输入如下地址时：http://ip:port/工程名/，即没有资源名的时候，默认访问index.html页面。
---
---
### IDEA整合Tomcat服务器
##### 步骤如下：File>Setting>Build,Execution,Deployment>Application Servers,然后配置Tomcat的安装目录，最后点击Apply，OK。
### IDEA中动态web工程的操作
##### IDEA中如何创建动态web工程（先有工程，才有模块）
1. 创建一个新模块：new>Module
2. Java Enterprise>Web Application(4.0)，然后Next。
3. 输入你的模块名，点击Finish，即可完成创建。