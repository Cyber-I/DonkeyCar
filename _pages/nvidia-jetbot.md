---
ID: 188
post_title: NVIDIA JetBot
author: gameshell_d7l6g7
post_excerpt: ""
layout: page
permalink: https://donkeycar.jp/nvidia-jetbot/
published: true
post_date: 2019-07-07 12:42:32
---
<h1 class="it-Header_title">NVIDIA JetBotとは</h1>
NVIDIA の Jetson Nano がGTCで発表され、同時に発表されたAIプロジェクトの <a href="https://github.com/NVIDIA-AI-IOT/jetbot" target="_blank" rel="nofollow noopener noreferrer">JetBot</a> も注目されています。

本家 GitHub レポジトリ；　<a class="autolink" href="https://github.com/NVIDIA-AI-IOT/jetbot" target="_blank" rel="nofollow noopener noreferrer">https://github.com/NVIDIA-AI-IOT/jetbot</a>
本家 GitHub の Wiki ； <a class="autolink" href="https://github.com/NVIDIA-AI-IOT/jetbot/wiki" target="_blank" rel="nofollow noopener noreferrer">https://github.com/NVIDIA-AI-IOT/jetbot/wiki</a>
本家 Wiki の BOM（部品表）； <a class="autolink" href="https://github.com/NVIDIA-AI-IOT/jetbot/wiki/Bill-of-Materials" target="_blank" rel="nofollow noopener noreferrer">https://github.com/NVIDIA-AI-IOT/jetbot/wiki/Bill-of-Materials</a>

&nbsp;
<h1>JetBot 版 Donkey Car を走らせる手順</h1>
<div class="_2cuy _3dgx _2vxa">JetBot 版 Donkey Car を走らせる手順を軽く説明。5) 以降について詳しくは Donkey Car サイトのドキュメント参照：</div>
<ol class="_5a_q _509r" dir="ltr">
 	<li class="_2cuy _509s _2vxa">jetbot を wi-fi につなぐ</li>
 	<li class="_2cuy _509s _2vxa">PCからjetbotにユーザ jetbot で ssh ログインする</li>
 	<li class="_2cuy _509s _2vxa">workon donkey で Donkey Car 用の python 仮装環境に入る</li>
 	<li class="_2cuy _509s _2vxa">cd ~/mycar</li>
 	<li class="_2cuy _509s _2vxa">python manage.py drive --model=models/mypilot.h5 で事前学習済みモデルで起動</li>
 	<li class="_2cuy _509s _2vxa">PC の Web ブラウザから　http://&lt;jetbotのIPアドレス&gt;:8887</li>
 	<li class="_2cuy _509s _2vxa">"Mode &amp; Pilot" から Local Pilot を 選ぶと自動走行開始</li>
</ol>
&nbsp;
<h1>参考資料</h1>
<ol>
 	<li><a href="https://faboplatform.github.io/JetbotDocs/">https://faboplatform.github.io/JetbotDocs/</a></li>
 	<li><a href="https://www.facebook.com/groups/351316242393961/">https://www.facebook.com/groups/351316242393961/</a></li>
</ol>