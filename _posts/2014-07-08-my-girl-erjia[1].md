---
layout: post
title: 二佳三部曲之远程操作智能电视利器
category: 二佳工作日志
---
<h2>{{page.title}}</h2>
<p>调试工具adb (android debug bridge)，主要使用adb完成大部分操作，此外作为linux系统能够使用ssh作为远程操作的工具。Eclipse中DDMS通过adb来调试android程序。原理就是本地adb工具与远程端口5555adbd服务进行通讯实现远程控制。通过adb可以实现软件安装、系统升级、shell (http://developer.android.com/tools/help/adb.html)</p>
<p>1. android sdk安装配置</p>
<p>下载android sdk，将platform-tools、tools文件夹路径加入到环境变量path中，便于在cmd中使用。</p>
<p>2. 设备配置</p>
<p>打开设备(智能电视、手机)的调试模式，在设置—开发中可以找到。如果是通过串口、usb连接设备，通过adb devices命令可以查看当前连接的设备；如果是通过ip访问通过adb connect命令进行远程连接。adb命令可以通过 adb help进行查看。</p>
<p>3. 常用命令</p>
<p>
	adb install：将本地apk安装到设备上</br>
	adb uninstall [-K] &lt;软件名&gt;：软件卸载，加入k参数保留软件配置和缓存</br>
	adb shell [linux 命令]：进入linux终端，加入命令则为仅执行此条linux命令，通过linux命令进行android内核和应用程序log抓取、调试</br>
	adb push &lt;本地文件路径&gt;&lt;远端文件路径&gt;：将本地文件发送到远程设备</br>
	adb pull &lt;远端文件路径&gt;&lt;本地文件路径&gt;：下载文件到本地
	adb bugreport：查看bug报告</br>
	android应用日志还可以使用logcat来抓取，logcat是android提供的日志命令行工具用于处理代码逻辑中使用Log类进行输出的结构化日志，其他命令可以通过adb help查看
</p>
<p>4. 实际操作</p>
<p>
	将browser作为系统应用安装到远程电视机上：1、打开电视……2、使用串口连接电视，通过终端检查adbd服务是否开启，需要用的linux命令 stop/start [服务]，这两个命令用于停止/启动服务，关于linux服务的解释和配置可以去看一下鸟哥的私房菜 linux服务配置 相关内容，对于这两个命令的用法 在linux终端下 man stop 或 man start查看，所有命令的文档都可以用man来查看，不要嫌弃文档是英文的。3、确认adbd服务启动后，确认电视机ip和adbd监听端口，ip通过终端命令ifconfig查看，adbd监听端口可以通过ps -ano|grep adbd确定。4、使用串口配置及确认信息后，在本地cmd中使用adb可以方便的进行远程操作。连接命令：adb connect 111.111.111.111:5555，连接成功后会有提示，连接不成功将错误回复在文章下面的留言版中集中解决，一般就是网络问题。使用adb devices查看连接的设备，使用adb disconnect 111.111.111.111:5555断开连接。连接到设备后偷一下懒，使用adb root提升一下权限，或者进入adb shell后su一下，方便之后操作，权限不是万能的，需要什么权限使用chmod添加什么权限，操作之后在将权限还原才是正确的。将/system重新挂载为可读写目录，使用linux mount命令：mount -o remount rw /system，否则不能进行写操作，重新挂载后，为/system/application添加写权限，具体要去了解linux权限控制ugo分组及rwx(1,2,4)相关概念，为你当前用户添加相应权限。这样能够将browser.apk push到/system/application，之后reboot一下系统，不用硬开关电视。</br>
	后文会对android远程调试进行说明，二佳加油。
</p>
<p>{{page.date|date_to_string}}，转载请注明：http://www.scylla.me{{page.url}}</p>