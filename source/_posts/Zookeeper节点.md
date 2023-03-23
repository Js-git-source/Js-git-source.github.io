---
title: Zookeeper节点
categories: Zookeeper
tags: Zookeeper
---
 一、节点类型
	1.持久节点
	2.临时节点
	3. 。。。。
![](/images/zookeeper节点.jpg)
 二、数据持久化
	 1.事务日志
	 zk把执行的命令以日志的形式保存在dataLogDir指定的路径文件中（如果没有指定dataLogDir,则按dataDir指定的路径）
	 2.数据快照
	 zk会在一点的直接间隔内做一次内存数据的快照，把该时刻的内存数据保存在快照文件中。
   zk通过两种形式的持久化，在恢复时先恢复快照文件中的数据到内存中，在用日志文件的数据做增量恢复，这样的恢复速度更快。
	delete -v 0 /node (删除版本为0的node节点，如果有其他人操作了该节点则删除失败->乐观锁删除)
