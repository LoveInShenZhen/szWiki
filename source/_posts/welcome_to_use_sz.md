 ---
title: 欢迎使用SZ后端开发框架
date: 2019-05-15T07:24:14.813Z
toc: true
tags: 
categories: 
    - SZ 后端开发框架
    - 简介
---

## 介绍
* **SZ** 是一套基于 **前后端分离** 的思想, 专门用于 **后端** (业务,应用服务器)的 **快速开发框架**.
* 开发语言: **[kotlin](https://kotlinlang.org/)** _[中文站点](https://www.kotlincn.net/)_
* **SZ** 是从 **[Play Framework](https://www.playframework.com/)** 中得到的启发, 底层框架是采用 **[vertx](https://vertx.io/)** 为基础开发而来的.  
* Java Web development _**without J2EE**_, 完全基于 **J2SE**, JDK 版本要求: **JDK 1.8** 及以上

## 前后端分离

### 什么是前后端分离?
* 核心思想是前端 **HTML纯静态页面** 通过 **Ajax** 调用后端的 **Http API** 接口并使用 **JSON** 数据进行交互

<center>
<img src="https://kklongming.github.io/res/images/diagram_1.jpg" width="50%" />
前后端分离示意图
</center>

### 为什么要采用前后端分离的方式进行开发?
* 前端和后端开发人员的技术技能, 思维方式是不一样的

> 1. 前端开发人员, 主要处理的问题是页面展现, 用户交互. 需要处理很多跟美术设计, 用户交互设计相关的问题. 
> 1. 后端开发人员, 主要处理的问题是业务逻辑如何实现, 数据如何查询,存储,更新. 
> 1. 从思维方式上可以看出, 前端对形象思维能力要求高, 而后端对逻辑思维能力要求高. 对普通人而言, 这2中思维方式很难同时拥有较高的水准.

* **Web 前端** 和 **移动端App** 可以重用后端的 **Http Api** 
* 在生产环境下可以节省带宽, 从而降低成本费用

> 一般采用nginx做静态HTML页面的host, 启用 ETag. 现代的浏览器基本上都支持 ETag.  浏览器对静态资源访问过一次后就会缓存下了. 下次访问的时候, 服务端(Nginx)会检查请求中的ETag与当前请求的资源的ETag是否一致, 如果一致, 返回的Response会告诉浏览器,你要访问的静态资源, 与你缓存里的一致. 这样, 只要静态页面资源(html,js,css,img...)不发生变化, 后续的访问就不需要实际传输静态资源的内容了, 流量带宽就这么省下来了. 而数据部分, 是浏览器通过Ajax调用后端的Http Api获取的json数据, 而api占用的带宽资源相对于原来整个页面加载来说, 是很小的一部分. 并且, 对查询类的api, 后端也可以同样实现ETag的支持.

* 在部署时, **静态页面** 和 **Http Api** 可以部署在不同的子域名下, 不同的子域名可以配置不同的外网IP, 设置不同的带宽. 具体的配置方法, 会在单独的 **部署** 分类的文当中细述

## 参考资料
### ETag
> - [ETag 百度百科](https://baike.baidu.com/item/ETag/4419019?fr=aladdin)
> - [初识HTTP缓存-ETag](https://www.jianshu.com/p/3e2afe089e11)
> - [Nginx ETag配置(官网)](http://nginx.org/en/docs/http/ngx_http_core_module.html#etag)
> - [Nginx配置启用ETag提高访问速度](http://www.t086.com/article/5207)
