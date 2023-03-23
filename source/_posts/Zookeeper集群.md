---
title: Zookeeper集群
categories: Zookeeper
tags: Zookeeper
---
 一、ZAB协议
	解决了Zookeeper的崩溃恢复和主从数据同步问题。
	ZAB协议定义了节点的四种状态
	1.Looking：选举状态
	2.Following:Followe节点（从节点）所处的状态
	3.Leading：Leader节点（主节点）所处的状态
	4.Observing：观察者节点所处的状态

![](/images/zookeeper集群主节点选举.jpg)
 二、崩溃恢复时的Leader选举
	主节点会定时项从节点ping格式的空数据（socket），从节点会定时去读取这个信息，如果断掉则开始重新选举，此时集群不能对外提供服务。
 三、主从数据同步
	1.如果客户端连接的是从节点，即使写数据从节点也会把数据通信给主节点，
	2.由主节点把数据写到自己的数据文件中，并给自己返回一个ACK。
	3.主节点再把数据发送给Follower
	4.从节点将数据写道本地数据文件中
	5.从节点返回ACK给Leader
	6.Leader收到半数以上的ACK后向Follower发送Commit（半数以上是为了提高性能，整个集群的半数）
	7.从节点收到Commit后把数据文件中的数据写到内存中

![](/images/zookeeper主从数据同步.jpg)
