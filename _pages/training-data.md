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
<pre><code class="hljs bash"></code></pre>