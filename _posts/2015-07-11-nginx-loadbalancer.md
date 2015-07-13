---
layout: post
title: 确定使用的jre版本
category: 技乃艺之末
---
<h2>{{page.title}}</h2>
<p>程序安全性需要，要在jre/lib/security中放置ssl连接证书，可惜不如愿。遂在每个jre版本中都放入一个，可行，才知需确定jre使用版本。在windows系统中可以在注册表中查看：<pre class="prettyprint">HKEY_LOCAL_MACHINE/SOFTWARE/JavaSoft/Java Runtime Environment，CurrentVersion</pre></pre></p>
<p>{{page.date|date_to_string}}，转载请注明：http://www.scylla.me{{page.url}}</p>