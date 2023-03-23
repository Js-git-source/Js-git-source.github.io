---
title: Zookeeper常用命令
categories: Zookeeper
tags: Zookeeper
---
  1.重命名conf中的文件zoo_sample.cfg ->zoo.cfg
​  2.启动zk服务器
	./bin/zkServer.sh start ./conf/zoo.cfg
  3.查看zk服务器状态
	./bin/zkServer.sh status ./conf/zoo.cfg
  4.停止zk服务器
    ./bin/zkServer.sh stop ./conf/zoo.cfg