---
title: redis
categories: redis
tags: redis
---
 #### 缓存与数据库双写不一致问题
![](/images/redis缓存与数据库双写不一致问题.png)
1.给缓存设置过期时间
2.延迟双删除
3.利用分布式锁解决 更新数据库和缓存的时候单线程 注意粒度 性能慢 

CREATE TABLE `t_workflow_alarm` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT COMMENT '数据编号',
  `title` varchar(256) NOT NULL DEFAULT '' COMMENT '工单标题',
  `workflow_status` int(11) NOT NULL DEFAULT '0' COMMENT '工单状态',
  `status` int(11) NOT NULL DEFAULT '0' COMMENT '数据状态',
  `plan_time` datetime COMMENT '期望完成时间',
  `description` longtext COMMENT '告警详情',
  `findings` longtext COMMENT '调查结果',
  `dispose` longtext COMMENT '处置建议',
  `rectification` longtext COMMENT '整改方案',
  `remark` longtext COMMENT '备注评论',
  `alarm_id` varchar(256) NOT NULL DEFAULT '' COMMENT '告警编号',
  `alarm_ip` varchar(32) NOT NULL DEFAULT '' COMMENT '告警ip',
  `alarm_type` int(11) NOT NULL DEFAULT '0' COMMENT '告警类型',
  `uri` longtext COMMENT '多个uri以|分割',
  `cve` varchar(256) NOT NULL DEFAULT '' COMMENT 'cve编号',
  `srmId` bigint(20) NOT NULL DEFAULT '0' COMMENT '农信工单id',
  `alarm_ids` longtext COMMENT '警id列表,多个以,分割',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='告警处置工单表';
 
 alarm_ip	varchar(32)	告警ip			
uri	longtext	多个uri以|分割			
cve	varchar(256)	cve编号			
srmId	bigint(20)	农信工单id			
alarm_ids	longtext	告警id列表,多个以,分割			



