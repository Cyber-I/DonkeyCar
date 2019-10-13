---
ID: 304
post_title: Training
author: gameshell_d7l6g7
post_excerpt: ""
layout: page
permalink: https://donkeycar.jp/machine-learning/
published: true
post_date: 2019-08-21 13:44:48
---
人間が操作して10～15周くらいコース上を走らせます。コース上には赤いコーンなどを配置してもよい。

この間に、ドンキーカーは1万枚程度の“画像”と人間が操作した“ステアリング”と“スロットル”の<a href="https://donkeycar.jp/training-data/">学習データ</a>を一緒に記録します。
<h1>操作</h1>
通常、PS3のコントローラやロジクールF710などの<a href="https://donkeycar.jp/controller/">ゲームパッド</a>で操作します。
<ol>
 	<li>PS3のコントローラ</li>
 	<li><a href="https://amzn.to/2R85kAK" rel="nofollow">Logicool Wireress GamePad F710</a></li>
 	<li><a href="https://amzn.to/2SddDvo" rel="nofollow">ELECOM Wireress GamePad JC-U3912T</a></li>
</ol>
<h1>学習</h1>
記録したデータのをPCにコピーして、グーグルの機械学習AIプラットフォームであるTensorFlowを使って学習モデルを生成します。

AIプラットフォームは必要に応じて次の3種類の利用が考えられます。
<ol>
 	<li><a href="https://donkeycar.jp/google-colab/">Google Colab</a>クラウドを利用</li>
 	<li>PCにTensorFlowを使って学習環境を用意</li>
 	<li>Donkey Car に<a href="https://donkeycar.jp/nvidia-jetbot/" aria-current="page">NVIDIA JetBot</a></li>
</ol>
クラウドを利用は手軽い始められるので、初心者におすすめです。

&nbsp;