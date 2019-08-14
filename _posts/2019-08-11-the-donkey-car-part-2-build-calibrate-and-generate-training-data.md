---
ID: 225
post_title: >
  DonkeyCar
  Part2：トレーニングデータの構築、調整、および生成
author: gameshell_d7l6g7
post_excerpt: ""
layout: post
permalink: >
  https://donkeycar.jp/2019/08/11/the-donkey-car-part-2-build-calibrate-and-generate-training-data/
published: true
post_date: 2019-08-11 09:03:13
---
DonkeyCar(ロバ車) Part2：トレーニングデータの構築、調整、および生成
<figure class="jo jp jq jr js dw v w paragraph-image">
<div class="v w jt">
<div class="jw l dg jx">
<div class="jy l"><img class="oe of fl n o fk x fh" src="https://miro.medium.com/max/700/1*-bGQSm7xvbdyZeA5TTVldg.jpeg" width="700" height="525" /></div>
</div>
</div>
<figcaption class="bw du kb kc hb cs v w kd ke br dt" data-selectable-paragraph="">これが私の組み立てられたロバ車です。私が注文したシャーシは注文した3Dパーツに合わなかったので、プレキシガラスを使って即興演奏しなければなりませんでした。</figcaption></figure>
<p id="071e" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">これは、ロバ車の3部構成シリーズのパート2です。これが<a class="bb cn kt ku kv kw" href="https://medium.com/@dmccreary/building-an-ai-community-with-diy-robotics-part-1-the-donkey-car-d285579985f1">パート1</a>と<a class="bb cn kt ku kv kw" href="https://medium.com/@dmccreary/donkey-car-part-3-yes-you-can-learn-autonomous-driving-for-under-250-406f56fa7466">パート3</a>です。では<a class="bb cn kt ku kv kw" href="https://medium.com/@dmccreary/building-an-ai-community-with-diy-robotics-part-1-the-donkey-car-d285579985f1">パート1</a>、私は私の新しいドンキーカーが稼働してラズベリーパイに基づいて、カメラの接続作業を持ってしまったかについて話しました。カメラを<a class="bb cn kt ku kv kw" href="https://elinux.org/RPi-Cam-Web-Interface">RPi Cam Web Interface</a>でテストし、家の1階を<a class="bb cn kt ku kv kw" href="https://elinux.org/RPi-Cam-Web-Interface">走り回っ</a>て車の感触と操作方法を確認しました。</p>

<figure class="jo jp jq jr js dw v w paragraph-image">
<div class="v w kx">
<div class="jw l dg jx">
<div class="ky l">
<div class="cu ju fl n o fk x jf t jv"></div>
<img class="oe of fl n o fk x fh" src="https://miro.medium.com/max/573/1*n3g-PCo_D4EjBgIkN_JZmg.png" width="573" height="298" />

</div>
</div>
</div>
<figcaption class="bw du kb kc hb cs v w kd ke br dt" data-selectable-paragraph="">RPi Cam Webインターフェイスのサンプル画像</figcaption></figure>
<p id="6360" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">このモードでは、PiはWebサーバーの背後にある携帯カメラであり、Webページにビデオ画像を送信していました。RCカーは、同梱されている2.4 Ghzコントローラーによって完全に制御されていました。RPi Cam Web Interfaceソフトウェアを実行するには、Piでターミナルを開き、<a class="bb cn kt ku kv kw" href="https://github.com/silvanmelchior/RPi_Cam_Web_Interface">githubサイト</a>からコードをダウンロードしました。次に、Webサーバーを起動するstartup.shスクリプトを実行しました。</p>
<p id="62f5" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">カメラで画像がキャプチャされてから、Webページで目の前に表示されるまでにどのくらいの遅延があるのか​​興味がありました。遅れは無視できたので、ウェブページの画像を見るだけで車を運転できました。これは、カメラとPi間の入出力が高速であり、WiFiチップを介したWebブラウザーへの画像の変換が高速であることを意味しました。基本的に、リアルタイムのリモートビデオドライビングを行うのに十分な馬力がPiにあることが証明されました。</p>
<p id="3825" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">次に、RCカーに付属の2.4GHzレシーバーからコネクターを取り外し、Amazonに注文した<a class="bb cn kt ku kv kw" href="https://www.amazon.com/HiLetgo-PCA9685-Channel-12-Bit-Arduino/dp/B01D1D0CX2">サーボコントローラーに</a>接続を移動しました。このサーボコントローラーボードは最大16個のサーボを制御するように設計されていますが、必要なサーボは2つだけです。1回はスピードのため、もう1回は車の回転のためです。また、サーボコントローラーからPi 40ピンGPIOバスに4本のワイヤーを接続する必要がありました。これらの接続の写真は次のとおりです。</p>

<figure class="jo jp jq jr js dw v w paragraph-image">
<div class="v w jt">
<div class="jw l dg jx">
<div class="jy l">
<div class="cu ju fl n o fk x jf t jv"></div>
<img class="oe of fl n o fk x fh" src="https://miro.medium.com/max/700/1*h4qiy7XaRDzg61D77xHUKg.jpeg" width="700" height="525" />

</div>
</div>
</div>
<figcaption class="bw du kb kc hb cs v w kd ke br dt" data-selectable-paragraph="">Piとサーボコントローラー間の通信には4本のワイヤが使用されます。黒はアース、赤は+ 5v、黄色とオレンジのワイヤーはSCL（クロック）とSDA（データ）です。サーボコントローラーに明確にラベルが付けられており、Pi GPIOインターフェースでピン配列を確認できます。</figcaption></figure>
<p id="ef0e" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">次のステップは、ステアリングと加速度計のキャリブレーションです。これを行うには、PiにSSH接続してキャリブレーションを実行する必要がありました。Electronic Speed Controller（ESC）の多くは少し異なるため、このプロセスは少し注意が必要です。<a class="bb cn kt ku kv kw" href="http://docs.donkeycar.com/guide/calibrate/">こちら</a>のロバカーサイトに文書化されてい<a class="bb cn kt ku kv kw" href="http://docs.donkeycar.com/guide/calibrate/">ます</a>。私の「STOP」周波数が正しくないため、車を後進させることができないようです。最終的な結果は、スロットルのパラメーターと車のステアリングをエンコードする構成ファイルです。</p>
<p id="874b" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">これが完了したら、テストトラックを回る準備ができました。妻の悔しさの多くに、私は地下の家具を部屋の片側に移動し、地下の床に白い電気テープを置いた。床にクールなエポキシコーティングを施しましたが、白いテープのコントラストは良好でした。</p>

<figure class="jo jp jq jr js dw v w paragraph-image">
<div class="v w jt">
<div class="jw l dg jx">
<div class="jy l">
<div class="cu ju fl n o fk x jf t jv"></div>
<img class="oe of fl n o fk x fh" src="https://miro.medium.com/max/700/1*1X-oJ_LEnhqiUie8VChiDA.jpeg" width="700" height="525" />

</div>
</div>
</div>
<figcaption class="bw du kb kc hb cs v w kd ke br dt" data-selectable-paragraph="">ロバ車のサンプルトレーニングトラック</figcaption></figure>
<p id="9ebd" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">また、床のライトの多くの反射を見ることができます。トレーニングプロセスでは、光の反射を無視し、床の白いテープにのみ「注意」をすることを学ばなければなりません。注意は、ディープラーニングの重要な概念です。</p>
<p id="8bca" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">次に、壁のプラグからPiを取り外し、Amazonで購入した新しい<a class="bb cn kt ku kv kw" href="https://www.amazon.com/gp/product/B06XS9RMWS/ref=oh_aui_detailpage_o01_s00">6800 mAHパワーパック</a>を使用して<a class="bb cn kt ku kv kw" href="https://www.amazon.com/gp/product/B06XS9RMWS/ref=oh_aui_detailpage_o01_s00">電源</a>を入れました。プラットフォームの下にパワーパックを固定するためにテープを使用しました。ESCからのGNDおよびVCCワイヤは、RCカーで使用される2.4GHzレシーバーのデジタル回路に電力を供給することに注意してください。ただし、この電流はPiに電力を供給するのに十分ではありません。テストとして、Piの実行中にUSP電流計を車に接続しました。結果は下の写真にあります：</p>

<figure class="jo jp jq jr js dw v w paragraph-image">
<div class="v w kz">
<div class="jw l dg jx">
<div class="la l">
<div class="cu ju fl n o fk x jf t jv"></div>
<img class="oe of fl n o fk x fh" src="https://miro.medium.com/max/700/1*N-41J0_xTfY7bjVrNcJ1Aw.jpeg" width="700" height="933" />

</div>
</div>
</div>
<figcaption class="bw du kb kc hb cs v w kd ke br dt" data-selectable-paragraph="">写真が撮影されたときに約300mAを描画するPiを示すUSB電流計の画像。実際には、300〜500mAの範囲で、ESPが提供するように設計されたよりもはるかに多くの電流が流れました。</figcaption></figure>
<h1 id="1200" class="lb lc fm bs br gf ld le lf lg lh li lj lk ll lm ln" data-selectable-paragraph="">トレーニングデータの生成</h1>
<p id="2ebf" class="kf kg fm bs kh b ki lo kk lp km lq ko lr kq ls ks" data-selectable-paragraph="">車をすべて組み立てたら、トレーニングデータセットを生成する準備ができています。次に、PiにSSHを実行し、ドライブプログラムを起動しました。</p>
<p id="283d" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph=""><strong class="kh lt">$ python manage.pyドライブ</strong></p>
<p id="da74" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">これは、カメラの内容を表示するWebサーバーを起動するpythonプログラムであり、トレーニングセットをキャプチャするためのコントロールも提供します。ドライブプログラムが実行されたら、任意のWebブラウザーに移動し、ポート8887を使用して車のIPアドレスを入力できます。今度は難しい部分です。トレーニングセットを作成するには、トラックを10回運転しなければなりませんでした！</p>
<p id="40df" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">問題は、キーボードのキーで車を制御することはできましたが、操縦するのが非常に困難だったことです。また、Webインターフェースの「ポインター」を試しましたが、操縦するのも困難でした。最後に、携帯電話を取り出して、電話のブラウザーでドンキーカーのWebページを表示しました。Webブラウザーは、スマートフォンの前方および側方の傾きを検出するのに十分なほどスマートであり、これを速度と回転に変換します。非常に賢い！約1時間の練習で、コースを回ることができました。その後、「記録開始」を押して、約10周後に「記録停止」を押しました。これが完了したら、Donkey CarにSSHで接続し、ディレクトリを「tub」フォルダーに変更しました。そのフォルダーには、約30Kの.jpgおよび.jsonファイルがありました。各JSONファイルには、画像への参照、タイムスタンプ、および浮動小数点数としての加速とステアリングがありました。これはトレーニングデータです。</p>
<p id="a52b" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">JSONファイルのサンプルは次のとおりです。</p>
<p id="09f9" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">{
「user / angle」：0.18989955357142868、
「user / throttle」：0.7175781250000001、
「user / mode」：「user」、
「cam / image_array」：「1000_cam-image_array_.jpg」、
「timestamp」：「2019–01– 05 17：09：35.184483”
}</p>
<p id="ef1c" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">そのJSONファイルに対応する画像を次に示します。</p>

<figure class="jo jp jq jr js dw v w paragraph-image">
<div class="v w lu">
<div class="jw l dg jx">
<div class="jy l">
<div class="cu ju fl n o fk x jf t jv"></div>
<img class="oe of fl n o fk x fh" src="https://miro.medium.com/max/160/1*SuJclI2RBhk7lM2C1dZAdw.jpeg" width="160" height="120" />

</div>
</div>
</div>
<figcaption class="bw du kb kc hb cs v w kd ke br dt" data-selectable-paragraph="">ロバ車を訓練するためのサンプル160X120ピクセル画像</figcaption></figure>
<p id="4c61" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">その後、トレーニングのためにドンキーカーからラップトップに画像をコピーしました。これについては<a class="bb cn kt ku kv kw" href="https://medium.com/@dmccreary/donkey-car-part-3-yes-you-can-learn-autonomous-driving-for-under-250-406f56fa7466">パート3で説明し</a>ます。</p>