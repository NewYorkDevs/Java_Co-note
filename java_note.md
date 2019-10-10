- String 和 StringBuffer 区别

String每次赋值会重新内存中开一个字符串，让指向新对象。

StringBuffer永远在旧的上面修改

- StringBuffer是线程安全

​    StringBuilder不是线程安全，不能同步访问

- dataType[] arr; 建议这么写
- arr = new dataType[size];
- str.toUpperCase(); 这个方法不改变str，返回值变大写
- 克隆会产生多个对象的拷贝，类克隆一定要实现Cloneable接口
- str1==str2 是在判断两个字符串内存地址是否相等
- str.delete(1,3) 删除1到2（不包括3）字符
- str.split(";");  用；分割字符串
- java 不准参数设置默认值
- java不会传递对象，只对传递对象引用，按引用传递对象，数组也是引用传递，值才会传递
- 静态函数不能调用非静态函数
- public static void main（String[] args)
- if(x=y)编译不过
- 子类可以访问所有（子类和超类）的public和protected方法
- private 修饰方法与属性只能在同一个类访问
- java变量一定要初始化
- java类只能单继承，或者伪多继承
- 线程是一次性消耗品，执行run()方法后，线程结束后销毁。不能再次start，只能重新建立新的线程对象。
- runnable接口必须重写run()
- Java.Lang.throwable 所有异常的基类
- bool值不可与任何其他类型转化 或 比较
- 类和对象只是同一个东西不同名称，类是对象的模板，对象是类的具体实例
- list常用方法，

增 add(Object obj)

删 remove(Index value/Object obj)

改 set(int index, Object obj)

查 get(int index)

插 add(int index, Object obj)

长度 size()

遍历1 Iterator 迭代器方式

2 增强for循环

3 普通循环

- 通过一个对象的引用访问静态成员属性或者方法时 ，访问操作只与所声明的引用类型相关 ；与引用对象是否为 null 无关 ，因为访问静态成员不需要实例化对象 ；即便引用不为 null ，也与运行时多态无关 ，因为静态成员是类相关的 。
- HashMap底层实现
- jdk 8 中注解新特性，可重复注解，类型注解

\1. 可重复注解

\2. 类型注解

注解就是类中的特殊标记，反射中读标记，在编译，类加载，运行时读取

- .super关键字作用

- - 主要存在于子类方法中，用于指向子类对象中父类对象。
  - 访问父类的属性
  - 访问父类的函数
  - 访问父类的构造函数

- 什么是枚举类，枚举类对象声明修饰符有哪些？

- - 枚举类：类中对象个数是有限的，不能再增加，
  - 当用常量时候，建议用枚举类
  - 如果枚举类只有一个对象，则可用单例模式实现方式
  - 
  - private final(no 错的)
  - private static final(yes 是的）

- 什么是元注解？说说Retention 和 Target 元注解作用

- - 元注解：对现有注解进行解释说明的注解
  - Retention： 指明所修饰的注解的生命周期，SOURCE CLASS（默认） RUNTIME

- 比较throw和throws区别

- - throw：生成一个异常对象，并抛出。方法内部<-->自动抛出异常对象
  - throws：处理异常方式，<--> try - catch - finally
  - "上游排污，下游治污"

- 谈谈你对同步代码块中同步监视器和共享数据的理解及各自要求

- - 同步监视器：俗称锁

  - - 任何一个类的对象可以充当锁
    - 多个线程公用一把锁

  - 共享数据，多个线程共同操作数据，即为共享数据。需要使用同步机制将操作共享数据代码包起来，不能包多了，也不能包少了。

- 开发过程中用框架，不会自己写组件，不会写JDBC，用Mybatis 等等框架应对更复杂实际开发场景 效率高

- - 框架 = 注解(免去xml)+反射机制+设计模式

- 自定义注解，查看SuppressWarnings定义

- - 注解里面（）其实是属性 不是方法

- 如何获取注解信息，通过反射来进行获取，调用

前提：要求此注解的元注解Retention中声明的生命周期状态为Runtime

- iterator() 三个方法 指向Collection第一个元素前面的元素

- - .hasNext()
  - .next()
  - .remove()

- hashset底层是hashmap，对对象求hashcode散列，链表，比较时候先比较hash值，一样再去比较equal方法

- linkedhashset多两个双向链表指针

- treeset类中加implements comparable，重写compareto方法，treeset中比较不用equal而用compareto

- treeset用到底层结构是红黑树

- 自然排序中，比较两个对象是否相同标准是 compareTo() 返回0 不再是equals()

- 定制排序中，比较两个对象是否相同标准是compare()返回0 不再是equals()

- 集合Collection中存储如果是自定义对象，需要自定义重写那个方法？

- - equals方法

  - LIst重写equals

  - Set

  - - （HashSet，LinkedHashSet为例）equals hashcode
    - （TreeSet）Comparable Comparator

- ArrayList LinkedList Vector 三者异同？

- - 三者都是List类，有序可重复
  - Vector线程安全
  - LinkedList底层是链表 ArrayList Vector 数组
  - ArrayList最常用 Vector最老

- CurrentHashMap 分段锁技术 实现多个线程操作同一部分共享数据

- Map底层实现原理：

- - map.put(key1,value1)

  - - 首先，调用key1所在类的hashCode()计算key1哈希值，此哈希值经过某种算法计算后，得到Node数组中存放位置

    - 如果，此位置数据空，key1-value1添加成功，情况1

    - 如果此位置上数据不为空，已存放一个或多个数据，链表形式，比较key1和已经存放的数据

    - - 如果哈希值与已有数据不相同，链表末端增加一个新Node，情况1

      - 如果哈希值与已经存在某一个哈希值相同，key2-value2哈希值相同，继续比较 用equals

      - - 如果返回false，添加key1-value1添加成功，情况2
        - 如果返回ture，则修改已有value2

- jdk7 底层 数组+链表；jdk8 底层 数组+链表+红黑树

- 数组典型替换就是List

- 当数组某一个索引上元素以链表形式存在个数>8 且当前数组长度>64时，索引位置上所有数据以红黑树存储

- - hashMap默认容量：16

  - hashMap默认加载因子 0.75

  - - 决定了HashMap的数据密度
    - 加载因子越大，密度越大，发生碰撞密度越高，数组中链表容易越长，造成查询或插入时的比较次数增多，性能下降
    - 负载因子越小，越容易扩容，数据密度越小，发生碰撞几率越小，数组中聊表也越短，查询和插入比较次数也小，性能高，但会浪费空间9998

  - threshold扩容临界值

  - Bucket中链表长度大于默认值，转化为红黑树，8

  - 桶中的Node被树化最小hash表容量64

- LinkedHashMap多了两个before after(类是entry是Node子类)

- Collections是操作Set List和Map的工具类，方法基本是静态方法，Collection是容器意思，是个接口

- TreeMap，中添加key-value，由于需要排序，所以key必须是同一个类创建的对象

- hashTable中的property用来记录配置文件

- ADT抽象数据结构

- Map存储数据结构特点是什么？并指明key value entry存储数据的特点

- - 双列数据，存储key-value对数据
  - key：无序的，不可重复的->Set存储
  - value：无序的，可重复的->Collection存储
  - key-value：无序的，不可重复->Set存储

- 描述HashMap的底层实现原理，

- - 数组 + 链表（装树的根） + 红黑树（左小右大）

- Map中常用实现类有哪些，各自特点

- - 在eclipse工程中

- 如何遍历Map中key-value对，代码实现

- - \1. entrySet() 定义 它的迭代器， hasNext() next() 来遍历
  - \2. keySet() 直接得到key的迭代器，hasNext() next() 来遍历

- Collection和Collections区别

- - 前者单列集合的接口，定义一些规范，List和Set
  - 后者是操作Collection和Map的工具类，有很多方法

- P561复习的多看几遍

- 接口和抽象类的概念不一样。接口是对动作的抽象，抽象类是对根源的抽象。

抽象类表示的是，这个对象是什么。接口表示的是，这个对象能做什么。比如，男人，女人，这两个类（如果是类的话……），他们的抽象类是人。说明，他们都是人。

人可以吃东西，狗也可以吃东西，你可以把“吃东西”定义成一个接口，然后让这些类去实现它.当你关注一个事物的本质的时候，用抽象类；当你关注一个操作的时候，用接口。

- 接口没有构造器 关键词是 interface

- extend 继承，泛型类的子类继承时候可以指定类型

- 泛型类可以有多个参数，逗号隔开

- 异常类不能泛型

- 泛型类中的方法中 不能是静态的

- 泛型方法可以是static的，原因：泛型参数是在调用方法时确定的，并非在实例化类时确定的

- DAO data access object，即操作数据库；ORM object relational mapping，即一个表对应一个类

- 泛型在继承方面体现：

- - 尽管 类A是类B的父类，但是G<A>、G<B>二者不具备子父类关系，二者是并列关系；
  - 补充 类A是类B的父类，A<G>是B<G>的父类

- 通配符：？，可作为别人的父类

- - 类A是类B的父类，G<A>和G<B>是没有关系的，二者共同的父类是G<?>

- 有限制条件的通配符使用

- - ？extends A：G<? extends A> 可以作为G<A> 和 G<B>的父类，其中B是A的子类，类似于小于等于
  - ？super A：G<？super A>可以作为G<A>和G<B>的父类，其中B是A的子类，类似于大于等于

- 缓冲流 复制文件速度更快

- 客户端/浏览器端 ----- 后台(java, GO, Python, Node.js，php) ----- 数据库，要求前后统一 UTF-8

- 对象流，用于存储和读取基本数据类型数据或对象的处理流，把java对象写入数据源中，或者把对象从数据源中还原

- 序列化机制，允许把内存中java对象转换成和平台无关的二进制流，从而使得二进制流持久存在磁盘上，网络将二进制流存到某节点，其他程序获得这个二进制流，就可以恢复成原来java对象

- - 序列化：ObjectOutputStream 保存
  - 反序列化：ObjectInputStream 读取

- 转换流：OutputStreamWriter 是字符流通向字节流的桥梁：可使用指定的字符编码表，将要写入流中的字符编码成字节，将字符串按照指定的编码表转成字节，在使用字节流将这些字节写出去

- close()和flush()的区别?

- - close()关闭流对象，但是先刷新一次缓冲区。关闭之后，流对象不可以继续再使用。
  - flush()仅仅刷新缓冲区,刷新之后，流对象还可以继续使用。

- 异常和序列化都需要提供一个序列版本号（全局常量）

- - public static final long serialVersionUID = 65869324798275L

- 不能序列化 用static 和 transient修饰

- 不一定真的传输内存中可序列化对象，特殊格式字符串——json

- 方法重载，两同一不同，类和方法名相同，形参不同

- 可变参数的方法

- - public void show(String ... strs){ //可变形参，只能有一个，写在列表最后面
  - ​     把strs当字符串数组处理即可
  - }
  - 同时保留public void show(String strs){}

- P211讲堆和栈

- 1 内存结构：栈（局部变量）、堆（new 出来的结构 对象（成员变量）数组等）

- 2 变量：成员变量 vs 局部变量 (方法内、方法形参、构造器内、构造器形参、代码块内)

- 面试题

- - 方法重载和重写区别
  - throws和throw
  - String/StringBuffer/StringBuilder
  - Collection/Collections
  - final/finally/finalize

- java bean 是一种Java写成的可重用组件

- - 所谓javabean，是指符合如下标准的java类

  - - 类是公共的，
    - 有一个无参构造器（由于需要通过反射造对象）
    - 有属性，且有对应get set方法

- UML图，unified modeling language统一建模语言

- 封装性

- - 实际问题中，我们要给属性赋值加入额外的限制条件，这个条件不能在属性声明时体现，只能通过方法进行限制条件添加，我们要避免用户用对象.属性赋值。则我们需要将属性声明为私有的(private)，体现了封装性
  - 我们将xxx属性私有化，同时提供公共的方法来获取（getxxx）和设置（setxxx）
  - 扩展：封装性体现在，1如上 2不对外暴露私有的方法 3 单例模式
  - 封装性体现通过修饰符实现，四种权限(从小到大)：private 缺省 protected public
  - 四种权限来修饰类及类内部结构：属性，方法，构造器，内部类
  - 修饰类只能用： 缺省 public

- this关键字 表明当前对象的属性 而不是形参

- - this.方法 或者 this.属性

- import导入，

- - import导入源文件中指定包和接口
  - import导入在包的声明和类声明之间
  - 使用“xxx.*”结构导入xxx包下面所有结构
  - 如果是java.lang包下定义的，可以省略
  - 如果使用的类或接口是本包下面的，也可以省略

- final最终的

- - 1 final 可以用来修饰结构：类，方法，变量

  - 2final用来修饰一个类，不能被其他类继承

  - - 比如：String、System、StringBuffer类

  - 3final用来修饰方法，表明此方法不可以被重写

  - - 比如：Object中的getClass()

  - 4final变量

  - - 修饰属性，可以显示初始化/代码块初始化/构造器初始化赋值一次，且只可赋值一次
    - 修饰局部变量，尤其是修饰形参时，表明此形参是一个常量，当我们调用方法时，给常量形参赋一个实参

​    一旦赋值以后，就只能使用不能修改

- static随类加载而加载，可以修饰：属性，方法，代码块，内部类

- - final static 修饰全局常量和属性

- 单例设计模式：饿汉模式，懒汉模式 ？？？

- private 私有的new不了，也不能重写

- 抽象的父类，以至于他没有具体的实例，这样类叫做抽象类。

- 方法可以重写，构造器不能重写，只能重载

- 类是单继承的，接口实现多继承效果

- 接口只能定义全局常量和抽象方法，接口中不能定义构造器，意味着不可以实例化

- 接口只能通过类+implements方式使用

- - 实现类实现了接口中的抽象方法

- 创建线程，四种方式，API两种，jdk5.0后面两种

- 解决线程安全问题三种：同步代码块，同步方法，log

- 程序是静态代码，进程是运行中的程序，线程是进程里面一条独立执行路径

- 看一下P413，讲jvm进程线程等知识

- 每个线程有自己独立程序计数器和运行栈，但是一个进程中不同线程共同使用一套堆和方法区，多线程操作公共系统资源是线程安全

- 多线程程序的优点：

- - 提高应用程序响应，对图形化界面更有意义
  - 提高计算机系统CPU利用率
  - 改善程序结构，将既长又复杂进程分为多个线程，独立运行，方便理解修改

- Thread下的方法：

- - 1.start() 启动当前线程，调用当前线程的run();
  - 2.run() 通常需要重写Threa类中此方法，将创建的线程要执行的操作写在此方法中
  - 3.currentThread() 静态方法，返回执行当前代码的线程
  - 4.getName() 获取当前线程名字
  - 5.setName() 设置当前线程名字
  - 6.yield() 释放当前cpu执行权
  - 7.join() 在线程a中调用b的join()方法，此时线程a进入阻塞状态，知道b执行完结束
  - 8.stop() 已过时，当执行此方法时，强制结束进程
  - 9.sleep(long millitime) 当前线程睡眠指定毫秒，在此之前线程处于阻塞状态
  - 10.isAlive 判断当前进程是否存活

- Thread的优先级

- - 1 MAX_PRIORITY = 10	//优先级高，优先运行权高，高概率被执行
  - 2 MIN_PRIORITY = 1
  - 3 NORM_PRIORITY = 5
  - getPrioirty();
  - setPrioirty(int p);

- 多线程两种构建方法：

- - 继承Thread类

  - 实现Runnable接口，后者好一点：

  - - java的单继承性质，本身可能有父类，继承Thread
    - 第一种方法，共享数据必须加static才能成为多线程共享数据，第二种，实现接口的类中数据天然共享

- 联系：

- - public class Thread implements Runnable
  - 两种方式都要重写run()，将线程要执行的逻辑声明在run()中

- 线程通信：wait() / notify() / notifyAll() ：此三个方法定义在Object类中的

- 线程的生命周期：NEW、RUNNABLE、BLOCKED、WAITING、TIMED_WAITING和TERMINATED。

- 新建 就绪 运行 阻塞 死亡

- - 新建 + start() = 就绪
  - 运行 + 执行完run()/调用stop()/出现Error/Exception但不处理 = 死亡
  - 运行 + sleep(long time)/join()/等待同步锁/wait()/suspend() = 阻塞
  - 阻塞 + sleep()时间到/join()结束/获取同步锁/notify()、notifyAll()/resume() = 就绪

- 方式一：

- - synchronized(同步监视器){//需要同步的代码块} //可以用windows1.class 方式1继承；this 方式2接口当锁
  - 同步监视器 俗称 锁，任意一个对象均可，
  - 要求：多个线程公用一把锁，不能写在run方法里面，要写在类里面的对象

​    说明：操作共享数据的代码，即为需要被同步的代码，

​    共享数据：多个线程共同操作的变量

- 方式二：

- - 

- 同步的方式，解决了线程的安全问题——好处

- - 操作同步代码时，只能有一个线程参与，其他线程等待，相当于是单线程，效率低







回头再看一下 哈夫曼树 和 哈希散列的代码