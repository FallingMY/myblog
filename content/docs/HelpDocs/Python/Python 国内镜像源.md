---
# type: docs 
title: Python 国内镜像源
date: 2024-07-05T11:34:47+08:00
featured: false
draft: false
comment: true
toc: true
reward: true
pinned: false
carousel: false
series:
  - HelpDocs
categories:
tags: 
  - HelpDocs
  - Python
authors:
  - CSDN_user
images: []
--- 
让 python pip 使用国内镜像源
--------------------

国内镜像源：
------

清华：[https://pypi.tuna.tsinghua.edu.cn/simple](https://pypi.tuna.tsinghua.edu.cn/simple)

阿里云：[http://mirrors.aliyun.com/pypi/simple/](http://mirrors.aliyun.com/pypi/simple/)

中国科技大学 [https://pypi.mirrors.ustc.edu.cn/simple/](https://pypi.mirrors.ustc.edu.cn/simple/)

华中理工大学：[http://pypi.hustunique.com/](http://pypi.hustunique.com/)

山东理工大学：[http://pypi.sdutlinux.org/](http://pypi.sdutlinux.org/)

豆瓣：[http://pypi.douban.com/simple/](http://pypi.douban.com/simple/)

注意：新版 Ubuntu 要求使用https源。

例如：pip3 install -i [https://pypi.doubanio.com/simple/](https://pypi.doubanio.com/simple/) 包名

临时使用：#  
可以在使用pip的时候加参数 -i [https://pypi.tuna.tsinghua.edu.cn/simple](https://pypi.tuna.tsinghua.edu.cn/simple)  
例如：`pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pyspider`，这样就会从清华的镜像去安装pyspider库。

永久修改，一劳永逸：#  
Linux下，修改 ~/.pip/pip.conf (没有就创建一个文件夹及文件。文件夹要加“.”，表示是隐藏文件夹)

内容如下：

```ini
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
[install]
trusted-host=mirrors.aliyun.com
```

windows下，直接在 %userprofile% 目录中创建一个 pip目录，再新建文件 pip.ini。（例如：C:\\Users\\WQP\\pip\\pip.ini）内容同上。

引用：[http://www.cnblogs.com/microman/p/6107879.html](http://www.cnblogs.com/microman/p/6107879.html)

本文转自 <https://www.cnblogs.com/chenjo/p/14071864.html>，如有侵权，请联系删除。