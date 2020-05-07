## Spring-MVC框架
---
![框架图1](http://note.youdao.com/yws/res/1983/WEBRESOURCE5a2694a7795c67a5f869091df09521ff)
![框架图2](http://note.youdao.com/yws/res/1985/WEBRESOURCE291dec2f0f4fe7c274fd8b6faf663347)
![框架图3](http://note.youdao.com/yws/res/1989/WEBRESOURCEe4266d60c9409d9a206bf73868a7c762)
## URL路由：@Contrller和@RequestMapping
###  @Controller
@Controller标注的类表示是一个处理HTTP请求的控制器(即MVC中的C)，该类中所有被@RequestMapping标注的方法都会用来处理对应URL的请求。 在Spring MVC框架中，使用@RequestMapping标注可以将URL与处理方法绑定起来，例如：

    @Controller
    public class IndexController {
        @RequestMapping("/")
        @ResponseBody
        public String index() {
        return "index";
        }
        @RequestMapping("/hello")
        @ResponseBody
        public String hello() {
        return "hello";
        }
    }
IndexController类被@Controller标注，其中的两个方法都被@RequestMapping标注，当应用程序运行后，在浏览器中访问http://localhost:8080/，请求会被Spring MVC框架分发到index()方法进行处理。同理，http://localhost:8080/hello会交给hello()方法进行处理。
### @ResponseBody
@ResponseBody标注表示处理函数直接将函数的返回值传回到浏览器端显示。 如果不使用@ResponseBody注解，则返回的是一个Path，则会将request重新分发到返回的path所对应的Controller，请大家自己试一试。
### @RequestMapping
**作用位置**<br>
1. 方法上面--->指定该方法处理的URL
2. 类上面--->指定该类处理的URL


    @Controller
    @RequestMapping("/blogs")
    public class AppController {
        @RequestMapping("/create")
        @ResponseBody
        public String create() {
            return "mapping url is /blogs/create";
        }
    }
###### tip:每一个类中都可以包含一个或多个@RequestMapping标注的方法;通常我们会将业务逻辑相近的URL（例如上例中的文章列表、创建文章）放在同一个Controller中进行处理。
### @RequestMapping的简写形式
在Web应用中常用的HTTP方法有四种:

    - PUT方法用来添加的资源
    - GET方法用来获取已有的资源
    - POST方法用来对资源进行状态转换
    - DELETE方法用来删除已有的资源
这四个方法可以对应到CRUD操作（Create、Read、Update和Delete），比如博客的创建操作，按照REST风格设计URL就应该使用PUT方法，读取博客使用GET方法，更新博客使用POST方法，删除博客使用DELETE方法。<br>
**每一个Web请求都是属于其中一种，在Spring MVC中如果不特殊指定的话，默认是GET请求。**<br>
比如@RequestMapping("/")和@RequestMapping("/hello")和对应的Web请求是：


    GET /
    GET /hello
实际上@RequestMapping("/")是@RequestMapping("/", method = RequestMethod.GET)的简写，即可以通过method属性，设置请求的HTTP方法。<br>
比如PUT /hello请求，对应于@RequestMapping("/hello", method = RequestMethod.PUT)<br>
Spring MVC提供了一种更加简洁的配置HTTP方法的方式，增加了四个标注：

    - @PutMapping
    - @GetMapping
    - @PostMapping
    - @DeleteMapping

基于新的标注@RequestMapping("/hello", method = RequestMethod.PUT)可以简写为@PutMapping("/hello")。@RequestMapping("/hello")与GetMapping("/hello")等价。
