---
layout: post
title: 如何将PyQt（pyqt-tools）中的Qt Designer改为中文界面（汉化）
categories: Python
description: 如何将PyQt（pyqt-tools）中的Qt Designer改为中文界面（汉化）
keywords: Python， windows， PyQt5(designer)
---

##如何将PyQt（pyqt-tools）中的Qt Designer改为中文界面（汉化）

首先直接用pip安装的PyQt-tools的Designer和windows执行程序安装的Designer，是不带翻译文件的，因此我们要把Qt creator中Designer的翻译文件拷贝到Pyqt的Designer目录中。

步骤1
打开Qt creator的translations文件夹。

笔者的路径：F:\Qt\Qt5.11.1\Tools\QtCreator\share\qtcreator\translations

![](/images/posts/python/python-PyQt.png)

步骤2
把其中一个文件拷贝，designer_zh_CN.qm是简体中文，designer_zh_TW.qm是繁体中文，这里我们拷贝简体中文的翻译文件。

![](/images/posts/python/python-PyQt0.png)

>Ps：不想下载Qt但是又想要designer_zh_CN.qm这个翻译文件的，笔者提供下载地址如下：



####请关注本人公众号：吾爱分享派，回复：“designer汉化文件“获取下载地址 ###



步骤3
将拷贝的翻译文件复制到 PyQt5 的translations文件夹中

笔者的路径：F:\Python\Lib\site-packages\PyQt5\Qt\translations

![](/images/posts/python/python-PyQt1.png)

步骤4
将拷贝的翻译文件复制到 pyqt5-tools 的translations文件夹中

笔者的路径：F:\Python\Lib\site-packages\pyqt5-tools\translations

![](/images/posts/python/python-PyQt2.png)

最终结果
此时打开PyQt5的designer就会发现界面变成中文的了。

![](/images/posts/python/python-PyQt3.png)
