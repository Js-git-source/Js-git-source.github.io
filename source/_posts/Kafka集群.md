---
title: Kafka集群
categories: Kafka
tags: Kafka
---
 一、副本
	 副本是对分区的备份。在集群中，不同的副本会被部署在不同的broker上。
	 　a.replicas：当前副本存在的broker节点
	 　b.leader：副本里的概念 直接对它进行读写，然后备份到follower
	 　c.follower：不提供读写，备份用 如果leader挂掉，参与新的leader选举
	 　d.isr：可以同步和已同步的节点会被存到isr集合中，leader选举从此集合中选。如果isr中的节点性能较差，会被isr剔除集合。
 二、消费
     1.一个partition只能被一个消费组里的某一个消费这消费，从而保证消费顺序。kafka只在partition的范围内保证消息的局部顺序性，不能在同一个topic中的多个partition中保证总的消费顺序性。一个消费者可以消费多个partition。
	 2.partition的数量决定了消费组中消费者的数量，建议同一个消费组中的消费者不要超过partition，多出来的消费者消费不到消息。
	 3.如果消费者挂了，那么会触发rebalance机制，会让其他消费者来消费该分区。
![](/images/kafka副本.jpg)
