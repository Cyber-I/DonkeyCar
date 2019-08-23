---
ID: 183
post_title: Fabo Donkey Car
author: gameshell_d7l6g7
post_excerpt: ""
layout: page
permalink: https://donkeycar.jp/fabo-donkey-car/
published: true
post_date: 2019-07-07 11:23:44
---
<h1>Fabo Donkey Car</h1>
Donkey Carは, ロボットカーのスタンダードになっているスターターキットだ。

一般販売されているラジコンカーと専用のシャーシ、Raspberry Piとスピードコントローラ、電源コンバーター、そして、Piカメラを搭載。これに、グーグルの機械学習ライブラリTensowFlowを搭載して自動走行させる。

自力でDonkey CarのコアとしてRaspberry Piを利用する場合、さまざまなPythonおよびTensorFlowライブラリをPiでネイティブに動作させるために大変な作業でした。

LinuxおよびPiの専門家によって3年間にわたって慎重に作成された、DonkeyCarに特化したRaspberry Piをディスクイメージを利用するとよい。

とくにGooole Colab に対応した<a href="https://donkeycar.jp/fabo-donkey-car/">Fabo Donkey Car</a>のディスクイメージがお薦めだ。Google Colaboraotoryと連携するために、DonkeyCar 2.5.8, TernsorFlow 2.0.0 Alpha0をインストール、プロジェクトの作成やWireless Joystick、マルチタブ化も実施したRaspberryPi用イメージになります。
<h1>Fabo Donkey Car製作手順</h1>
<div class="md-sidebar md-sidebar--primary" data-md-component="navigation">
<div class="md-sidebar__scrollwrap">
<div class="md-sidebar__inner"><nav class="md-nav md-nav--primary" data-md-level="0">
<ul class="md-nav__list" data-md-scrollfix="">
 	<li class="md-nav__item md-nav__item--active md-nav__item--nested"><nav class="md-nav" data-md-component="collapsible" data-md-level="1">
<ul class="md-nav__list" data-md-scrollfix="">
 	<li class="md-nav__item"><a class="md-nav__link" title="組み立て" href="https://faboplatform.github.io/DonkeyDocs/1.DonkeyCar2%E3%81%AE%E6%A7%8B%E7%AF%89/00.build/">組み立て</a></li>
 	<li class="md-nav__item"><a class="md-nav__link" title="使用ツール" href="https://faboplatform.github.io/DonkeyDocs/1.DonkeyCar2%E3%81%AE%E6%A7%8B%E7%AF%89/01.Tools/">使用ツール</a></li>
 	<li class="md-nav__item md-nav__item--active"><a class="md-nav__link md-nav__link--active" title="RaspPi3用のイメージ作成" href="https://faboplatform.github.io/DonkeyDocs/1.DonkeyCar2%E3%81%AE%E6%A7%8B%E7%AF%89/02.rasppi_allsetting/">RaspPi3用のイメージ作成</a></li>
 	<li class="md-nav__item"><a class="md-nav__link" title="Wifiの設定" href="https://faboplatform.github.io/DonkeyDocs/1.DonkeyCar2%E3%81%AE%E6%A7%8B%E7%AF%89/03.network/">Wifiの設定</a></li>
 	<li class="md-nav__item"><a class="md-nav__link" title="SSHでRaspberryPiのログイン" href="https://faboplatform.github.io/DonkeyDocs/1.DonkeyCar2%E3%81%AE%E6%A7%8B%E7%AF%89/04.ssh/">SSHでRaspberryPiのログイン</a></li>
 	<li class="md-nav__item"><a class="md-nav__link" title="キャリブレーション" href="https://faboplatform.github.io/DonkeyDocs/1.DonkeyCar2%E3%81%AE%E6%A7%8B%E7%AF%89/05.calbration/">キャリブレーション</a></li>
 	<li class="md-nav__item"><a class="md-nav__link" title="教師データの作成" href="https://faboplatform.github.io/DonkeyDocs/1.DonkeyCar2%E3%81%AE%E6%A7%8B%E7%AF%89/06.parent/">教師データの作成</a></li>
 	<li class="md-nav__item"><a class="md-nav__link" title="Colabでの学習(GPU)" href="https://faboplatform.github.io/DonkeyDocs/1.DonkeyCar2%E3%81%AE%E6%A7%8B%E7%AF%89/07.train_colab/">Colabでの学習(GPU)</a></li>
 	<li class="md-nav__item"><a class="md-nav__link" title="自動走行" href="https://faboplatform.github.io/DonkeyDocs/1.DonkeyCar2%E3%81%AE%E6%A7%8B%E7%AF%89/08.autopilot/">自動走行</a></li>
</ul>
</nav></li>
</ul>
</nav></div>
</div>
</div>
<div class="md-content"><article class="md-content__inner md-typeset">
<p id="rasppi3"></p>

</article></div>
<h1>Fabo Donkey Car参考資料</h1>
<ul>
 	<li><a href="https://faboplatform.github.io/DonkeyDocs/">https://faboplatform.github.io/DonkeyDocs/</a></li>
 	<li><a href="https://weekly.ascii.jp/elem/000/000/423/423904/">https://weekly.ascii.jp/elem/000/000/423/423904/</a></li>
</ul>
<h1>Fabo Store</h1>
<ul>
 	<li><a href="https://fabo.store/">https://fabo.store/ </a></li>
</ul>