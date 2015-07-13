---
layout: post
title: Nginx Sticky Module 方式实现负载均衡
category: 技乃艺之末
---
<h2>{{page.title}}</h2>
<p>
	最近项目需要提升web服务承载规格，初步选定使用Nginx反向代理+负载均衡，将请求映射到多个服务后端提高系统规格。多项对比后，决定使用Nginx Sticky Module这个第三方模块进行实现，并使用官方自带ip_hash作为备选方案。
</p>

