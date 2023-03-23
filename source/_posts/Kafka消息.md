---
title: Kafka消息
categories: Kafka
tags: Kafka
---
 一、基本概念
     1.Broker：消息中间件处理节点，一个kafka节点就是一个broker，一个或多个Broker可以组成一个kafka集群。
	 2.Topic：kafka根据topic对消息经行归类，发布到kafka集群的每条消息都需要指定一个topic。
	 3.Producer：
	 4.Consumer：
	 5.ConsumerGroup：每个Consumer属于一个特定的消费组，一条消息可以被多个不同的消费组消息，但是一个消费组中只有一个消费者可以消费该消息。（单播和多播实现）
	 6.Partition：物理上的概念，一个topic可以分为多个分区，每个分区内部消息是有序的。<font color="#660000">分区存储可以解决文件过大的问题，提高读写的吞吐量。</font>
 二、消费消息
     kafka有两种消费消息的方式：
	 　a.从当前主题的最后一条消息的offset（偏移量位置）+1开始消费。
	 　b.从当前主题的第一条开始消费。
