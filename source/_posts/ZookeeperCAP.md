---
title: ZookeeperCAP
categories: Zookeeper
tags: Zookeeper
---
 一、CAP定理
	 一个分布式系统最多只能同时满足一致性（COonsistency）、可用性（Availability）、和分区容错性（Partition tolerance）
	 1.一致性：更新操作成功并返回客户端后，所有节点在同一时间的数据完全一致。
	 2.可用性：服务一致可用，而且是正常响应时间
	 3.分区容错性：分布式系统在遇到某节点或网络分区故障的时候，仍然可以对外提供满足一致性或可用性的服务。避免单点故障，就要进行冗余部署，冗余部署相当于是服务的分区，这样的分区就具备了容错性。<font color="#660000">（必须）</font>

 二、BASE理论
	 1.基本可用
	 2.软状态
	 3.最终一致性
