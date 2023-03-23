---
title: Java多线程与高并发2
categories: Java
tags: 多线程
---
 #### 线程池
 1.使用已存在的线程，消除了线程创建的时耗。
 2.通过设置线程数目，防止资源不足。
 3.ThreadPoolExecutor：corePoolSize：线程池中的核心线程数（不会被销毁） maximumPoolSize:线程池中能拥有的最多线程数 workQueue：用于缓存任务的阻塞队列 keepAliveTime:空闲线程的存活时间 handler:表示当workQueue已满，且池中的线程数达到最大线程数时，线程池拒绝添加线程的策略。
 4.newCachedThreadPool: 工作的线程创建数量几乎没有限制，空闲的线程会自动销毁，使用时需要注意控制任务的数量，否则大量线程同时运行，会造成系统瘫痪。
 5.newFixedThreadPool：创建一个固定线程数量的线程池，不会自动销毁空闲的线程池，浪费资源，根据业务需求使用。
 6.newSingleThreadExecutor：创建一个单线程化的Executor，保证所有任务按照指定顺序执行，感觉不如单线程。
 7.newScheduleThreadPool：线程执行周期性的任务。
 #### Callable
 1.优点：可以有返回值。
 2.缺点：当没有返回值的时候线程会阻塞，在线程很多时可能会导致线程爆炸。