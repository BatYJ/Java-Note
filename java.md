## java
#### HashMap 实现
+ Entry数组，初始长度16，0.75扩容，拉链式处理hashcode相同的key

#### 线程池
+ 重复利用已创建的线程，减少JVM消耗
+ 任务到达时，不需要等待线程创建就能立即执行，响应时间快
+ 线程统一调优，分配，利于管理
+ ```corePoolSize``` ```maximumPoolSize``` ```SynchronousQueue``` ```LinkedBlockingQueue(任务数无限制)``` ```ArrayBlockingQueue```
+ 自定义一个线程池
+ ```newCachedThreadPool``` ：来任务就创建线程，线程空闲超过60秒，销毁线程
+ ```newSingleThreadExecutor```
+ ```newFixedThreadPool```

#### 线程同步原理
+ ```wait```: 持有该对象的线程把该对象的控制权交出去，然后处于等待状态
+ ```notify```: 通知某个正在等待这个对象控制权的线程可以继续运行
+ ```notifyAll```: 通知所有等待这个对象控制权的线程继续运行（互相竞争，最终只有一个线程获得控制权）
+ 使用wait notify notifyAll 需要保让线程拥有对象的控制权，可以通过synchronized对象保证，否则会抛出```java.lang.IllegalMonitorStateException```

#### 内存泄露 循环引用

#### gc机制 


#### ConcurrentHashMap volatile
+ ConcurrentMap 通过分段锁，锁定Segment，而不是整个ConcurrentHashMap

#### jstack jmap jstat jinfo JVM基本参数 -verbose:class javap
+ jmap用法：```jmap -dump:format=b,file=heap.bin``` 进程号  生成的heap.bin文件通过Eclipse MAT工具进行分析
+ 出现内存溢出 使用 jvm参数 ```XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/home/admin/logs -XX:ErrorFile=/home/admin/logs/hs_err_pid%p.log``` 获取溢出时的镜像文件，通过MAT进行分析

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
