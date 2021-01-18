---
layout: post
title: 利用Python3开发一款小工具（界面的设计）
categories: Python
description: 利用Python3开发一款小工具（界面的设计）
keywords: Python， windows, pycharm, 软件开发， PublicSoftwareProject
---

## 简单的小例子``` ##



	#!/usr/bin/python3
	# -*- coding: utf-8 -*-
	import os
	import sys
	import paramiko
	from PyQt5 import QtCore, QtGui, QtWidgets

	if __name__ == '__main__':
    app = QtWidgets.QApplication(sys.argv)
    MyUI = QtWidgets.QWidget()
    MyUI.setWindowsTitle('demo')
    MyUI.resize(250, 150)
    MyUI.show()
    sys.exit(app.exec_())

![](/images/posts/python/PuSoftP.png)
    
上面的图就是运行之后的小窗口，下面对代码进行分块介绍：

	#!/usr/bin/python3
	# -*- coding: utf-8 -*-
	
第一行的含义是指定python3执行，第二行指定编码方式utf-8

	import os
	import sys
	import paramiko
	from PyQt5 import QtCore, QtGui, QtWidgets
	
这里是导入基本的必要模块，因为需要做界面，因此我我们将PyQt模块导入。

	app = QtWidgets.QApplication(sys.argv)
	
所有的PyQt5应用必须创建一个应用（Application）对象。sys.argv参数是一个来自命令行的参数列表。Python脚本可以在shell中运行。这是我们用来控制我们应用启动的一种方法。

	MyUI = QtWidgets.QWidget()

Qwidget组件是PyQt5中所有用户界面类的基础类。这里给QWidget提供了默认的构造方法。

	MyUI.setWindowsTitle('demo')
	MyUI.resize(250, 150)
	
resize()方法调整了widget组件的大小。它现在是250px宽，150px高。
setWindowsTitle(‘demo’)设置了我们窗口的标题，这个标题显示在标题栏中。

	MyUI.show()

show()方法在屏幕上显示出widget。一个widget对象在这里第一次被在内存中创建，并且之后在屏幕上显示。

	sys.exit(app.exec_())

最后，应用进入主循环。在这个地方，事件处理开始执行。主循环用于接收来自窗口触发的事件，并且转发他们到widget应用上处理。如果我们调用exit()方法或主widget组件被销毁，主循环将退出。sys.exit()方法确保一个不留垃圾的退出。系统环境将会被通知应用是怎样被结束的。

exec_()方法有一个下划线。因为exec是Python保留关键字。因此，用exec_()来代替。

## 2、我们的界面 ##

很多时候界面非常的复杂，我们单纯的使用代码生成，费时费力，那有没有一个简单直观的方式构造一个界面呢？
当然是有的，还记得开发环境搭建那一章节吧，我们在pycharm里添加了一个扩展工具qt designer。我们在这里就要用到qt designer来设计我们的界面。

## 2.1、界面规划 ##

1>用户设置部分

涉及到windows代码上传到Linux中，必然包含了Linux服务器地址、用户名、密码、远程目录名、本地工程路径等。这里都放在用户设置部分。

2>命令勾选部分

因为小工具上传完代码后，需要根据我们勾选的命令，执行不同版本的编译。而且不同的编译命令，需要在不同的服务器上执行，这也是后续代码处理中折磨我好久的东西。

3>运行日志查看部分

运行中肯定是要日志的吗，不论你看或者不看，它都在那里，不增不减。而且万一出错了，这里也要能够打印出trace日志，不然没有日志让我定位，臣妾做不到啊。

## 2.2、界面设计 ##

设计步骤：
>pycharm-tools-extension tools- qt designer

![](/images/posts/python/PuSoftP0.png)

>到此就可以在designer里面设计页面

![](/images/posts/python/PuSoftP1.png)

## 3、如何让小工具显示图标 ##


代码

	class Ui_L3AutoCodeCheck(QtWidgets.QMainWindow):
    	def __init__(self):
        	super(Ui_L3AutoCodeCheck, self).__init__()
        	***省略*****
        	icon = QtGui.QIcon()
        	icon.addPixmap(QtGui.QPixmap("python.ico"), QtGui.QIcon.Normal, QtGui.QIcon.Off)
        	self.setWindowIcon(QtGui.QIcon(':python.ico'))
        	***省略****

重点关注这里的代码，将本地的ico图形文件关联到工具中，这里需要用到extension tools中的pyrcc将ico的文件转换py文件。

>建立img.qry文件

	<!DOCTYPE RCC>
		<RCC>
    	<qresource>
        <file alias="python.ico">python.ico</file>
    	</qresource>
	</RCC>

qt designer中将图片添加到resource中

















