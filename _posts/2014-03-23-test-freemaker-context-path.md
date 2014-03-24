---
layout: post
title: freemaker之context_path设置
category: 技乃艺之末
---
<h2>{{page.title}}</h2>
<p>
实现一个自己的FreeMakerViewResolver
{% highlight java linenos %}
public class MyFreeMarkerView extends FreeMarkerView {
	private static final String CONTEXT_PATH = "base"; 
	@Override
	protected void exposeHelpers(Map<String, Object> model,
			HttpServletRequest request) throws Exception {
		model.put(CONTEXT_PATH, request.getContextPath());
		super.exposeHelpers(model, request);
	}
}
{% endhighlight %}
在模板中可以这样$\{base\}:
{% highlight java linenos %}
<bean class="org.springframework.web.servlet.view.freemarker.FreeMarkerViewResolver">
    <!-- 自定义FreeMarkerView，用来定义项目的全局路径 -->
	<property name="viewClass" value="com.scylla.utils.MyFreeMarkerView" />
</bean>
{% endhighlight %}
</p>
<p>{{page.date|date_to_string}}，转载请注明：http://www.scylla.me{{page.url}}</p>
