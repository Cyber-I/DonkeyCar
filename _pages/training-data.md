---
ID: 313
post_title: Training Data
author: gameshell_d7l6g7
post_excerpt: ""
layout: page
permalink: https://donkeycar.jp/training-data/
published: true
post_date: 2019-08-21 13:47:35
---
車のフォルダーを開き、車を起動します。
<pre><code class="hljs bash"></code></pre>
<pre><code class="hljs bash"><span class="hljs-built_in">cd</span> ~/mycar
python manage.py drive</code></pre>
<pre><code class="hljs bash"></code></pre>
このスクリプトは、車を制御するためのWebサーバーである部分を含む車のドライブループを開始します。

次のURLのWebブラウザーから車を制御できるようになりました：

&lt;あなたの車のIPアドレス&gt;：8887

&nbsp;

<img src="https://donkeycar.jp/wp-content/uploads/2019/08/drive_UI.png" alt="drive UI" />
<h2>Web Controllerを使用した運転</h2>
お使いの携帯電話では、スタートボタンを押して、現在の携帯電話の傾きをゼロスロットルとステアリングに設定できます。 スマートフォンを前方に傾けるとスロットルが増加し、左右に傾けるとステアリングが回転します。
<h3>特徴</h3>
<ul>
 	<li>     記録-記録データを押して、画像、ステアリングエンジェル、スロットル値の記録を開始します。</li>
 	<li>     スロットルモード-スロットルを一定に設定するオプション。 これは、操縦するがスロットルを制御しないパイロットがいる場合にレースで使用されます。</li>
 	<li>     パイロットモード-パイロットが角度やスロットルを制御する必要がある場合は、これを選択します。</li>
 	<li>     最大スロットル-最大スロットルを選択します。</li>
</ul>
<h3>キーボードショートカット</h3>
<ul>
 	<li>     スペース：車を止めて記録を止める</li>
 	<li>     r：記録を切り替える</li>
 	<li>     i：スロットルを上げる</li>
 	<li>     k：スロットルを下げる</li>
 	<li>     j：左に曲がる</li>
 	<li>     l：右折</li>
</ul>
&nbsp;
<h2>ゲーム Joystick Controllerを使用した運転</h2>
LogiCoolゲームコントローラのUSBドングルを接続
$ ls /dev/input
js0 があればOK
$ hexdump /dev/input/js0
ボタン類を操作して16進の数値が表示されればOK
ctrl＋cで終了

LogiCoolコントローラ用に以下のファイルを差し替える
~/donkeycar/donkeycar/parts/controller.py

ゲームコントローラのボタン類の割り当ては以下の通り
<a href="https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.amazonaws.com%2F0%2F263672%2F981d589c-b147-4119-b588-86bcfed771b1.jpeg?ixlib=rb-1.2.2&amp;auto=compress%2Cformat&amp;gif-q=60&amp;s=3cef7f77550b4176e02cea378c143337" target="_blank" rel="nofollow noopener noreferrer"><img class="" src="https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.amazonaws.com%2F0%2F263672%2F981d589c-b147-4119-b588-86bcfed771b1.jpeg?ixlib=rb-1.2.2&amp;auto=compress%2Cformat&amp;gif-q=60&amp;s=3cef7f77550b4176e02cea378c143337" srcset="https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.amazonaws.com%2F0%2F263672%2F981d589c-b147-4119-b588-86bcfed771b1.jpeg?ixlib=rb-1.2.2&amp;auto=compress%2Cformat&amp;gif-q=60&amp;w=1400&amp;fit=max&amp;s=eae285bbc8d6f8cdd59f6c4e30d48a66 1x" alt="logicool.jpg" width="736" height="369" data-canonical-src="https://qiita-image-store.s3.amazonaws.com/0/263672/981d589c-b147-4119-b588-86bcfed771b1.jpeg" /></a>

コントローラにJC-U3912TまたはJC-VRP-01を使用する場合はmanage.pyファイル28行目の「controller_logicool」を「controller_elecom_usb」または「controller_elecom_bt」に変更する

&nbsp;
<h2>人間の操作でコースを何周か走行し学習データを作成</h2>
$ python manage.py drive --js

最大スロットル値を調整
赤ボタンで走行記録をオン

前進後退のレバーを上げて走行を開始
走行中は学習データを生成する
停止時は学習データを生成しない
ターミナルからctrl＋Cでプログラムを終了

~/mycar/data/tub_＊_y_m_d
のフォルダが作られ中にjpgファイルとjsonファイルが出来ているか確認

&nbsp;
<h2>参考</h2>
https://qiita.com/mituhiromatuura/items/86a4dde22f469119f9d3
<pre><code class="hljs bash"></code></pre>