---
layout: post
title: PyCharm如何使用Qt Designer
categories: PyCharm
description: PyCharm如何使用Qt Designer
keywords: Python， windows, pycharm
---

Qt Designer 是一个 GUI 设计器，能可视化设计出界面。PyQT5 通过 pyuic5 工具将 Qt Designer 生成的 xxx.ui 文件转换成 python 代码，大大节省手工编写界面代码的工作量。

本篇介绍如何在 PyCharm 中集成 Qt Designer 工具，包括 QT Designer 的配置， pyuic5 的配置和调用界面代码的方法。

pyqt5 可以使用 pip 工具来安装：```

	pip install pyqt5
	
安装了 pyqt5 之后，在 python 安装目录下面的 Scripts 文件夹中，有一个 pyuic5.exe 文件，这个可执行文件用于将 Qt Designer 生成的 ui 文件转换为 python 代码。

##安装 Qt Designer
在 https://build-system.fman.io/qt-designer-download 这个网址可以下载和安装独立的 Qt Designer 安装版，根据操作系统选择合适的安装文件进行安装。

##在 PyCharm 中配置 Qt Designer
Qt Designer 安装后，在安装目录下面有一个 designer.exe 文件。打开该程序，以拖拽的方式设计界面元素。设计完成后保存为 xxx.ui 文件。ui 文件为 xml 格式，用于描述窗体和控件的属性。

在 PyCharm 中配置 Qt Designer，目的是在开发的时候，在 PyCharm 中直接操作 Qt Designer，同时能方便的将 ui 文件保存到 Python 工程指定的文件夹下。通过菜单 File -> Settings 打开如下的配置界面，点击右键 “+” 号配置 Qt Designer:

![](/images/posts/python/pycharmqtd.png)

![](/images/posts/python/pycharmqtd0.png)

左边是配置的路径，右面是配置的参数：
Program： designer.exe 的路径
Working Directory: 设置保存的 UI 文件位置，$FileDir$ 表示文件所在目录。

这个配置适合调用 Qt Designer 新建窗口的情况。如果要对已经创建的 ui 文件进行编辑，为了方便，可以再新建一个配置如下：

![](/images/posts/python/pycharmqtd1.png)

测试一下。比如在 Python 工程中新建一个 designer 文件夹，选中 designer 文件夹

![](/images/posts/python/pycharmqtd2.png)

通过菜单 Tools -> External Tools 菜单打开 qt designer:

![](/images/posts/python/pycharmqtd3.png)

注意这里的 QT Designer Create 和 QT Designer Edit 都是我刚才配置的外部工具。在 Qt Designer 中新建一个 Main Window:

![](/images/posts/python/pycharmqtd4.png)

在 Main Window 中拖拽几个控件。因为本文主要讲解 Qt Designer 的用法，所以对控件的细节不展开。

![](/images/posts/python/pycharmqtd5.png)

然后将界面保存为 MainWindow.ui，路径为 designer 文件夹下面。选中 MainWindow.ui，通过菜单 Tools -> External Tools -> QT Desinger Edit，MainWindow.ui 文件被 Qt Designer 打开。Qt Designer 的配置没有问题。

##如何调用界面代码
ui 转换的 python 代码随着对 ui 的变更，每次都会重新生成，所以不要在 MainWIndow.py 中编写代码。我们需要另外新建一个 python 文件，并在其中编写代码来调用界面代码。

我们看到，qt designer 自动生成的代码实现了一个名为 UI_MainWindow 的类，这个类继承自 object，在该类的 setupUi() 方法中有一个名为 MainWindow 的参数，我们需要将真正的 QMainWindow 对象传给这个方法，来实现我们自己的主窗口。

	from designer.MainWindow import Ui_MainWindow
	import sys
	from PyQt5.QtWidgets import QApplication, QMainWindow

	if __name__ == '__main__':
    # application 对象
    app = QApplication(sys.argv)
    
    # QMainWindow对象
    mainwindow = QMainWindow()
    
    # 这是qt designer实现的Ui_MainWindow类
    ui_components = Ui_MainWindow()
    # 调用setupUi()方法，注册到QMainWindwo对象
    ui_components.setupUi(mainwindow)

    # 显示
    mainwindow.show()

    sys.exit(app.exec_())

	











