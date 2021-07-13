面试总结
 Posted on 2021-07-12
面试总结
中科软（郑州）7.10 am
说一下JAVA中的异常
在JAVA中的异常分为两大类一类叫做error，一类叫做exception（意外情况）。他们两个有一个顶级的父类（超类）叫做Throwable。

error指的是在通常情况下，不希望被程序捕获的异常。常常用于由于系统显示或者是系统本身出现错误而导致的异常。比如堆栈错误。

exception指的是通常情况下，用户程序可能出现的异常。

exception又分为两类一类是RunTimeException和非运行时异常；比如空指针异常是一种常见的运行时异常；ClassNotFound就属于常见的非运行时异常。

运行时异常（Unchecked Exception）是可以提前检查也可以不检查的异常，换句话说，这种问题一般是逻辑问题，可以通过逻辑来补救。

异常名称	说明
NullPointException	空指针异常
ClassCastException	类型转换异常
ArithmeticException	算数运算异常
IndexOutOfBoundsException	数组下标越界异常
NumberFormatException	数据格式异常
非运行时异常（Checked Exception）是必须要提前检查的异常，是一种如果不检查程序就无法通过编译的异常是除了RunTimeException以外的Exception异常，包括自定义异常。

异常名称	说明
IOException	IO异常
ClassNotFindException	类找不到异常
NoSuchMethodException	指定方法不存在
NoSuchFieldException	指定字段不存在
InstantiationException	实例化异常
说一下你对JAVA中集合的理解
集合中主要分为三类，一类是Collection做超类的集合，一类是Map做超类的键值对，一类是Iterator做工具类的迭代器。

Collection下又分为两大类：List和Set集合

List是按照插入顺序且允许值重复，可以为空的集合（索引从0开始）。Set是不按照插入顺序且不允许重复可以有一个空值的集合。

List下边又分为三大类:

ArrayList,底层维护一个数组，主要是查询修改快，删除增加慢（需要重新定义长度）。

LinkedList底层维护一个双向链表（可以用作队列）主要是删除增加快，查询修改慢（指针不好查找）。

Vector底层也是维护了一个数组，是矢量队列，相较于ArrayList它的线程安全（方法全部加了synchronized关键字，并且实现了序列化）。

Vector中还有一个继承了他的类叫Stack，叫做栈，相对于队列的先进先出，栈可以做到先进后出。

Set分为两大类：

HashSet:基于HashMap实现；LinkedHashSet默认按照插入顺序来

TreeSet:基于TreeMap实现

Map本身不按照插入顺序输出分为三大类：

HashMap:键值对的方式存储的，但不能保证次序，单线程；有一个继承他的叫做LinkedHashMap的可以用作缓存。

HashTable:键值对的方式存储的，但不能保证次序，支持多线程；

TreeMap:键值对的方式存储的，有排序，基于红黑树排序，默认升序；

JAVA中的IO流
流其实就是一个有起点和终点，有顺序的字节集合。

文件的IO流分为字节流（8字节）和字符流（16字节）；

字节流可以读取很多类型的文件（文本文件，媒体文件等），字符流仅仅能用来读取文本文件。

常用的字符流：

BufferReader;//read()读到末尾返回-1 readLine一次读一行
BufferWriter;//write()写
常用的字节流：

InputStream f1 = FileInputStream("文件地址");
int length=0;
byte[] c=new byte[1024];
while((length=f1.read(c,0,length)!=-1){
    System.out.println();
}
      
OutputStream f2 = FileOutputStream("文件地址");
      for(byte b : c){
          f2.write(b);
      }
Spring如何整合Mybatis
引入数据库jar和C3P0连接池jar包

引入Spring的jar包以及配置文件

引入MyBatis的jar包以及配置文件

修改config配置文件实现数据库管理和事务管理

常用的SpringBoot注解
引入数据库jar和C3P0连接池jar包

引入Spring的jar包以及配置文件

引入MyBatis的jar包以及配置文件

在全局配置文件中进行数据库连接配置（驱动，URL，用户名，密码）

序列化和反序列化
序列化的实现：

实现Sericalizable,写一个SericalizableUID;

实现Externalnalizable接口，在类中实现readExternal(ObjectInput in)和writeExternal(ObjectOutput out)方法.

序列化的优势：

对象随着程序的运行而被创建，然后在不可达时被回收，生命周期是短暂的。但是如果我们想长久地把对象的内容保存起来怎么办呢？把它转化为字节序列保存在存储介质上即可。那就需要序列化。

所有可在网络上传输的对象都必须是可序列化的，比如RMI（remote method invoke,即远程方法调用），传入的参数或返回的对象都是可序列化的，否则会出错；所有需要保存到磁盘的java对象都必须是可序列化的。通常建议：程序创建的每个JavaBean类都实现Serializeable接口

进程间传递对象，Android是基于Linux系统，不同进程之间的java对象是无法传输，所以我们此处要对对象进行序列化，从而实现对象在 应用程序进程 和 ActivityManagerService进程 之间传输。

序列化漏洞：

攻击者能够将恶意数据序列化并存储到数据库或内存中，当应用进行反序列化时，应用会执行到恶意代码。

解决：

对数据进行完整性检查；在创建对象之前强制执行严格的类型约束；

子查询
比如我要查询业绩排名第一的部门的员工都有谁：

select 员工 from 员工表 where 部门名称=(select top(部门名称) from 部门表 order by 业绩 desc)
连接查询
左连接：以左为主；

右连接：以右为主；

内连接：以都有的为主；

外连接：所有的都有，没有的用null代替

亚信科技（郑州）7.11 am
说一下你项目的优点
拦截器实现时段试卷

通过实现HandlerInterceptor接口中的preHandler方法默认参数（HttpServletRequest,httpServletResponse,handler）获取Request参数

getRequestURL()方法获取请求参数，同时进行判断在时间段内返回true,不在抛出异常

shiro框架的使用

认证的实现，通过调用业务层方法获取前端传入的这个账户密码是否真实有效（账户是否存在，密码是否正确，账户是否被冻结）

授权的实现，通过调用业务层方法获取用户角色的授权信息，因为一个用户可能有多个角色，不同角色的权限可能重复，此处采用HashSet来存储授权信息。

@RequiresPermissions注解去实现授权。注意如果没有触发授权功能不会调用授权信息。

Spring中AOP
AOP是面向切面编程，它可以使程序员更关心于我们的主要业务，同时对于其他可能需要进行功能增强（日志，事务）。

AOP的实现有两种方式：组合与继承。

JDK代理通过反射来获取该类并且进行功能增强，优点是创建快，但是频繁的AOP可能会使用时比较慢，必须要有实现的接口。

CGLIB代理通过字节码增强来对该类进行继承，优点是频繁使用效率高，但是创建慢。

HashMap
HashMap采用数组加链表/红黑树的形式，当数组下标一样的话，数组下边加链表，当链表过长时（大于8）会转换为红黑树。

数组可以提供查询的速度而链表可以加快增加删除的速度。

线程不安全。

MySQL隔离级别
事务的基本要素：原子性，隔离性，一致性，持久性。

隔离级别	解释	脏读	不可重复读	幻读
read-uncommitted	读未提交	1	1	1
read-committed	读已提交(Oracle)		1	1
repeatable-read	可重复读（MySQL）			1
serializable	序列化			
读已提交
在写数据时锁住该行。

可重复读
类似与乐观锁。

@SpringBootApplication注解
类似于三个注解：

@SpringBootConfiguration //基本配置

@EnableAutoConfiguration //自动配置

@ComponentScan //包扫描

Windows下若依项目的部署
 Posted on 2021-07-12
若依项目的部署
下载地址
若依官网 http://ruoyi.vip/。

若依微服务官网地址 https://doc.ruoyi.vip/ruoyi-cloud/

微服务技术选型
后端技术栈
MyBatis、Spring、Spring Boot、Spring Cloud & Alibaba、Nacos、Sentinel

前端VUE技术栈
ES6、vue、vuex、vue-router、vue-cli、axios、element-ui

项目骨架
后端项目架构
com.ruoyi     
├── ruoyi-ui              // 前端框架 [80]
├── ruoyi-gateway         // 网关模块 [8080]
├── ruoyi-auth            // 认证中心 [9200]
├── ruoyi-api             // 接口模块
│       └── ruoyi-api-system                // 系统接口
├── ruoyi-common          // 通用模块
│       └── ruoyi-common-core               // 核心模块
│       └── ruoyi-common-datascope          // 权限范围
│       └── ruoyi-common-datasource         // 多数据源
│       └── ruoyi-common-log                 // 日志记录
│       └── ruoyi-common-redis               // 缓存服务
│       └── ruoyi-common-security            // 安全模块
│       └── ruoyi-common-swagger             // 系统接口
├── ruoyi-modules         // 业务模块
│       └── ruoyi-system                      // 系统模块 [9201]
│       └── ruoyi-gen                         // 代码生成 [9202]
│       └── ruoyi-job                         // 定时任务 [9203]
│       └── ruoyi-file                        // 文件服务 [9300]
├── ruoyi-visual          // 图形化管理模块
│       └── ruoyi-visual-monitor             // 监控中心 [9100]
├──pom.xml                // 公共依赖
前端项目骨架结构
├── build                      // 构建相关  
├── bin                        // 执行脚本
├── public                     // 公共文件
│   ├── favicon.ico           // favicon图标
│   └── index.html            // html模板
├── src                        // 源代码
│   ├── api                    // 所有请求
│   ├── assets                 // 主题字体等静态资源
│   ├── components             // 全局公用组件
│   ├── directive              // 全局指令
│   ├── layout                 // 布局
│   ├── router                 // 路由
│   ├── store                  // 全局 store管理
│   ├── utils                  // 全局公用方法
│   ├── views                  // view
│   ├── App.vue                // 入口页面
│   ├── main.js                // 入口 加载组件 初始化等
│   ├── permission.js          // 权限管理
│   └── settings.js            // 系统配置
├── .editorconfig              // 编码格式
├── .env.development           // 开发环境配置
├── .env.production            // 生产环境配置
├── .env.staging               // 测试环境配置
├── .eslintignore              // 忽略语法检查
├── .eslintrc.js               // eslint 配置项
├── .gitignore                 // git 忽略项
├── babel.config.js            // babel.config.js
├── package.json               // package.json
└── vue.config.js              // vue.config.js

环境准备
JDK
MySql
ry-config.sql ry-cloud.sql

两个sql数据库。

Node
Nacos
下载网站：https://github.com/alibaba/nacos/releases

第一次配置需注意：

/conf/application.properties
该文件夹下修改数据库(注意数据库名字ry-config)：

#*************** Config Module Related Configurations ***************#
### If use MySQL as datasource:
 spring.datasource.platform=mysql 

### Count of DB:
 db.num=1

### Connect URL of DB:
 db.url.0=jdbc:mysql://127.0.0.1:3306/ry-config?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true&useUnicode=true&useSSL=false&serverTimezone=UTC
 db.user.0=root
 db.password.0=root
服务启动：

/bin 目录下：

此命令为单机模式下的登陆非集群模式：

startup.cmd -m standalone
注意默认访问路径

http://localhost:8848/nacos/index.html
默认登录账户与密码：

账户：nacos
密码：nacos
进入配置列表：

nacos配置列表

将所有涉及到MySQL和Redis的地方，账户与密码均改为自己的账户密码。注意redis默认没有密码，网上教程很多就不说了。

Redis
官方网站：http://www.redis.cn/

windows下载地址：https://github.com/MicrosoftArchive/redis/releases

在其安装/解压目录下输入下面指令去安装Redis：

redis-server --service-install redis.windows.conf
启动服务指令：

redis-server --service-start
停止服务：

redis-server --service-stop
卸载服务:

redis-server --service-uninstall
链接测试Redis,默认端口6379

redis-cli -h 127.0.0.1 -p 6379
基于Idea打开项目后端
第一步：jdk,maven等配置一下（idea空项目搭建）

jdk

jdk

maven

maven

第二步：依次启动ruoyi-gateway，ruoyi-auth，ruoyi-modules下的ruoyi-system。

第二步:检测nacos的服务列表，如图所示：

打开项目前端
第一步：在命令行输入 npm run dev 启动运行前端服务

第二步：npm install 下载依赖

第三步：npm run dev 开启服务

打开项目
服务端口

Hello World
 Posted on 2021-07-11
Welcome to Hexo! This is your very first post. Check documentation for more info. If you get any problems when using Hexo, you can find the answer in troubleshooting or you can ask me on GitHub.

Quick Start
Create a new post
$ hexo new "My New Post"
More info: Writing

Run server
$ hexo server
More info: Server

Generate static files
$ hexo generate
More info: Generating

Deploy to remote sites
$ hexo deploy
