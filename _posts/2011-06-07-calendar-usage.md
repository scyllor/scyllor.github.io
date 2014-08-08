---
layout: post
title: Usage 4 Calendar
category: 技乃艺之末
---
<h2>{{page.title}}</h2>
<p>当我们需要处理时间问题的时候，我们首先想到的是Date类型，然而熟悉Date API的人一定都知道，这个类的许多方法都被废弃了，取而代之的是Calendar类，Calendar的中文意思是“日历”，因此用他来处理时间问题，也算是实至名归了，下面是我对Calendar的一些理解，不足之处请指正。</p>

<p>一．Calendar是一个抽象类，不能直接New一个实例，可以有两种方法得到它的实例：</br>
方法一：Calendar cal = new GregorianCalendar(); //GregorianCalendar是Calendar的实现类，</br>
方法二：Calendar cal = Calendar.getInstance();</br>
通过以上方法获得的实例，默认都是当前日期。我们可以通过以下代码验证一下：</br>

//此时是2010年8月25日15时18分18秒</br>
Calendar cal = Calendar.getInstance();</br>
System.out.println("DAY_OF_WEEK: "+cal.get(Calendar.DAY_OF_WEEK));</br>
System.out.println("DAY_OF_MONTH: "+cal.get(Calendar.DAY_OF_MONTH));</br>
System.out.println("DAY_OF_YEAR: "+cal.get(Calendar.DAY_OF_YEAR));</br>
System.out.println("YEAR: "+cal.get(Calendar.YEAR));</br>
System.out.println("MONTH: "+cal.get(Calendar.MONTH));</br>
System.out.println("HOUR_OF_DAY : "+cal.get(Calendar.HOUR_OF_DAY));</br>
System.out.println("MINUTE : "+cal.get(Calendar.MINUTE));	 System.out.println("SECOND : "+cal.get(Calendar.SECOND));</br>

得到的结果如下：</br>
DAY_OF_WEEK: 4</br>
DAY_OF_MONTH: 25</br>
DAY_OF_YEAR: 237</br>
YEAR: 2010</br>
MONTH: 7</br>
HOUR_OF_DAY : 15</br>
MINUTE : 18</br>
SECOND : 18</br>

注意：</br>
DAY_OF_WEEK表示星期几。从星期日开始到星期六为一个周期，数字表示依次为：1，2，3……7。
MONTH的表示是从数字0开始，所以月份应该是该数字+1.</p>

<p>二． 很多情况下，我们需要进行时间的计算，如：将某个时间向前推几小时、几天、几个月等。这个时候我们就需要对Calendar设定一个时间值。

我们有几种常见的设置方法：</br>
方法一：setTime(Date date)</br>

方法二：
set(int field, int value)</br>

方法三：</br>
set(int year, int month, int date)</br>
set(int year, int month, int date, int hourOfDay, int minute)</br>
set(int year, int month, int date, int hourOfDay, int minute, int second)</br>

方法四：setTimeInMillis(long millis)</br>

在进行时间运算的时候，我们经常会用到如下方法：</br>
add(int field, int amount)</br>

示例代码：</br>

Calendar cal = Calendar.getInstance();</br>
cal.add(Calendar.DATE, 1);</br>
System.out.println(cal.getTime());</br>

结果如下：</br>
Thu Aug 26 15:49:03 CST 2010</br>

以上是将时间向后推，如果要向前推，将第二个参数（amount）改成负数即可。</p>

<p>三． 另外，Calendar还提供几个非常好用的日期比较函数：</br>
after(Object when)</br>
before(Object when)</br>
equals(Object when)</br>
compareTo(Calendar anotherCalendar)</br>

需要注意的是：上面的Object参数类型必须是Calendar的实例(instance)，否则就没有意义了。示例代码：</br>

Calendar cal = Calendar.getInstance();</br>
Calendar cal2 = Calendar.getInstance();</br>

cal2.setTimeInMillis(1282023123371L);</br>

System.out.println("Date1: " + cal.getTime());</br>
System.out.println("Date2: " + cal2.getTime());</br>

System.out.println("Date1 is later than Date2: " + cal.after(cal2));</br>
System.out.println("Date1 is earlier than Date2: " + cal.before(cal2));</br>
System.out.println("Date1 equals Date2: " + cal.equals(cal2));</br>
System.out.println("Date1 compare to Date2: " + cal.compareTo(cal2));</br>

运行结果为：</br>
Date1: Wed Aug 25 16:18:07 CST 2010</br>
Date2: Tue Aug 17 13:32:03 CST 2010</br>
Date1 is later than Date2: true</br>
Date1 is earlier than Date2: false</br>
Date1 equals Date2: false</br>
Date1 compare to Date2: 1</br>

compareTo()函数的返回值有三个：0 1 -1，分别表示相等、大于（表示第一个时间离现在较近）、小于（表示第一个时间离现在较远）。</p>

<p>四． 总结
相比Date类型，Calendar显得更加灵活和强大。掌握Calendar的用法必将为你的开发之路打下良好的基础。更多详情请查阅JDK1.5帮助文档。
</p>
<p>{{page.date|date_to_string}}，转载请注明：http://www.scylla.me{{page.url}}</p>
