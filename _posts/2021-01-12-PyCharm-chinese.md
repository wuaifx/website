---
layout: post
title: 使用PyCharm官方中文语言包汉化PyCharm
categories: PyCharm
description: 使用PyCharm官方中文语言包汉化PyCharm
keywords: PyCharm， windows
---

对于英文不行我来说使用英文版PyCharm实在是太难受了，网上好多汉化补丁都是网友提供了，下面为大家介绍一种PyCharm官方中文语言包汉化方法

在PyCharm主窗口中点击菜单栏中的File菜单下的Settings...菜单进入PyCharm设置窗口，如下图

![](/images/posts/python/pycharm-ch.png)

![](/images/posts/mac/auto-operate.png)
	
PyCharm设置窗口，如下图。点击下图标注1 Plugins选项进入PyCharm插件管理窗口，在下图标注2处输入“chinese”系统会自动搜索相关插件，找到如下图标注3处所示的chinese(simplified) language pack eap插件安装此插件（点击下图标注4处 Install按钮）

![](/images/posts/python/pycharm-ch0.png)

PyCharm中文语言插件安装完成后需要重启PyCharm，如下图所示。点击下图标注1或2处 RESTART IDE按钮重启PyCharm

![](/images/posts/python/pycharm-ch1.png)

点击上图标注1或2处 Restart IDE按钮重启PyCharm后弹出确认重启提示窗，如下图。点击下图标注1处 Restart按钮确认重启PyCharm

![](/images/posts/python/pycharm-ch2.png)


完成重启后PyCharm主窗口成功改为中文，如下图。

![](/images/posts/python/pycharm-ch3.png)


##PyCharm汉化成功后如果我们想改回英文的该如何操作呢？

依然是在PyCharm的设置窗口中的Plugins选项中如，下图所示
	
![](/images/posts/python/pycharm-ch4.png)

点击上图标注1 Plugins选项进入插件管理窗口，点击上图标注2处的 Installed选项显示所有已安装PyCharm插件，找到并选中已安装的PyCharm中文语言插件上图标注3，点击上图标注4处 Disable按钮关闭PyCharm中文语言插件，然后点击上图标注5处 确定按钮重启PyCharm，重启后PyCharm又恢复到了英文状态。

再次改为中文只需按此操作打开PyCharm中文语言插件即可




