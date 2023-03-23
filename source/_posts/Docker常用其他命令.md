---
title: Docker常用其他命令
categories: Docker
tags: Docker
---
 一、常用其他命令
	  1.后台启动命令 docker run -d 镜像名 常见的坑：docker容器使用后台运行，就必须要有一个前台进程，docker发现没有应用，就会自动停止。
	  2.查看日志 docker logs -tf -- tail [行数] 容器
	  3.查看容器中进程信息 docker top 容器id 
	  4.查看镜像元数据 docker inspect 容器id
	  5.进入当前正在运行的命令 
	  　a.docker exec -it 容器id /bin/bash   进入容器后开启一个新的终端，可以在里面操作
	  　b.docker attach 容器id 进去容器正在执行的终端，不会启动新的进程
	  6.从容器内拷贝文件到主机上 docker cp 容器id：容器路径 目的主机路径
 二、安装插件基本步骤
	 1.搜索插件 docker search
	 2.下载下来 docker pull
	 3.启动 docker run -d -p 1009:8080 --name tomcat1 tomcat 对外可以用1009访问
![](/images/docker端口暴露.jpg)
