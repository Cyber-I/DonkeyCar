---
ID: 218
post_title: '用DIY机器人构建AI社区：第1部分 &#8211; 驴车'
author: gameshell_d7l6g7
post_excerpt: ""
layout: post
permalink: 'https://donkeycar.jp/2019/08/11/%e7%94%a8diy%e6%9c%ba%e5%99%a8%e4%ba%ba%e6%9e%84%e5%bb%baai%e7%a4%be%e5%8c%ba%ef%bc%9a%e7%ac%ac1%e9%83%a8%e5%88%86-%e9%a9%b4%e8%bd%a6/'
published: true
post_date: 2019-08-11 08:52:15
---
Using DIY Robotics to Build an AI Community

使用DIY机器人构建AI社区
<p id="41ba" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">This is the first in a 3-part series on the Donkey Car. Here are links to <a class="bx dh kw kx ky kz" href="https://medium.com/@dmccreary/the-donkey-car-part-2-build-calibrate-and-generate-training-data-54265797e8c9">part 2</a>and <a class="bx dh kw kx ky kz" href="https://medium.com/@dmccreary/donkey-car-part-3-yes-you-can-learn-autonomous-driving-for-under-250-406f56fa7466">part 3</a>.</p>
这是关于Donkey Car的3部分系列中的第一部。以下是第2部分和第3部分的链接。

（https://medium.com/@dmccreary/building-an-ai-community-with-diy-robotics-part-1-the-donkey-car-d285579985f1）
<div class="kp l"><img class="lc ld gi n o gh x ge" src="https://miro.medium.com/max/700/1*Sg5cuLqFufM0IX4nZd9bMA.png" width="700" height="327" /></div>
我已经通过CoderDojo计划建立了用于教孩子计算机科学近四年的机器人。这是一次有益的经历，我学到了很多关于构建Arduino套件和简单机器人的知识。我一直在为8-18岁的孩子创造“学习阶梯”，而我的机器人则被5岁以下的儿童在The Works Museum使用。围绕DIY项目构建STEM课程很有趣，也是寻找社区的好方法。你可以在Moving Rainbow和CoderDojo Robots网站上看到我的一些工作。

随着新的一年，我决定扩展我的舒适区，包括基于Raspberry Pi，Python和机器学习的更复杂的机器人。我的朋友Arun Batchu也通过购买非常酷的NVIDIA Jetson Xavier开发套件来鼓励这一点。不幸的是，我的小机器人不足以运行这个价值90亿的晶体管系统。我认为这对我来说是一个很好的方式来了解最新的图像识别和边缘计算的热门话题。建立一个本地DIY机器人小组也是在明尼阿波利斯地区建立一个更强大的AI社区的一种方式。

对于那些不熟悉Donkey Car项目的人来说，它是一个开源DIY项目，让人们学习实时图像识别和一些AI的基础知识。这辆车的零件大约250美元。这比我的Arduino机器人贵10倍，但它也更强大。在湾区，有超过2,500人参加了DIY Robocars聚会，Donkey Car Slack工作区几乎有多少人在汽车，赛道，算法，机器学习模型和相关主题上有数千个帖子。我们在明尼苏达州还没有像这样的社区，但我希望改变这个！

以下是我开始制作驴车的工作日记。所以他们说...我们参加了比赛！

我在Swarm64的伟大人物的最后一次MinneAnalytics会议上“天赋”了一个Raspberry Pi 3 B + Kit，其中包括Paul McCullugh和Thomas Richter。 Swarm64使用FPGA为RDBMS系统提供了出色的加速器。如果你需要一个更快的关系数据库给他们一个电话！

Raspberry Pi套件包括带有PI OS的32GB micro SD卡，电源砖，GPIO分线器以及外壳以及其他一些部件。我添加了一个27美元的SainSmart广角鱼眼摄像头和一个PCA9685 16通道12位PWM伺服电机驱动器以及一辆新的90美元RC车（我还没有测试过）。我使用GPIO使用Thonny Python IDE对LED进行了闪烁测试，并找到了用于控制LED灯条的DMA库。我还在圣路易斯公园的Microcenter购买了两张额外的32GB SD卡，每张4.99美元。这比我在亚马逊上找到的要少。微中心真的很摇滚！我建议你买几张微型SD卡，这样你就可以进行备份了。

在Arduino的“C / C ++”工作多年之后，我对Pi开始的难度感到有些惊讶。有许多库需要以正确的顺序安装，需要考虑许多版本的Python。 Thonney Python IDE很不错，但它缺少我们需要用TensorFlow认真工作的大多数库。好消息是，一旦库设置编码变得非常快。如果您正在使用物理设备进行硬件编程，那么当您对代码进行更改并且必须将其上传到Arduino时，就没有“滞后”。程序立即运行！我认为这可以加快开发速度，特别是当你有大型程序时。

现在进入Donkey Car ... Donkey Car网站做得非常好，但它假设UNIX和Pi的背景非常强大。当他们发出指示时，我不清楚我应该在我的新Pi或远程计算机上运行。我花了大约两天时间试图让各种Python和TensorFlow库在Pi上本地工作。虽然我在进步中学到了很多东西，但事实证明这是一个死路一条。只有2GB或RAM的Pi太小，无法在没有英勇努力的情况下编译大规模的TensorFlow-Keras系统。即使在具有16GB内存的Mac上，我也遇到了基于Bazel的TensorFlow编译系统的bug。 Bazel构建框架本身非常复杂，您需要Bazel来编译TensorFlow怪物。做只是没有削减它。我正要放弃。如果像我这样拥有25年UNIX经验的人无法安装这个东西，我怎么能希望培养我14岁的学生呢？

然后我开始意识到，在Donkey汽车上完成的所有事情都假设了一个无头Pi（没有监视器，只是一个SSH访问），并使用他们的磁盘映像，这些映像由Linux和Pi专家精心制作了三年。你需要启动他们的Pi图像，其他一切都有效！你不能将Pi用作开发系统。 TensorFlow文档确实这样说，但我没有RTFM。

我努力了解如何基于Donkey图像（包含磁盘映像的zip文件）为Pi构建启动映像。在尝试了NOOBS系统后，我意识到balenaEtcher应用程序正是我所需要的。该应用程序在Windows或Mac上使用非常简单。您只需从Donkey Car网站下载图像zip文件，将新SD卡放入并运行belenaEtcher应用程序。它会提示您输入图像文件（无需解压缩zip文件），它会自动找到SD驱动器然后我点击“Flash”。噗！在短短几分钟内，我就有了经过验证的磁盘映像。

重新启动新SD到我的Pi后，我可以登录并更改wifi设置。再一次重启，我准备好进入我的新驴车。我还设置了静态IP地址，因此每次都会重新连接到同一个IP地址。 “/ home / pi / env”目录下的文件计数显示了近13,000个文件。如果您需要所有血腥的详细信息，请将其放入已启用评论的Google文档文件中。随意为该文件添加注释。

我将在发布更新时发布更新，并在其他部分到达后发布。我需要它们来做校准步骤。
<div id="extensionsWeblioEjBx" style="position: absolute; z-index: 2147483647; left: 189px; top: 104px;"></div>