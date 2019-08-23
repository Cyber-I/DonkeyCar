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

&nbsp;
<h2>WiFi設定</h2>
<h3><code>wpa_supplicant.conf</code>に無線LAN情報を追記</h3>
以下を実行
<div class="code-frame" data-lang="text">
<div class="highlight">
<pre>$ sudo sh -c 'wpa_passphrase SSID PASSPHRASE &gt;&gt; /etc/wpa_supplicant/wpa_supplicant.conf'
</pre>
</div>
</div>
<code>SSID</code>と<code>PASSPHRASE</code>を自身の無線ルータ等の設定にしてください。
<h3><span id="生パスワードを削除" class="fragment"></span>生パスワードを削除</h3>
<code>/etc/wpa_supplicant/wpa_supplicant.conf</code>ファイル内では、生パスワードがコメントアウトで記載されているので、確認してから削除しましょう。
<div class="code-frame" data-lang="text">
<div class="code-lang"><span class="bold">/etc/wpa_supplicant/wpa_supplicant.conf</span></div>
<div class="highlight">
<pre>ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=GB

network={
        ssid="SSID"
        #psk="PASSPHRASE" #消しておきましょう
        psk=xxxxxxxxxxx....xxx
}

</pre>
</div>
</div>
<h2>固定IP設定</h2>
<h3><code>dhcpcd.conf</code>にネットワーク情報を追記</h3>
Raspbian Wheezyでは、固定IPアドレス設定には、<code>/etc/network/interface</code>のファイルを修正しましたが、Jessieからは代わりに<code>/etc/dhcpcd.conf</code>ファイルへ設定内容を追記します。
<div class="code-frame" data-lang="text">
<div class="code-lang"><span class="bold">/etc/dhcpcd.conf</span></div>
<div class="highlight">
<pre># 追記
interface wlan0
static ip_address=192.168.11.40/24
static routers=192.168.11.1
static domain_name_servers=192.168.11.1
</pre>
</div>
</div>
上記の設定はBuffalo無線ルータの場合の設定です。
<code>routers</code>というのは<code>gateway</code>に当たります。
<h2><span id="設定確認" class="fragment"></span>設定確認</h2>
シャットダウンしてLANケーブルが繋がっているならば抜き、再起動後、指定したIPアドレスで無線LANが設定されているかを確認します。
<div class="code-frame" data-lang="text">
<div class="highlight">
<pre>$ ip addr
(略)
3: wlan0: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether b8:27:eb:82:1b:df brd ff:ff:ff:ff:ff:ff
    inet 192.168.11.40/24 brd 192.168.11.255 scope global wlan0
       valid_lft forever preferred_lft forever
    inet6 fe80::dcdd:d297:5e54:2b4d/64 scope link
       valid_lft forever preferred_lft forever
</pre>
</div>
</div>
これで無線LANを通じてSSH接続等ができるようになりました!
<h1>教訓</h1>
教訓１：シャットダウンしないて、電源コンセントをいきなり抜く<span class="a-size-base review-text review-text-content" data-hook="review-body"><span class="">。</span></span>

学生の初心者は、Raspberry Piの電源コンセントをいきなり抜くことが多発する。Headless状態でモニター画面がないけど、動いている。DonkeyCarを学習する際、原因不明のエラーで中止され、数日解決できない。

専門家の助けを求めたら、Raspberry Piを停電すると、ゴミファイル大量に発生する。DonkeyCarの学習に悪影響。手間をかけてゴミファイルをクリアしたら、DonkeyCarの学習はできた。

&nbsp;
<h1>参考</h1>
<ul>
 	<li>https://qiita.com/momotaro98/items/fa94c0ed6e9e727fe15e</li>
</ul>