---
layout: post
title: 中国人民共和国地址选择器
category: 技乃艺之末
---
<h2>{{page.title}}</h2>
<div id="test">
	<select id="testareapicker"></select>
	<script>
		$(function(e) {
			$('#testareapicker').areaPicker({});
		});
	</script>
</div>
<p>{{page.date|date_to_string}}，转载请注明：http://www.scylla.me{{page.url}}</p>
<script type="text/javascript" src="/js/jquery.query.js"></script>
<script type="text/javascript" src="/js/area_json.js"></script>
<script type="text/javascript" src="/js/jquery.areapicker.js"></script>
