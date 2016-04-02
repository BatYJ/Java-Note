## java
#### HashMap 实现
+ Entry数组，初始长度16，0.75扩容，拉链式处理hashcode相同的key

#### 线程池 实现

#### 内存泄露 循环引用

#### gc机制 
+ http://blog.jobbole.com/80499/

#### 并发Map volatile

#### jstack jmap jstat jinfo JVM基本参数 -verbose:class javap

===


## Spring
#### bean 声明周期 
+ Spring容器 从XML 文件中读取bean的定义，并实例化bean。
+ Spring根据bean的定义填充所有的属性。
+ 如果bean实现了BeanNameAware 接口，Spring 传递bean 的ID 到 setBeanName方法。
+ 如果Bean 实现了 BeanFactoryAware 接口， Spring传递beanfactory 给setBeanFactory 方法。
+ 如果有任何与bean相关联的BeanPostProcessors，Spring会在postProcesserBeforeInitialization()方法内调用它们。
+ 如果bean实现IntializingBean了，调用它的afterPropertySet方法，如果bean声明了初始化方法，调用此初始化方法。
+ 如果有BeanPostProcessors 和bean 关联，这些bean的postProcessAfterInitialization() 方法将被调用。
+ 如果bean实现了 DisposableBean，它将调用destroy()方法。
