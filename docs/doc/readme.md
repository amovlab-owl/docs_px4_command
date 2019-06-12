# 关于sphinx + github + read the docs 协作文档的介绍

### sphinx
sphinx是python官方文档生成工具，具有可根据 rst / md 文件生成在线文档，并带有自动化索引的功能。

### read the docs
该网站是一个在线开放的文档平台，它具有监听git仓库变化，及时更新文档的功能，并且提供自动化sphinx文档生成。

# 协作文档建立

### 创建带有build文件夹的git工程
在本地创建git仓库，或从github拉取仓库后，在仓库隐藏文件夹 .gitignore 下创建 build 文件夹。

### 创建该项目的文档
在项目目录下，创建 docs文件夹，并将示例文件拷贝至 docs目录下。
该目录是read the docs 的规范文件夹，它是文档书写的文件夹，整个文档都需要写在该文件夹下。

### 上传git仓库至github

### read the docs 创建在线项目文档

进入 https://readthedocs.org 网站，登录或注册账号

选择 import project 创建一个新的项目文档

选择 github类型
第一次使用会要求登录github账号，之后会直接显示github账号内的仓库。

选择我们的工程项目，就创建成功了该项目的在线文档

read the docs 会读取项目下的docs文件夹，并自动编译为在线文档。同时，它也会监听github是否有更新，一旦仓库更新，它会主动更新该文档。

# 创建后使用

当文档创建完毕，普通用户书写文档只需要在docs目录下进行操作，使用 rst 或 md 文件进行编辑即可，推送至github，则文档就会同步更新

# 文档书写

### rst文件书写
当前只使用 index.rst 作为目录，其他文件建议使用md格式编写

#### index.rst
```

Welcome to amov's documentation!
================================ //此处表示左侧的一个1级分类


二级分类
-----------    //左侧的二级分类

.. toctree::  //目录树形结构的标志
   :maxdepth: 2 //表示从该分类下的文档中读取几级目录 1 表示 只读取 一级目录

   hello  //引入的md文档文件，可以不加 .md的后缀。 这里表示引入同级目录下的hello文件，并读取 一级目录作为主页展示目录。这里也可以书写 如 test/index ，表示读取目录 test下的index.md文件作为文档

```

这里注意，一定要在分类/配置属性结构/引入文档处上下预留空行。

# 改变文档样式

在conf.py文件中
找到 
html_theme = 'sphinx_rtd_theme'
后面的值就是选择的样式，可以根据sphinx文档进行更改