---
title: gateway
categories: Spring
tags: Java
---
Spring Cloud Gateway 提供统一的路由方式且基于Filter链的方式提供了网关的基本功能，如：安全，监控/指标，和限流。使用的是Webflux重的reactor-netty响应式编程组件，底层使用了Netty通讯框架。
三大核心概念：
　　1.Route(路由)
　　2.Predicate(断言)
　　3.Filter(过滤)