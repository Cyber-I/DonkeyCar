---
ID: 230
post_title: >
  驴车：第3部分
  -是的，你可以学习250美元以下的自动驾驶
author: gameshell_d7l6g7
post_excerpt: ""
layout: post
permalink: >
  https://donkeycar.jp/2019/08/11/donkey-car-part-3-yes-you-can-learn-autonomous-driving-for-under-250/
published: true
post_date: 2019-08-11 09:08:29
---
<div>
<div id="b066" class="it iu ce bc iv b iw ix iy iz ja jb jc"></div>
</div>
<figure class="jt ju jv jw jx ei v w paragraph-image">
<div class="v w px">
<div class="kb l ds kc">
<div class="py l"><img class="mb mc fv n o fu x fr" src="https://miro.medium.com/max/700/1*embz2VLlEt0Z1oe4ij9ZEA.png" width="700" height="500" /></div>
</div>
</div>
<figcaption class="bg eg kg kh hf de v w ki kj bb ef" data-selectable-paragraph=""><span>学习的概念地图驾驶驴汽车。绿色是开始的概念，蓝色的中间和黑色是先进的“整理”概念。</span></figcaption></figure>
<p id="0c35" class="kk kl ce bc km b kn ko kp kq kr ks kt ku kv kw kx" data-selectable-paragraph=""><span>这是系列的第3部分。以下是第</span><a class="bj cu ky kz la lb" href="https://medium.com/@dmccreary/building-an-ai-community-with-diy-robotics-part-1-the-donkey-car-d285579985f1"><span>1</span></a><span>部分和第</span><a class="bj cu ky kz la lb" href="https://medium.com/@dmccreary/the-donkey-car-part-2-build-calibrate-and-generate-training-data-54265797e8c9"><span>2</span></a><span>部分的链接。经过几天的挣扎，我终于让我的驴车在地下室的轨道周围自动驾驶！这里有一个简短的视频：<a class="bj cu ky kz la lb" href="https://www.youtube.com/watch?v=Bpt8NZdQLrU">https</a>：</span><a class="bj cu ky kz la lb" href="https://www.youtube.com/watch?v=Bpt8NZdQLrU"><span>//www.youtube.com/watch？v = Bpt8NZdQLrU</span></a></p>
<p id="86c9" class="kk kl ce bc km b kn ko kp kq kr ks kt ku kv kw kx" data-selectable-paragraph=""><span>所以这就是让我失望的原因。当我将我的模型从我的Mac上传到Pi并运行“驱动器”命令时，加载模型时出错。我一直在重新运行这些步骤并得到了同样的错误。我花了几天才意识到我在Donkey Car上运行</span><strong class="km ly"><span>旧版</span></strong><span>TensorFlow（1.8）和</span><strong class="km ly"><span>更新版本</span></strong><span>我的MacBook Pro上的TensorFlow 1.12版本。我还在Donkey Car帮助Slack频道上发布了一个问题，他们在使用较新的TensorFlow版本1.12构建的模型上确认不会在较旧版本的TensorFlow上运行。一旦我弄清楚如何在我的Mac上降级TensorFlow（一线pip shell命令），我重新训练，用SCP将我的新模型转移到Pi，我的车开始运行......那是在我意识到我之后将相机镜头盖打开......</span></p>
<p id="3436" class="kk kl ce bc km b kn ko kp kq kr ks kt ku kv kw kx" data-selectable-paragraph=""><span>我从一个约16K图像的相对较小的训练集开始。TensorFlow 1.12的训练时间为55分钟，TensorFlow </span><a class="bj cu ky kz la lb" href="https://github.com/tensorflow/tensorflow/releases/tag/v1.8.0"><span>1.8的</span></a><span>时间为75分钟。1.8发布于2018年4月。让我们希望DonkeyCar图像很快升级，这样我们都可以利用这些性能改进！我也只是在赛道周围逆时针方向使用了一套测试装置。在真正的比赛中，我会用顺时针和逆时针方向训练赛车。但这也会增加构建模型的时间。</span></p>
<p id="4321" class="kk kl ce bc km b kn ko kp kq kr ks kt ku kv kw kx" data-selectable-paragraph=""><span>虽然汽车可以绕过轨道，但很容易被地板上的灯光和侧面的其他白色物体的反射所欺骗。这是因为我在地板上只使用了一条白色胶带。这对视觉系统来说还不够用。但是，我不认为我的妻子真的要我画一条宽大的黑色“道路”，中间有黄色条纹，就像官方的Donkey Car轨道一样。</span></p>
<p id="ecbe" class="kk kl ce bc km b kn ko kp kq kr ks kt ku kv kw kx" data-selectable-paragraph=""><span>当我终于让汽车在自动模式下工作时，它非常令人满意。但是也有点“怪异”。我实际上“教”了一个小大脑来跟随地板上的线。它几乎似乎模仿我糟糕的驾驶。它甚至学会了如何在直道上加速，并且在紧凑的曲线上减速。真的很酷！</span></p>
<p id="193f" class="kk kl ce bc km b kn ko kp kq kr ks kt ku kv kw kx" data-selectable-paragraph=""><span>虽然我在TensorFlow和Keras的工作中做过一些工作，但很多步骤都有点抽象。一旦我开始玩驴车，事情就更容易理解了。系统的优势及其弱点都变得清晰。我还意识到，在训练系统（我的MacBook）和推理系统（Pi）之间同步Python和TensorFlow库是一个关键步骤。</span></p>
<p id="691c" class="kk kl ce bc km b kn ko kp kq kr ks kt ku kv kw kx" data-selectable-paragraph=""><span>在完成所有步骤后，我现在了解了大部分组件，并且我正在构建一个“概念图”，其他人可以使用它来帮助理解他们需要知道什么概念才能让他们的Donkey Car运行。</span></p>
<p id="b5ce" class="kk kl ce bc km b kn ko kp kq kr ks kt ku kv kw kx" data-selectable-paragraph=""><span>我现在正在回顾我学到的所有步骤，并将这些步骤与我为当地CoderDojo俱乐部制作概念卡的先前工作相结合。这是博客文章顶部的数字。概念图中的每个方框最终将成为1/2张层压纸，正面有活动和问题，背面有答案。这些在CoderDojo中被称为“寿司卡”，因为它们是比特大小的学习点。以下是“电动机”概念卡的示例图像：</span></p>

<figure class="jt ju jv jw jx ei v w paragraph-image">
<div class="v w pz">
<div class="kb l ds kc">
<div class="qa l">
<div class="dg jz fv n o fu x jk t ka"></div>
<img class="mb mc fv n o fu x fr" src="https://miro.medium.com/max/635/1*MAG7wAuHnkkdZGR1SSGgdg.png" width="635" height="476" /></div>
</div>
</div>
<figcaption class="bg eg kg kh hf de v w ki kj bb ef" data-selectable-paragraph=""><span>AI赛车联盟的电动概念卡。</span></figcaption></figure>
<p id="e05c" class="kk kl ce bc km b kn ko kp kq kr ks kt ku kv kw kx" data-selectable-paragraph=""><span>我的朋友Jon Herke也有兴趣使用Donkey Cars建立一个“AI赛车联盟”，旨在教孩子们关于人工智能和机器人技术。请继续关注我们是否可以为hackdays建立一个基础和一个为期10周，每周4小时的夏令营类型计划。我们希望让女孩和弱势青年参与这些计划。如果您有兴趣帮助我们入门，请告诉我们。</span></p>