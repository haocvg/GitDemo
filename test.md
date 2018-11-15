测验
===

J2SE
---

### 基本数据类型

- int和Integer有什么区别？
```
int是基本数据类型，默认值是0；Integer是int的包装类型，默认值是null
```
- 运算符`&`和`&&`的区别？
```
&是非短路与，无论&前的判断是否成立，两边的判断都要执行；&&是短路与，当&&前边判断不成立时后方判断不再执行
```
- Math.round(11.5)等于多少？Math.round(-11.5)等于多少？
```
Math.round(11.5)等于12；Math.round(-11.5)等于-11
```
- equals/hashCode 必须同时实现或不实现
```
如果两个对象equals相同等,那么还必须拥有相同的hashcode才相等;两个对象有相同的hash code,他们不一定相等
```
- 当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递？
```
值传递，Java中只有值传递，引用传递一般需要指针
```
- String和StringBuilder、StringBuffer的区别？
```
String是字符串类型，被final修饰，不可继承，对象不可修改，修改内容时是先创建一个新的String对象，然后将引用指向新的对象，String重写了equals()方法；StringBiulder和StringBuffer其对象是可以被修改的，他们都没有重写equals()方法，StringBuffer是线程安全的。在有大量的字符串修改时StringBiulder和StringBuffer的效率要远高于String。
```
- char 型变量中能不能存贮一个中文汉字，为什么？
```
可以，char存放的是一个Unicode，汉字有对应的Unicode，所以每个char可以存放一个汉字
```
- Java 中的final关键字有哪些用法？
```
可以修饰变量，这个变量便不可以被修改，可以用来修饰常量；可以修饰方法，这个方法不可以被重写，可以用来保证方法安全、不被篡改；可以修饰类，类不可以被继承，如String
```
- 简述正则表达式及其用途。
```
正则表达式是用一串有规则的字符串来匹配另一串字符串，判断其是否符合规则，一般用于数据的校验
```

### Lombok

说明下列注解的作用：

- val
`用在局部变量，自动类型，final`
- @Data
`提供类的getter和setter，重写equals和hashcode，生成toString`
- @Value
`相当于@Data,属性前加final，只提供getter不提供setter`
- @EqualsAndHashCode
`重写equals和hashcode`
- @ToString
`提供toString方法`
- @Builder
`建造者模式`
- @Getter
`提供getter方法`
- @Setter
`提供setter方法`
- @RequiredArgsConstructor
`提供包含常量和notnull参数的构造`
- @AllArgsConstructor
`提供全参构造`
- @NoArgsConstructor
`提供无参构造`

### 集合类型

- List<T>、Set<T>、Map<K,V> 各自的用途？
```
List<T>储存T类型元素的有序集合，值可重复；Set<T>储存T类型元素的无序集合，值不可重复；Map<K,V>储存key-value的键值对集合，key不可重复，value可重复
```
- ArrayList<T>、LinkedList<T>、TreeMap<K,V> 的存储性能和特性。
```
ArrayList 和Vector他们底层的实现都是一样的，都是使用数组方式存储数据，此数组元素数大于实际存储的数据以便增加和插入元素，它们都允许直接按序号索引元素，但是插入元素要涉及数组元素移动等内存操作，所以索引数据快而插入数据慢。
LinkedList使用双向链表实现存储（将内存中零散的内存单元通过附加的引用关联起来，形成一个可以按序号索引的线性结构，这种链式存储方式与数组的连续存储方式相比，内存的利用率更高），按序号索引数据需要进行前向或后向遍历，但是插入数据时只需要记录本项的前后项即可，所以插入速度较快。
TreeMap取出来的是排序后的键值对。插入、删除需要维护平衡会牺牲一些效率。但如果要按自然顺序或自定义顺序遍历键，那么TreeMap会更好。
```

### 类型转换

- 如何将字符串转换为基本数据类型？
`使用包装类的parseXxx()方法；使用valueOf()方法转为基本类型的包装类型，然后自动拆箱`
- 如何将基本数据类型转换为字符串？
`拼接空字符串；使用包装类的toString()方法；使用String的valueOf()`
- 如何实现字符串的反转及替换？
`使用StringBuilder的revers和replace`
- 怎样将GB2312编码的字符串转换为UTF-8编码的字符串？
`byte的getBytes("GB2312")编码，new String(字符串变量,"UTF-8")转码；或者在IO流中转换`

### 时间(JSR310)

- 如何取得年月日、小时分钟秒？
`使用calendar的getTime()方法或者new Date()获取时间,使用SimpleDateFormat的format()规定时间显示格式；单独获取年月日时，要在calendar的getTime()方法传参，分别是calendar.YEAR等`
- 如何取得从2010年1月1日0时0分0秒到现在的毫秒数？
`long time = new Date().getTime()获取从1970年到现在毫秒`
- 如何取得某月的最后一天？
`calendar的getTime()传参calendar.DAY_OF_MONTH`
- 如何格式化日期？
`使用SimpleDateFormat("yyyyMMdd HHmm")规定格式,format()将时间传至SimpleDateFormat进行格式化`
- 打印昨天的当前时刻。
` calendar.add(Calendar.DATE, -1)，打印calendar.getTime()`
### 异常

- Error、Exception、RuntimeException 有什么区别？
`Error是关键性错误，一旦出现系统将会停止运行；Exception是异常的基类，分为检查时异常和运行时异常，检查时异常在编辑代码时就会出现提示，经过修改才能进行编译，运行时异常（RuntimeException）是在运行时才会报出的异常`
- 列出一些你常见的运行时异常？
`NullPointerException;NumberFormatException;ClassCastException;ClassNotFoundException`

### I/O

- Java中有几种类型的流？
`inputStream outputStream inputStreamReader outputStreamWriter`
- 写一个方法，输入一个文件名和一个字符串，统计这个字符串在这个文件中出现的次数。

- 如何用Java代码列出一个目录下所有的文件？
(```)
	File f = new File("/目录名");
        for (File t : f.listFiles()) {
            if (t.isFile()) {
                System.out.println(t.getName());
            }
        }
(```)
### RDB

- 设计几个数据模型，并用ERD说明之间的关系，然后提出几个数据访问的需求，并用SQL解决问题。
- 事务的ACID是指什么？
`原子性：事务不可分割，要么一起执行成功，要么一起执行失败；一致性：在事务执行前和执行后都保证数据和数据库中一致；隔离性：事务与事务之间相互不影响；持久性：事务产生的影响能够长久保存`
- 只读事务和读写事务在读取数据的一致性方面有什么差异？
- 你知道的事务隔离级有哪些？有什么区别？
- 你知道的事务传播方式有哪些？什么情况下起作用？

### JDBC

- 阐述JDBC操作数据库的步骤。
`加载驱动，建立连接，执行sql，处理结果集，释放连接`
- Statement和PreparedStatement有什么区别？哪个性能更好？
`PreparedSatatement可以防止sql注入，而且效率更高，性能更好`
- 使用JDBC操作数据库时，如何提升读取数据的性能？如何提升更新数据的性能？
- 在进行数据库编程时，连接池有什么作用？
`控制链接数量，资源复用，节省链接和放弃链接的开支`
- JDBC中如何进行事务处理？
`commit和rollback`


Spring Boot
---

### 说明下列注解的作用：

- @Profile
- @Configuration
- @ConfigurationProperties
- @EnableConfigurationProperties
- @Bean
`标识一个用于配置和初始化一个容器管理的新对象的方法`
- @Qualifier
- @Primary
`优先使用这个注解的bean`
- @Autowired
`自动装配`
- @Component
- @Service
`注解说明这是一个Service方法，纳入容器管理`
- @RestController (和`@Controller`有什么区别？)

### Bean Factory

- `Bean`从生命周期区分的话，有哪几种类型？
- 请用简约的代码描述推荐的外部配置引入方法。
- 请用简约的代码描述推荐的`Bean`的配置方法。


J2EE
---

### 安全

- 什么是SQL注入攻击？如何防护？
`在传入数据库的数据中包含sql语句，未作防护就可以获取数据、插入数据或者删除数据；使用PreparedStatement而不使用Statement,对传入数据库的信息进行验证`
- 什么是XSS攻击？如何防护？
- 什么是CSRF攻击？如何防护？

### JAR和WAR

- 请说明 jar 文件内部的构成及其作用
`resource.xml是资源配置文件 ，在META-INF下MANIFEST.MF是jar包的描述文件，其他目录下.class是java类文件 `
- 请说明 war 文件内部的构成及其作用
`.jsp等动态页面，images图片等资源，在META-INF下WEB-INF中web.xml是WAR包的描述文件 ，classes 中的.class是java类文件，lib中是依赖的jar包`
- 请说明 web.xml 中的内容有哪些？各有什么用途？
`配置文件位置，过滤器，监听器`

其他重要的技术点
---

### Swagger

API规范 Swagger 主要用到的 Annotation 有哪些，作用于哪些对象？

` @Api()用于类；
表示标识这个类是swagger的资源`<br>
` @ApiOperation()用于方法；
表示一个http请求的操作`<br>
` @ApiParam()用于方法，参数，字段说明；
表示对参数的添加元数据（说明或是否必填等）`<br>
` @ApiModel()用于类
表示对类进行说明，用于参数用实体类接收`<br>
` @ApiModelProperty()用于方法，字段
表示对model属性的说明或者数据操作更改`<br>
`@ApiIgnore()用于类，方法，方法参数
表示这个方法或者类被忽略`<br>
` @ApiImplicitParam() 用于方法
表示单独的请求参数`<br>
`@ApiImplicitParams() 用于方法，包含多个 @ApiImplicitParam`


### MyBatis

我们主要用到的 Mybatis Annotation 有哪些，作用于哪些对象？有什么用？<br>
<br>
结果函数<br>
`@Results 用于填写结果集的多个字段的映射关系. `<br>
`@Result 用于填写结果集的单个字段的映射关系. `<br>
`@ResultMap 根据ID关联XML里面<resultMap>. `<br>

CRUD的高级注解：<br>
`@SelectProvider`<br>
`@InsertProvider`<br>
`@UpdateProvider`<br>
`@DeleteProvider`

