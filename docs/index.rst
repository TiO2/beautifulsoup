.. BeautifulSoup文档 documentation master file, created by
   delong wang on Fri Nov 29 13:49:30 2013.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Beautiful Soup 4.4.0 文档 这是个测试 
=====================================

`Beautiful Soup <http://www.crummy.com/software/BeautifulSoup/>`_ 是一个可以从HTML或XML文件中提取数据的Python库.它能够通过你喜欢的转换器实现惯用的文档导航,查找,修改文档的方式.Beautiful Soup会帮你节省数小时甚至数天的工作时间.

这篇文档介绍了BeautifulSoup4中所有主要特性,并且有小例子.让我来向你展示它适合做什么,如何工作,怎样使用,如何达到你想要的效果,和处理异常情况.

文档中出现的例子在Python2.7和Python3.2中的执行结果相同

你可能在寻找 `Beautiful Soup3 <http://www.crummy.com/software/BeautifulSoup/bs3/documentation.html>`_ 的文档,Beautiful Soup 3 目前已经停止开发,我们推荐在现在的项目中使用Beautiful Soup 4, `移植到BS4 <http://www.baidu.com>`_

这篇帮助文档已经被翻译成了其它语言:

寻求帮助
--------

如果你有关于BeautifulSoup的问题,可以发送邮件到 `讨论组 <https://groups.google.com/forum/?fromgroups#!forum/beautifulsoup>`_ .如果你的问题包含了一段需要转换的HTML代码,那么确保你提的问题描述中附带这段HTML文档的 `代码诊断`_ [1]_

快速开始
========

下面的一段HTML代码将作为例子被多次用到.这是 *爱丽丝梦游仙境的* 的一段内容(以后内容中简称为 *爱丽丝* 的文档):

::

    html_doc = """
    <html><head><title>The Dormouse's story</title></head>
    <body>
    <p class="title"><b>The Dormouse's story</b></p>

    <p class="story">Once upon a time there were three little sisters; and their names were
    <a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>,
    <a href="http://example.com/lacie" class="sister" id="link2">Lacie</a> and
    <a href="http://example.com/tillie" class="sister" id="link3">Tillie</a>;
    and they lived at the bottom of a well.</p>

    <p class="story">...</p>
    """

使用BeautifulSoup解析这段代码,能够得到一个 ``BeautifulSoup`` 的对象,并能按照标准的缩进格式的结构输出:

::

    from bs4 import BeautifulSoup
    soup = BeautifulSoup(html_doc, 'html.parser')

    print(soup.prettify())
    # <html>
    #  <head>
    #   <title>
    #    The Dormouse's story
    #   </title>
    #  </head>
    #  <body>
    #   <p class="title">
    #    <b>
    #     The Dormouse's story
    #    </b>
    #   </p>
    #   <p class="story">
    #    Once upon a time there were three little sisters; and their names were
    #    <a class="sister" href="http://example.com/elsie" id="link1">
    #     Elsie
    #    </a>
    #    ,
    #    <a class="sister" href="http://example.com/lacie" id="link2">
    #     Lacie
    #    </a>
    #    and
    #    <a class="sister" href="http://example.com/tillie" id="link2">
    #     Tillie
    #    </a>
    #    ; and they lived at the bottom of a well.
    #   </p>
    #   <p class="story">
    #    ...
    #   </p>
    #  </body>
    # </html>
    
    
