---
ID: 254
post_title: Raspberry Pi
author: gameshell_d7l6g7
post_excerpt: ""
layout: page
permalink: https://donkeycar.jp/raspberry-pi/
published: true
post_date: 2019-08-21 12:48:54
---
<h1>Raspberry Piとは</h1>
Raspberry Piは、最近ではIoTを構築するための手軽なプラットフォームといった使われ方をしているが、もともとはARMプロセッサを使った安価な教育用コンピュータとして開発されたものだ。

<em>Raspbian</em> は Debianベースの Raspberry Pi 用の子供向けの教育用、および小規模な開発者向けのコンピュータOS(オペレーティング-システム) である。少ないリソースでも快適に動作するように設計されている。
<h1>DonkeyCar用Raspberry Piイメージファイル</h1>
自力でDonkey CarのコアとしてRaspberry Piを利用する場合、さまざまなPythonおよびTensorFlowライブラリをPiでネイティブに動作させるために大変な作業でした。

LinuxおよびPiの専門家によって3年間にわたって慎重に作成された、DonkeyCarに特化したRaspberry Piをディスクイメージを利用するとよい。

とくにGooole Colab に対応した<a href="https://donkeycar.jp/fabo-donkey-car/">Fabo Donkey Car</a>のディスクイメージがお薦めだ。Google Colaboraotoryと連携するために、DonkeyCar 2.5.8, TernsorFlow 2.0.0 Alpha0をインストール、プロジェクトの作成やWireless Joystick、マルチタブ化も実施したRaspberryPi用イメージになります。

<a href="https://drive.google.com/open?id=1i7_qAR-i-pqW47MtnTXW08zxKMfCSH8x">Download</a>

焼き込みには、Etcherを使い焼き込みます。 <a href="https://www.balena.io/etcher/">https://www.balena.io/etcher/</a>
<h1>Raspberry PiにWiFi接続</h1>
Piに新しいSDを差込、モニターに繋いて起動した後、ログインして、
<ol>
 	<li>WiFi設定</li>
 	<li>固定IP設定</li>
 	<li>ssh 接続</li>
</ol>
してください。
<h1>教訓</h1>
教訓１：シャットダウンしないて、電源コンセントをいきなり抜く<span class="a-size-base review-text review-text-content" data-hook="review-body"><span class="">。</span></span>

学生の初心者は、Raspberry Piの電源コンセントをいきなり抜くことが多発する。Headless状態でモニター画面がないけど、動いている。DonkeyCarを学習する際、原因不明のエラーで中止され、数日解決できない。

専門家の助けを求めたら、Raspberry Piを停電すると、ゴミファイル大量に発生する。DonkeyCarの学習に悪影響。手間をかけてゴミファイルをクリアしたら、DonkeyCarの学習はできた。

&nbsp;