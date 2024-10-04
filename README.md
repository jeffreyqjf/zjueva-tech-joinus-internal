# 技术小组纳新试题

以下共有8题，题目难度和类型也不相同，你可以按照自己的情况选取若干题目完成，三至四题即可。其中第0题包含了题目解答上传的途径，因此必须完成。在解题过程中，你可以搜索相关资料，但请不要与其他人交流。

这些题目旨在了解各位的即时学习能力以及面向文档的学习能力，每道题目对于你来说都可能是完全陌生的，我们不需要你有多么优秀的基础，但我们欣赏你努力解题的过程。

如果在努力尝试后仍未能完全解答，可以谈一谈你对这些题目的理解，也可以将你对题目的探索过程作为附件提交，我们会酌情加分。

技术小组的纳新提交将于2024年10月18日23:59截止，逾期不候哦\~

**Have fun coding\~**

# 0. 来签到啦！- Git

作为一位（准）开发人员，你会遇到很多很多与他人合作完成项目的场景。你也许听说过“这个项目我Fork了”“这个项目我Star了”“我提交了一个PR”这样的说法，其实这都与Git息息相关。

Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。它是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

### 你的任务

1.  新建一个Git远程仓库，并保证技术小组管理员可以访问到你的仓库，托管平台不限。
2.  使用你的学号作为密钥，将管理员发送给你的一串密文进行解密，并将解密结果放在一个文本文件里，和其他题目的作答分别放在以题目序号命名的文件夹中，推送到你自己的远程仓库。文件格式不限。
3.  技术小组的纳新试题也会同步放在ZJU Git,Github以及Gitea托管平台，当你完成时，请在纳新试题仓库提出issue，并附上你的个人仓库链接。

### 明文的加密过程

1.  明文固定4位，密钥固定学号后4位
2.  将明文与学号对应位置的字符先转化为整数，再相乘，将结果转换为16进制
3.  将4个独立的运算结果之间以`"/"`分割，再整合为一个字符串（密文）
4.  如果搞不清楚这个运算过程，下面有一个利用Python实现的加密示例：

```python
# 明文固定4位，密钥为你的学号后4位
encrypt = lambda clear, key: "".join([hex(ord(clear[i]) * ord(key[i]))[2:] + '/' for i in range(4)])[:-1]

```

你可能会用到的Git命令：

-   `git init`：在当前目录初始化Git仓库
-   `git add . `：将当前目录下所有文件加入暂存区
-   `git commit -m "xxx"`：提交暂存区的更改，并附加评论“xxx”
-   `git push`：将本地仓库的更改推送到远程仓库
-   `git clone https://xxxx`：将\[URL]的仓库克隆到本地

### 附加题

-   请简单解释一下这个函数是如何只用一行代码就完成工作的。它们还能再简化吗？

如果你实在无法通过Git将代码上传到你的个人仓库，请于2024年10月18日23:59之前打包发送到jeffreyqjfing\@gmail.com，邮件标题格式为 **姓名-学号-部门-技术小组纳新**。

### 参考资料

-   [Git](https://git-scm.com/ "Git")
-   [Learn Git Branching](https://learngitbranching.js.org/?locale=zh_CN "Learn Git Branching")
-   [ZJU Git](https://git.zju.edu.cn/ "ZJU Git")
-   [Python入门](https://www.runoob.com/python/python-tutorial.html "Python入门")

# 1.原来是拟合 - Pytorch
在大家写实验报告的时候不可避免的会遇到拟合实验数据的曲线，小钱同学由于不会使用Excel拟合曲线，导致每次实验报告都被打低分。他下定决心要找出能最好拟合实验数据的曲线，于是他想到了神经网络...

### 你的任务
现在，请你使用pytorch设计并训练一个神经网络，可以拟合实验数据的一系列点，例如符合 `y = 3x ± 0.5` 分布的一系列散列的点，要求：

-  需要提供训练代码和神经网络的模型结构代码，并将训练完成的模型保存为xx.pt的文件附在一起提交。
-  需要提供神经网络在你所选定的一个线性或非线性的函数上的最终训练效果的图片，即数据点和曲线绘制在一张图上（建议使用matplotlib等绘图工具）。

### 一些可能有助于完成项目的小提示：
-  本次任务并不需要用到卷积（Convolution），池化（Pooling）等操作，需要的仅仅是线性层（Linear）和激活函数。
-  pytorch简单入门可以参考这个文章：
[https://pytorch.ac.cn/tutorials/beginner/basics/intro.html](https://pytorch.ac.cn/tutorials/beginner/basics/intro.html "https://pytorch.ac.cn/tutorials/beginner/basics/intro.html")
### 附加题
1. 训练一个卷积神经网络，数据集为MINST数据集（需自行下载），识别的准确率需要达到80%以上，提供内容同上，将原来训练效果的图片改为准确率的截图。
2. 试试不依赖神经网络, 编写 Python 代码用传统的统计方法拟合实验数据, 并讨论一下这种方法与使用神经网络进行拟合的区别。

# 2.网络蜘蛛侠 - spider
小钱同学是一个医学专业的小e，很多时候需要搜索文献，但是人工手动搜索文献效率太低了，小钱同学就想着能不能通过一个自动程序来将相关的搜索结果以 **文献标题：文献链接** 保存为为一个.txt的文件中。

### 你的任务
-  将[Nature](https://www.nature.com/ "Nature")上的文章的文献标题和文献链接保存下来，比如 
```text
Fratricide-resistant CD7-CAR T cells in T-ALL : https://www.nature.com/articles/s41591-024-03228-8

A CAR enhancer increases the activity and persistence of CAR T cells : https://www.nature.com/articles/s41587-024-02339-4
```
这样两行，搜索的关键词可以自定义，如`CAR-T`。
-  你所需要提交的包括一个.txt文件和相应的源代码（建议使用python）。

### 一些可能有助于完成项目的小提示：
-  某些网站可能存在反爬虫的策略，为了更好的得到数据，可以使用chromedriver + python中的`selenium`包 来模仿用户行为，selenium相关教程可以参考[这个网站](https://selenium-python-zh.readthedocs.io/en/latest/getting-started.html "这个网站")。
-  Nature的web源代码可能比较多，可以在查看网页源代码的同时使用ctrl + F 来搜索自己感兴趣的的地方（比如网址）。
-  在page source 中获取自己感兴趣的内容（文献标题与文献链接），可以使用 `BeautifulSoup` 包来解析，也可以使用正则表达式来匹配，BeautifulSoup相关教程可以参考[这个网站](https://beautifulsoup.readthedocs.io/zh-cn/v4.4.0/ "这个网站").

### 附加题
1. 实现从一页相关的搜索结果拓展到10页，将10页中的`文献标题：文献链接`内容都下载下来。
2. 实现不仅仅只获取文献链接，将文献链接所指的PDF也下载到本地。