---
title: JAVA引用类型总结
categories: JAVA
tags: JAVA
---
 #### 强引用
 ``` Person person = new person(); person = null;``` 此时person没有任何对象指向它，会被垃圾回收机制回收。
 #### 软引用
 ``` SoftReference<byte[]> sr = new SoftReference<>(new byte[1024*1024*10])```; 此时sr是软引用，如果此时有一个引用如```byte[] b = new byte[1024*1024*10] ```		        导致JVM内存不够的时候，会把sr回收掉，不会报OOM的异常。一般使用在缓存场景，由SoftReference包装。
 #### 弱引用
 ``` WeakReference<M> wr = new WeakReference<>(new Person());  ```
	垃圾回收器发现就会回收该对象。
``` ThreadLocal<Person> tl = new ThreadLocal();
	tl.set(new Person());
	tl.remove();  ```
	ThreadLocal 每个线程是自己私有的，其他线程访问不到。
 #### 虚引用
 堆外内存使用
 