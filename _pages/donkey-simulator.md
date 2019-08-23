---
ID: 292
post_title: Donkey Simulator
author: gameshell_d7l6g7
post_excerpt: ""
layout: page
permalink: https://donkeycar.jp/donkey-simulator/
published: true
post_date: 2019-08-21 13:39:21
---
<h1>Donkey Simulator</h1>
Donkey Carに関心を持たれた方は、Donkey Simulatorを使ってPC上でDonkey Carのテスト走行、教師あり学習、自律走行をシミュレーションで楽しむことができる。

RCカーを購入する前にDonkey Carで必要な作業がどんなものなのか、どういったところが楽しいのかを体感できる。
<h1>Donkey Simulatorをインストールする</h1>
<a href="https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F61995%2Ff8463480-49b4-1a35-640e-741963d61851.png?ixlib=rb-1.2.2&amp;auto=compress%2Cformat&amp;fit=max&amp;s=0e2da87e3fbd0670a4db63b032c7c0fc" target="_blank" rel="nofollow noopener noreferrer"><img src="https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F61995%2Ff8463480-49b4-1a35-640e-741963d61851.png?ixlib=rb-1.2.2&amp;auto=compress%2Cformat&amp;fit=max&amp;s=0e2da87e3fbd0670a4db63b032c7c0fc" srcset="https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F61995%2Ff8463480-49b4-1a35-640e-741963d61851.png?ixlib=rb-1.2.2&amp;auto=compress%2Cformat&amp;fit=max&amp;w=1400&amp;s=23d2db5c08aaafb71b325ede87b77042 1x" alt="donkey_sim_icon.png" /></a>

シミュレーターをインストールします。各プラットフォーム毎に用意されています
<a class="autolink" href="https://github.com/tawnkramer/gym-donkeycar/releases" target="_blank" rel="nofollow noopener noreferrer">https://github.com/tawnkramer/gym-donkeycar/releases</a>

Macの場合、最新版をダウンロードしてzipで展開すると<code>DonkeySimMac</code>が作成されます。その中にある<code>donkey_sim</code>を<code>/Application</code>にドラッグ&amp;ドロップします。
<h1>DonkeyCarをセットアップする</h1>
<a href="https://docs.donkeycar.com/guide/host_pc/setup_mac/" target="_blank" rel="nofollow noopener noreferrer">Install Donkeycar on Mac</a>に従ってPCにdonkeycarをセットアップします。Donkey Carは現時点の最新バージョン<code>3.1.0</code>です。Donkey Carの開発は活発なのでバージョンアップされてセットアップ方法が変更される可能性があります

&nbsp;
<h1>プロジェクトを作成する</h1>
<code>donkey createcar</code>コマンドでプロジェクトを作成します
<div class="code-frame" data-lang="shell">
<div class="highlight">
<pre>donkey createcar <span class="nt">--path</span> ./mycar
<span class="nb">cd</span> ./mycar
</pre>
</div>
</div>
<code>myconfig.py</code>を編集します。このプロジェクトをDonkey Simulatorに対応させるための設定を行います。200行目あたりの以下の3行のコメントを外し、<code>DONKEY_GYM</code>を<code>True</code>に<code>DONKEY_SIM_PATH</code>にDonkey Simulatorのパスを設定します
<div class="code-frame" data-lang="python">
<div class="code-lang"><span class="bold">myconfig.py</span></div>
<div class="highlight">
<pre><span class="n">DONKEY_GYM</span> <span class="o">=</span> <span class="bp">True</span>
<span class="n">DONKEY_SIM_PATH</span> <span class="o">=</span> <span class="s">"/Applications/donkey_sim.app/Contents/MacOS/donkey_sim"</span>
<span class="n">DONKEY_GYM_ENV_NAME</span> <span class="o">=</span> <span class="s">"donkey-generated-track-v0"</span>
</pre>
</div>
</div>
以上でDonkey Carシミュレーターで遊ぶ準備ができました
<h1>シミュレーターを起動してテスト走行する</h1>
<code>donkey_sim</code>を起動します。コンフィギュレーションダイアログが表示されるので<code>Screen resolution</code>を<code>800 x 600</code>、<code>Windowed</code>にチェックを入れて<code>Play!</code>ボタンをクリックします。
<h1>教師用データを取得する</h1>
Donkey Car実機では教師データを取得するために手動で記録用走行を行います。このとき前方に搭載したカメラで走行中の景色を画像データとして記録し、同時に手動操作されたスロットルやハンドルの操作履歴を記録してそれを教師用データとします。シミュレーターでは記録モードで走行することで実機と同様のデータを取得することができます。

まず、テスト走行のときと同様に<code>donkey_sim</code>を起動します。コースを選択する前に画面右下の<code>Log dir</code>ボタンをクリックします

カーソルキーでDonkey Carを操作してコースを周回します。左下の<code>Log:</code>の表示で記録されている画像の枚数を確認できます。だいたい5000〜10000くらいを目安にしてください。十分に記録ができたら右上の<code>Stop</code>ボタンでシミュレーターを終了します
<h1>学習する</h1>
<h2>Colabで高速に訓練する</h2>
<a href="https://faboplatform.github.io/DonkeyDocs/2.DonkeyCar%E5%80%8B%E5%88%A5%E8%A8%AD%E5%AE%9A/13.train_colab/" target="_blank" rel="nofollow noopener noreferrer">FaBo DonkeyCar Docs Colabでの学習(GPU)</a>で<a href="https://colab.research.google.com/notebooks/welcome.ipynb" target="_blank" rel="nofollow noopener noreferrer">Google Colab</a>のGPUを利用できるnotebookが公開されています。このnotebookを使うとGPUを使って高速に訓練することができるので大変便利です。教師用画像データが5000枚程度であればだいたい5分くらいで訓練が完了します。使い方はNotebookに丁寧に記載されているので、記載どおりにすすめていけばよいです
<h1>自律走行してみる</h1>
以下のコマンドを実行します。<code>--type=categorical</code>に注意してください。<code>--type</code>で指定するモデルタイプは上記の<code>python manage.py train</code>のときに指定したものと必ず一致させる必要があります
<div class="code-frame" data-lang="shell">
<div class="highlight">
<pre>python manage.py drive <span class="nt">--type</span><span class="o">=</span>categorical <span class="nt">--model</span><span class="o">=</span>models/mypilot.h5 
</pre>
</div>
</div>
上記を実行するとDonkey Simulatorのコンフィギュレーションダイアログが起動するのでテスト走行のときのように設定して<code>Play!</code>をクリックします
<h1>参考資料</h1>
<ul>
 	<li>https://qiita.com/bathtimefish/items/99afeaa406cc60ff2204 - Donkey Carを組み立てる前にシミュレーターで楽しんでみる Donkey Car 3.1.0編</li>
</ul>