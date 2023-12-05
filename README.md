# 学习笔记Web应用程序

## 一、项目概述

该项目是一个基于 Django 框架开发的学习笔记 Web 应用程序。它旨在让用户记录他们感兴趣的主题，并在学习每个主题的过程中添加日志条目。该应用程序的主页描述了网站的功能，并鼓励用户注册或登录。一旦用户登录，他们可以创建新主题、添加新条目以及阅读已有的条目。通过记录学习新主题所掌握的知识，用户可以更好地跟踪和复习这些知识。



## 二、本地运行程序

因为本人学习这个项目在Github上找资料的时候，发现找到的资料不知道怎么在本地运行，所以特加上这一点，希望能让其他人少走弯路。不过这个步骤仅适用于我自己的这个项目哈，因为其他人的项目我也尝试用这个方法运行了，并没有什么用，现在还没有找到解决方法，如果有人知道请告知我。

如果要在本地运行学习笔记Web应用程序，以下是详细的步骤：

### 1. 建立虚拟环境：

首先，建立虚拟环境按照以下步骤进行：

1. 打开命令行（Windows）或终端（MacOS、Linux）。
2. 进入项目目录。
3. 运行以下命令来创建名为 `ll_env` 的虚拟环境：

```bash
python -m venv ll_env
```

### 2. 激活虚拟环境：

进入项目目录后，激活虚拟环境：

- 在 Windows 平台上：

```bash
ll_env\Scripts\activate
```

- 在 MacOS/Linux 平台上：

```bash
source ll_env/bin/activate
```

### 3. 启动项目：

在虚拟环境激活状态下，使用以下命令启动项目：

```bash
python manage.py runserver
```

这将在本地计算机上启动Django服务器。

### 4. 访问应用程序：

在浏览器中输入以下地址来访问应用程序：

```
http://localhost:8000/
```

这是本地服务器的默认地址和端口，可以在浏览器中查看到学习笔记Web应用程序的主页。

### 注意事项：

- 确保在项目目录下执行命令。
- 如果端口8000被其他应用程序占用，可以尝试使用 `python manage.py runserver <port>` 来指定其他端口，例如 `python manage.py runserver 8080`。



## 三、项目搭建过程

由于本人也是第一次尝试做这样比较大型的项目，踩了不少坑，现将踩过的坑和项目搭建过程描述如下，一方面是吃一堑长一智，另一方面是希望能够帮助到接下来要做这个项目的小伙伴。

### 3.1 踩过的坑

- 首先，尽量不要去网上，比如说CSDN上找一些比较久远的教程，计算机行业更迭非常迅速，各工具之间版本也一直在更新，所以版本匹配问题非常关键，很多时候报错是因为版本之间会不兼容或者写法变了。

  - 我一开始是找了CSDN上这篇文章上推荐的教程（因为不想对着书一个个敲代码，而且那个时候老师还没有开始讲这个项目）：[Python编程：从入门到实践项目3总结——Web应用程序_typeerror: url() got an unexpected keyword argumen-CSDN博客](https://blog.csdn.net/weixin_44212573/article/details/121270229?ops_request_misc=%7B%22request%5Fid%22%3A%22170081347816800180620948%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=170081347816800180620948&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-121270229-null-null.142^v96^control&utm_term=Python从入门到实践web应用程序&spm=1018.2226.3001.4187) 

  - 后面发现越写越不对劲，就算对照着写也总有很多错误，去问ChatGPT报错的原因，解释说是因为这种写法已经过时了，类似下图：

  ![image1](img/image1.png)

  

  ![image2](img/image2.png)

  

  - 真的很让人绝望，后来我决定断舍离，全部重新写这个项目，对照着教材上的内容一步步看，确保和教材一模一样，而这个时候，我也发现了老师给的和教材几乎一样的源代码。这时，我的项目才算真正开始。

    老师源代码链接如下：[python_course/src/15-python-web-apps at main · zhoujing204/python_course (github.com)](https://github.com/zhoujing204/python_course/tree/main/src/15-python-web-apps)

  - PS：直到这两天，我才发现，我看的那几篇CSDN博客的文章都是《Python编程从入门到实践》第2版的，而我手上的教材已经到第3版了。（哭）

- 不要想着快速把书上的步骤做完，然后再去理解，一定要边理解边操作。

  - “稳”真的很重要，尤其是像Web应用程序这样需要创建很多文件，并且一步步根据需求改代码的项目。
  - 之前“失败”的那次，我就是有点操之过急，总想着不就是一个个创建文件嘛，文字都不需要看的，我大概都知道，结果看到后面报错的时候一直是懵的，不知道具体是哪里出错了，思路全是混乱的。
  - 就比如说**使用Django创建网页的三大过程：定义URL，编写视图，编写模板**。之前我不理解代码的时候，我就只觉得，怎么这么多操作，写着写着都不知道写哪去了，就很迷惑。
  - 后面我采取了每写一段代码，就把书上的描述文字全看一遍，需要强调的就用黑笔多划几下（甚至挺有成就感的哈哈哈哈），虽然没有我上一次慢，但是思路真的异常清晰，最后直接进度飞快，省去了很多调试错误代码的时间。

- 如果一段代码对照半天连自己都找不出什么问题，可以去问一下人工智能，一下就解决了。

  比如说这个例子，原因就在于我自己都没看出来代码里多了个'd'：

  ![image3](img/image3.png)

  

### 3.2 具体搭建步骤

- 我前面有提到过，首先就是完全对照教材上的步骤来（不过后面事实证明有些内容还是需要看最新的官方文档，比如部署Django应用到platform.sh平台的时候）

- 其次在需要写长段代码的时候，我会复制老师写的源代码以节省时间。不过肯定不是一下把后面的代码也复制下来，我是一步步复制，如果有多的就删掉
- 由于老师给的代码注释是英文的，我会把注释改为书上的中文注释，这样一方面是方便后续的查看，另一方面我也能加深这些模块的印象
- 后面就基本上按照前三步来的，就不细说了，简单来说就是一步步来，遇到bug不要慌，相信自己！！！

再次给上老师的源代码，真的帮了我很多哈哈哈哈：[python_course/src/15-python-web-apps at main · zhoujing204/python_course (github.com)](https://github.com/zhoujing204/python_course/tree/main/src/15-python-web-apps)





