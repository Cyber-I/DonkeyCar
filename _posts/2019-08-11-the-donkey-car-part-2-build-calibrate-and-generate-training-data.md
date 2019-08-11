---
ID: 225
post_title: '驴车：第2部分 &#8211; 构建，校准和生成培训数据'
author: gameshell_d7l6g7
post_excerpt: ""
layout: post
permalink: >
  https://donkeycar.jp/2019/08/11/the-donkey-car-part-2-build-calibrate-and-generate-training-data/
published: true
post_date: 2019-08-11 09:03:13
---
<figure class="kf kg kh ki kj ev v w paragraph-image">
<div class="v w pg">
<div class="kn l ef ko">
<div class="ph l">
<div class="dt kl gi n o gh x bj t km"></div>
<img class="lc ld gi n o gh x ge" src="https://miro.medium.com/max/700/1*-bGQSm7xvbdyZeA5TTVldg.jpeg" width="700" height="525" />

</div>
</div>
</div>
<figcaption class="bu et ks kt hs dr v w ku kv bp es" data-selectable-paragraph="">这是我组装的驴车。我所拥有的chasis不符合我订购的3D部分，所以我不得不用一些有机玻璃即兴创作。</figcaption></figure>
<p id="071e" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">这是关于Donkey Car的3部分系列的第2部分。这是<a class="bx dh kw kx ky kz" href="https://medium.com/@dmccreary/building-an-ai-community-with-diy-robotics-part-1-the-donkey-car-d285579985f1">第1部分</a>和<a class="bx dh kw kx ky kz" href="https://medium.com/@dmccreary/donkey-car-part-3-yes-you-can-learn-autonomous-driving-for-under-250-406f56fa7466">第3部分</a>。在<a class="bx dh kw kx ky kz" href="https://medium.com/@dmccreary/building-an-ai-community-with-diy-robotics-part-1-the-donkey-car-d285579985f1">第1部分中</a>，我谈到了如何基于Raspberry Pi启动并运行新的Donkey Car，并使相机连接正常工作。我用<a class="bx dh kw kx ky kz" href="https://elinux.org/RPi-Cam-Web-Interface">RPi Cam Web界面</a>测试了相机，并在我们家的一楼开车，以感受汽车的感觉以及它如何导航。</p>

<figure class="kf kg kh ki kj ev v w paragraph-image">
<div class="v w pi">
<div class="kn l ef ko">
<div class="pj l">
<div class="dt kl gi n o gh x bj t km"></div>
<img class="lc ld gi n o gh x ge" src="https://miro.medium.com/max/573/1*n3g-PCo_D4EjBgIkN_JZmg.png" width="573" height="298" />

</div>
</div>
</div>
<figcaption class="bu et ks kt hs dr v w ku kv bp es" data-selectable-paragraph="">来自RPi Cam Web界面的示例图像</figcaption></figure>
<p id="6360" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">在这种模式下，Pi只是在Web服务器后面的便携式摄像机，将视频图像传输到其网页。RC汽车完全由汽车附带的2.4 Ghz控制器控制。要运行RPi Cam Web Interface软件，我只需打开Pi上的终端并从<a class="bx dh kw kx ky kz" href="https://github.com/silvanmelchior/RPi_Cam_Web_Interface">github站点</a>下载代码。然后我运行了启动Web服务器的startup.sh脚本。</p>
<p id="62f5" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">我感兴趣的是，相机拍摄的图像与网页上出现的图像之间有多大的延迟。延迟可以忽略不计，这让我只需通过观看网页上的图像来驾驶汽车。这意味着相机和Pi之间的输入/输出速度很快，因为图像通过WiFi芯片转换为Web浏览器。它基本上证明了Pi中有足够的马力来进行实时远程视频驱动。</p>
<p id="3825" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">然后我断开连接器与RC汽车附带的2.4GHz接收器，并将连接移动到我从亚马逊订购的<a class="bx dh kw kx ky kz" href="https://www.amazon.com/HiLetgo-PCA9685-Channel-12-Bit-Arduino/dp/B01D1D0CX2">伺服控制器</a>。虽然这个伺服控制器板设计用于控制多达16个伺服系统，但我们只需要使用两个伺服系统。一次是速度，一次是转弯。我还必须将四条线从伺服控制器连接到Pi 40 Pin GPIO总线。这些连接的照片如下：</p>

<figure class="kf kg kh ki kj ev v w paragraph-image">
<div class="v w pg">
<div class="kn l ef ko">
<div class="ph l">
<div class="dt kl gi n o gh x bj t km"></div>
<img class="lc ld gi n o gh x ge" src="https://miro.medium.com/max/700/1*h4qiy7XaRDzg61D77xHUKg.jpeg" width="700" height="525" />

</div>
</div>
</div>
<figcaption class="bu et ks kt hs dr v w ku kv bp es" data-selectable-paragraph="">四条线用于在Pi和伺服控制器之间进行通信。黑色为地，红色为+ 5v，黄色和橙色线为SCL（时钟）和SDA（数据）。它们在伺服控制器上清晰标记，您可以看到Pi GPIO接口上的引脚分布。</figcaption></figure>
<p id="ef0e" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">下一步是转向和加速度计的校准。要做到这一点，我必须SSH到Pi并运行校准。这个过程有点棘手，因为许多电子速度控制器（ESC）有点不同。据记载毛驴车网站<a class="bx dh kw kx ky kz" href="http://docs.donkeycar.com/guide/calibrate/">在这里</a>。因为我的“停止”频率不正确，我仍然无法让汽车进入倒车状态。最终结果是我们有一个配置文件，可以编码油门的参数和汽车的转向。</p>
<p id="874b" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">一旦完成，我就准备开车绕过测试跑道了。令我妻子懊恼的是，我把地下室的家具搬到了房间的一侧，在地下室的地板上放了一些白色的电工胶带。我们在地板上放了一层很酷的环氧树脂涂层，但白色胶带的对比度很好。</p>

<figure class="kf kg kh ki kj ev v w paragraph-image">
<div class="v w pg">
<div class="kn l ef ko">
<div class="ph l">
<div class="dt kl gi n o gh x bj t km"></div>
<img class="lc ld gi n o gh x ge" src="https://miro.medium.com/max/700/1*1X-oJ_LEnhqiUie8VChiDA.jpeg" width="700" height="525" />

</div>
</div>
</div>
<figcaption class="bu et ks kt hs dr v w ku kv bp es" data-selectable-paragraph="">我的驴车示例训练轨道</figcaption></figure>
<p id="9ebd" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">你还可以看到地板上灯光的很多反射。我们的训练过程必须学会忽略光反射，只能对地板上的白色胶带“注意”。注意力是深度学习的一个重要概念。</p>
<p id="8bca" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">然后，我从墙上插头上取下了Pi，并使用我在亚马逊上购买的新型<a class="bx dh kw kx ky kz" href="https://www.amazon.com/gp/product/B06XS9RMWS/ref=oh_aui_detailpage_o01_s00">6800 mAH电源组</a>为其供电。我用了一些磁带来固定平台下的电源组。我应该注意，来自ESC的GND和VCC导线确实为RC汽车中使用的2.4GHz接收器中的数字电路供电。然而，这个电流不足以为Pi供电。作为测试，我在Pi运行时将USP电流表连接到汽车上。结果如下图所示：</p>

<figure class="kf kg kh ki kj ev v w paragraph-image">
<div class="v w pk">
<div class="kn l ef ko">
<div class="pl l">
<div class="dt kl gi n o gh x bj t km"></div>
<img class="lc ld gi n o gh x ge" src="https://miro.medium.com/max/700/1*N-41J0_xTfY7bjVrNcJ1Aw.jpeg" width="700" height="933" />

</div>
</div>
</div>
<figcaption class="bu et ks kt hs dr v w ku kv bp es" data-selectable-paragraph="">当前拍摄照片时，USB电流表显示Pi绘图约300mA的图像。在实践中，它的电流范围为300至500mA - 比ESP设计提供的电流大得多。</figcaption></figure>
<h1 id="1200" class="pm pn be bq bp hb po pp pq pr ps pt pu pv pw px py" data-selectable-paragraph="">生成培训数据</h1>
<p id="2ebf" class="jr js be bq jt b ju pz jw qa jy qb ka qc kc qd ke" data-selectable-paragraph="">一旦我们将所有汽车组装好，我们就可以生成训练数据集了。然后我做了一个SSH进入Pi并启动了驱动程序：</p>
<p id="283d" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph=""><strong class="jt la">$ python manage.py drive</strong></p>
<p id="da74" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">这是一个python程序，它启动一个Web服务器，显示摄像头上的内容，它还为您提供了一些捕获训练集的控件。一旦驱动程序开始，您可以转到任何Web浏览器并使用端口8887键入您的汽车的IP地址。现在是困难的部分。我不得不在赛道上开车10次以建立一个训练集！</p>
<p id="40df" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">问题是虽然我可以用键盘键控制汽车，但很难驾驶。我也试过网络界面“指针”，但这也很难引导。最后，我拿出手机，在手机浏览器中拉出了Donkey Car的网页。网络浏览器足够智能，可以检测到手机的前倾和侧向倾斜，并将其转换为速度和转弯。非常聪明！通过大约一个小时的练习，我可以绕过课程。然后我按下“开始录音”，大约10圈后我按下“停止录音”。完成此操作后，我可以通过SSH进入Donkey Car并将目录更改为“tub”文件夹。在该文件夹中有大约30K .jpg和.json文件。每个JSON文件都具有对图像的引用以及时间戳，加速和转向作为浮点数。这是我们的培训数据。</p>
<p id="a52b" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">以下是JSON文件的示例：</p>
<p id="09f9" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">{
“user / angle”：0.18989955357142868，
“user / throttle”：0.7175781250000001，
“user / mode”：“user”，
“cam / image_array”：“1000_cam-image_array_.jpg”，
“timestamp”：“2019-01- 05 17：09：35.184483“
}</p>
<p id="ef1c" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">这是与该JSON文件对应的图像：</p>

<figure class="kf kg kh ki kj ev v w paragraph-image">
<div class="v w qe">
<div class="kn l ef ko">
<div class="ph l">
<div class="dt kl gi n o gh x bj t km"></div>
<img class="lc ld gi n o gh x ge" src="https://miro.medium.com/max/160/1*SuJclI2RBhk7lM2C1dZAdw.jpeg" width="160" height="120" />

</div>
</div>
</div>
<figcaption class="bu et ks kt hs dr v w ku kv bp es" data-selectable-paragraph="">样品160X120像素图像用于训练驴车</figcaption></figure>
<p id="4c61" class="jr js be bq jt b ju jv jw jx jy jz ka kb kc kd ke" data-selectable-paragraph="">然后我将Donkey Car中的图像复制到我的笔记本电脑进行培训。我将在第<a class="bx dh kw kx ky kz" href="https://medium.com/@dmccreary/donkey-car-part-3-yes-you-can-learn-autonomous-driving-for-under-250-406f56fa7466">3部分介绍</a>。</p>