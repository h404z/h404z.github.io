---
title: mac+pycharm+pyqt开发环境准备
date: 2019-03-24 22:26:22
tags: pyqt
---



pyqt的搭建过程遇到不少问题，简单记录下方便日后部署。

1. mac自带的是python2.7，似乎pyqt5只支持python3，由于不想重新编译pyqt5的源码（需要解决各种报错和依赖），遂安装python3.7 <https://www.python.org/getit/>

2. pyqt的安装方式很多，尝试从官网下载安装包，但多次出现网络访问问题，最后改用pip，完成安装

   > pip3 install pyqt5

3. pyqt安装完成后，import一下确认安装ok

   ![](https://ws2.sinaimg.cn/large/006tKfTcgy1g1ea8ocfihj30eb030q34.jpg)

4. 在pycharm配置designer和uic，方便调用

   1. designer

      ![](https://ws3.sinaimg.cn/large/006tKfTcgy1g1eamixwl6j30eg09smy4.jpg)

      Program:`/usr/local/Cellar/qt/5.12.1/libexec/Designer.app`

   2. uic

      ![](https://ws1.sinaimg.cn/large/006tKfTcgy1g1eao3m12mj30ek09s75b.jpg)

      Program:`/Library/Frameworks/Python.framework/Versions/3.7/bin/pyuic5`

      Arguments:`$FileName$ -o $FileNameWithoutExtension$.py`

5. 简单写个hello world把`designer生成ui文件 -> uic把ui文件转化成py文件 -> 运行程序显示控件`整个流程跑起来。

   ![](https://ws4.sinaimg.cn/large/006tKfTcgy1g1eaugog43j30q407dgmz.jpg)

   ![](https://ws2.sinaimg.cn/large/006tKfTcgy1g1ebaoukr1j30hx06smxb.jpg)

   ```python
   import sys
   
   import hello_world
   from PyQt5.QtWidgets import QApplication, QMainWindow
   
   if __name__ == '__main__':
       app = QApplication(sys.argv)
       MainWindow = QMainWindow()
       ui = hello_world.Ui_MainWindow()
       ui.setupUi(MainWindow)
       MainWindow.show()
       sys.exit(app.exec_())
   ```

   