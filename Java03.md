# Java大厂面试题03

### 1.锁可以锁哪里？

​	Java中为程序加锁的方式主要有两种：synchronized 与 Lock。

1. synchronized 可以修饰的作用域为：
   - 非静态方法 （加的锁为对象锁）；
   - 静态方法 （加的锁为类锁）；
   - 代码块 （对象锁与类锁都可以）；
2. Lock采用lock()对代码进行加锁，unlock()进行解锁

​		[参考资料](https://blog.csdn.net/yx0628/article/details/79086511)

### 2.怎末利用反射获取类中的对象？

1. 获取Class对象
2. 通过Class对象获取构造方法
3. 通过构造方法调用newInstance()方法创建实例

​		[参考资料](https://baijiahao.baidu.com/s?id=1619748187138646880&wfr=spider&for=pc)

### 3.说说你常用的Linux基本操作命令

- ls	用来显示目标列表
- cd    用来切换目录
- pwd    显示当前目录（绝对路径）
- cat    查看文件内容
- grep    文本搜索工具，使用的是正则表达式，打印匹配的行
- tail    输出文件尾部内容
- ps     当前系统的进程状态（docker ps）
- kill    删除执行中的程序或工作
- top    查看系统运行情况

### 4.Maven中package和install区别

package是把jar打到本项目的target下，而install是把target下的jar安装到本地仓库，供其他项目使用

### 5.谈谈简单工厂和抽象工厂的区别

- 简单工厂模式：是由一个工厂对象创建产品实例，简单工厂模式的工厂类一般使用静态方法，通过不同的参数的不同实例对象可以生产结构中的任意产品，不能增加新的产品。
- 抽象工厂模式：提供一个创建一系列相关或相互依赖对象的接口，而无需定制具体的类，生产多个系列产品生产不同产品族的全部产品，不能新增产品，可以新增产品族。

​		[参考资料](https://www.cnblogs.com/gclokok/p/10029088.html)

### 6.说说Aop和IOC的应用

​	IOC的主要应用场景体现在BeanFactory接口，BeanFactory下面有具体的实现类来实现IOC的功能

​	AOP的主要应用场景：日志、权限、事物等。

### 7.Spring中的bean是线程安全的吗？

​	Spring容器中的Bean本身不具备线程安全的特性，但还是要结合具体scope的Bean去研究

1. Spring容器中Bean默认是单例的，所有线程都共享一个单实例的Bean，因此会存在资源的竞争。如果单例Bean，是一个无状态Bean，也就是线程中的操作不会对Bean的成员执行查询以外的操作，那么这个单例Bean是线程安全的。比如Spring mvc 的Controller、Service、Dao等，这些Bean大多是无状态的，只关注于方法本身。对于有状态的Bean，是线程不安全的，但是我们可以通过ThreadLocal去解决线程安全的方法。
2. 对于原型Bean（即scope = "prototype"），每次创建一个新对象，也就是线程之间不存在Bean共享，自然也就不会有线程安全的问题。

​		[参考资料](https://blog.csdn.net/qq_29645505/article/details/88432001)







