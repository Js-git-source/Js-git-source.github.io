---
title: Kafka运用
categories: Kafka
tags: Kafka
---
 一、生产者端的同步和异步发送
	 1.同步：如果生产者发送的消息没有收到ack，生产者会阻塞3s的时间，如果还没有收到消息，会进行重试。重试的次数3次。
	 　ACK配置
	 　　a.ack = 0：kafka-cluster不需要任何的broker收到消息，就立即返回ack给生产者。<font color="#660000">最容易丢消息的，效率最高。</font>
	 　　b.ack = 1：多副本之间的leader已经收到消息，并把消息写入到本地的log中，才会返回ack给生产者。<font color="#660000">性能和安全性是最均衡的。</font>
	 　　c.ack = -1/all：里面有默认的配置min.insync.replicas=2(默认为1，推荐配置大于等于2)。<font color="#660000">最安全，性能最差</font>
	 2.异步：生产者发送完消息后就可以执行之后的业务，broker在收到消息后异步调用生产者提供的callback回调方法。
 二、offset（偏移量）
	 1.消费者offset的自动提交和手动提交：
	 　a.手动提交：消费完消息后手动进行提交。
	 　　．手动同步提交：消费完消息后调用同步提交方法，当集群返回ack前一直阻塞，返回ack后表示成功，执行之后的逻辑。
	 　　．手动异步提交：消费完消息后不需要等到ack返回直接执行之后的逻辑。
	 　b.自动提交：消费者poll到消息后默认情况下，会自动向broler的_consumer_offset主题提交当前主题-分区的消费偏移量。<font color="#660000">
	 会丢消息：如果poll下来的消息还未被消费，消费者挂了此时poll下来的消息就会丢失</font>
	 2.poll消息：
	 　ａ.while(true){//配置时间内poll消息：如果时间内poll到500（可配置）条则直接执行for循环逻辑代码，如果没有到500条则继续poll知道消息到500条或者到设定时间}
	 　ｂ.如果两次poll的时间超过30s的时间间隔，kafka会任务其消费能力弱，将其踢出消费者组。触发rebalance机制，会造成性能开销。可以设置一次poll的消息条数少一点。
 三、rebalance：前提是没有指定分区，当消费组里的消费者和分区的关系发生变化时会触发rebalance机制
	 1.range：通过公式计算消费者应该在哪个分区。前面的消费者是sum/n+1，后面的消费者是sum/n （分区总数/消费者数）
	 2.轮询：大家轮着消费
	 3.sticky：在触发了rebalance后，在消费者消费的原分区不变的基础上进行调整
 四、HW和LEO
	 HW高水位，去一个partition对应的ISR中修小的LEO（log-end-offset）作为HW，Consumer最多只能消费到HW所在的位置。另外每个replica都有HW，leader和follower负责更新自己的HW状态。对于leader新写入的消息，Consumer不能立刻消费，leader会等到所有isr中的replicas同步后更新HW，此时消息才能被消费。这样保证了如果leader所在的broker失效，该消息仍然可以从新选举的leader中获取。
![](/images/zookeeper主从数据同步.jpg)
