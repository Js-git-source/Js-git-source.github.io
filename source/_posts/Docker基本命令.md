---
title: Docker基本命令
categories: Docker
tags: Docker
---
 一、底层原理
	 Docker是一个Client-Service机构的系统，Docker的守护进程运行在主机上。通过Socket从客户端访问！Servev接到Client的指令就会执行这个命令。
	 　docker有着比虚拟机更少的抽象层（服务直接安装在操作系统上）快！
	 　docker利用的是宿主机的内核，vm需要是Guest Os。快！
 二、镜像命令
	 docker images 查看本地主机上的所有镜像信息
	 docker search 搜索镜像
	 docker pull 下载镜像
	 docker rml 删除镜像
 三、容器命令
	 docker run[可选参数] image 运行指定镜像
	 exit 从容器中退出到主机
	 docker ps 列出所有的运行的容器
	 docker rm [-f][{docker ps -aq}]容器id 删除指定[所有]容器
	 docker start 容器id     启动容器
	 docker restart 容器id	 重启容器
	 docker stop 容器id		 停止容器
	 docker kill 容器id		 强行停止容器
![](/images/docker原理.jpg)
