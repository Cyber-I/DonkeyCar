---
ID: 230
post_title: >
  DonkeyCar
  Part3：250ドル未満で自動運転を学ぶ
author: gameshell_d7l6g7
post_excerpt: ""
layout: post
permalink: >
  https://donkeycar.jp/2019/08/11/donkey-car-part-3-yes-you-can-learn-autonomous-driving-for-under-250/
published: true
post_date: 2019-08-11 09:08:29
---
<div id="b066" class="it iu ce bc iv b iw ix iy iz ja jb jc">
<figure class="jo jp jq jr js dw v w paragraph-image">
<div class="v w ua">
<div class="jw l dg jx">
<div class="ub l">
<div class="cu ju fl n o fk x jf t jv"></div>
<img class="oe of fl n o fk x fh" src="https://miro.medium.com/max/700/1*embz2VLlEt0Z1oe4ij9ZEA.png" width="700" height="500" />

</div>
</div>
</div>
<figcaption class="bw du kb kc hb cs v w kd ke br dt" data-selectable-paragraph="">ロバ車を運転することを学ぶための概念図。緑は出発点の概念であり、青は中級、黒は高度な「仕上げ」の概念です。</figcaption></figure>
<p id="0c35" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">これはシリーズのパート3です。パート<a class="bb cn kt ku kv kw" href="https://medium.com/@dmccreary/building-an-ai-community-with-diy-robotics-part-1-the-donkey-car-d285579985f1">1</a>および<a class="bb cn kt ku kv kw" href="https://medium.com/@dmccreary/the-donkey-car-part-2-build-calibrate-and-generate-training-data-54265797e8c9">2</a>へのリンクを次に示します。数日間の苦労の末、ようやくドンキーカーで地下の線路を自律的に走行できるようになりました！ここに短いビデオがあります：</p>
https://www.youtube.com/watch?v=Bpt8NZdQLrU

&nbsp;
<p id="86c9" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">だからここで私がつまずいたのです。MacからPiにモデルをアップロードし、「ドライブ」コマンドを実行すると、モデルの読み込みエラーが発生していました。ステップを再実行し続け、同じエラーが発生しました。ドンキーカーと<strong class="kh lt">新しい</strong>バージョンのTensorFlow（1.8）の<strong class="kh lt">古い</strong>バージョンを実行していることに気づくまでに数日かかりましたMacBook Pro上のTensorFlow 1.12のバージョン。また、Donkey CarのヘルプSlackチャンネルに質問を投稿し、新しいTensorFlowバージョン1.12で構築されたモデルがTensorFlowの古いバージョンでは動作しないことを確認しました。MacでTensorFlowをダウングレードする方法を見つけたら（1行のpipシェルコマンド）、トレーニングを再実行し、SCPを使用して新しいモデルをPiに転送しました。カメラのレンズキャップをつけたままにしていた…</p>
<p id="3436" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">約16Kの画像からなる比較的小さなトレーニングセットから始めました。TensorFlow 1.12ではトレーニングに55分かかりましたが、TensorFlow <a class="bb cn kt ku kv kw" href="https://github.com/tensorflow/tensorflow/releases/tag/v1.8.0">1.8</a>では75分かかりました。1.8は2018年4月にリリースされました。DonkeyCarイメージがすぐにアップグレードされ、これらのパフォーマンスの改善をすべて活用できることを願っています。また、トラックを反時計回りに走行するテストセットを使用していました。実際のレースでは、時計回りと反時計回りの両方の走行で車を訓練します。しかし、それはまた、モデルを構築する時間を追加します。</p>
<p id="4321" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">車はトラックを回避できますが、床のライトの反射や側面のその他の白い物体に簡単にだまされます。これは、床に白いテープを1本だけ使用しているためです。それはビジョンシステムが使用するのに十分な信号ではありません。しかし、妻が本当にロバの公式トラックが使用しているように、真ん中に黄色いストライプのある広い黒い「道路」を描くことを望んでいたとは思わない。</p>
<p id="ecbe" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">私がついに自動車を自律モードで動作させるようになったとき、それは非常に満足でした。しかし、それは少し「不気味」でもありました。私は実際に小さな脳に床の線をたどるように「教えた」。それはほとんど私の貧しい運転を模倣するように見えた。ストレートでスピードアップする方法を学び、タイトなカーブでスローダウンしました。それは本当にクールでした！</p>
<p id="193f" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">TensorFlowとKerasを使って仕事をしていましたが、手順の多くは少し抽象的でした。一度ロバ・カーで遊ぶようになったとき、物事はより理解しやすくなりました。システムの長所と短所の両方が明らかになりました。また、トレーニングシステム（私のMacBook）と推論システム（Pi）の間でPythonとTensorFlowライブラリのバージョンを同期させることが重要なステップであることに気付きました。</p>
<p id="691c" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">すべての手順を一度行った後、ほとんどのコンポーネントを理解し、他の人がドンキーカーを実行するために知っておくべき概念を理解するために使用できる「コンセプトマップ」を作成しています。</p>
<p id="b5ce" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">私は今、学んだすべてのステップをたどり、そのステップを、地元のCoderDojoクラブのコンセプトカードを作成した以前の作業と統合しています。これは、ブログ投稿の上部にある図です。コンセプトマップの各ボックスは、最終的にアクティビティと質問が前面に、回答が背面にある1/2枚のラミネート紙になります。これらはビットサイズの学習であるため、CoderDojoでは「寿司カード」と呼ばれます。「Electric Motors」コンセプトカードのサンプル画像を次に示します。</p>

<figure class="jo jp jq jr js dw v w paragraph-image">
<div class="v w uc">
<div class="jw l dg jx">
<div class="ud l">
<div class="cu ju fl n o fk x jf t jv"></div>
<img class="oe of fl n o fk x fh" src="https://miro.medium.com/max/635/1*MAG7wAuHnkkdZGR1SSGgdg.png" width="635" height="476" />

</div>
</div>
</div>
<figcaption class="bw du kb kc hb cs v w kd ke br dt" data-selectable-paragraph="">AI Racing Leagueの電動モーターコンセプトカード。</figcaption></figure>
<p id="e05c" class="kf kg fm bs kh b ki kj kk kl km kn ko kp kq kr ks" data-selectable-paragraph="">私の友人Jon Herkeは、ドンキーカーを使用して、AIとロボット工学について子供たちに教えることを目標とする「AIレーシングリーグ」を構築することにも興味があります。ハックデイの基礎と、10週間、4時間/週のサマーキャンプタイプのプログラムを構築できるかどうか、ご期待ください。私たちは、これらのプログラムに少女や恵まれない若者を巻き込むことを望んでいます。あなたが私たちが始めるのを手伝うことに興味があれば教えてください。</p>

</div>