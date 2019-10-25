---
ID: 161
post_title: Calibration
author: gameshell_d7l6g7
post_excerpt: ""
layout: page
permalink: https://donkeycar.jp/motor-shield/
published: true
post_date: 2019-06-23 16:59:53
---
<h2>ステアリングキャリブレーション</h2>
暴走を防ぐため、車が地面から離れていることを確認してください。
<ol>
 	<li>    車の電源を入れます。</li>
 	<li>    車のサーボケーブルを見つけて、PCAボードに接続されているチャンネルを確認します。 1または0である必要があります。</li>
 	<li>    実行ドンキーキャリブレーション--channel &lt;your_steering_channel&gt; --bus = 1</li>
 	<li>    360と入力すると、車の車輪がわずかに動くのが見えるはずです。 400または300を入力しない場合。</li>
 	<li>    次に、開始値から+/- 10の値を入力して、車を左いっぱいに、右いっぱいに回すPWM設定を見つけます。これらの値を覚えておいてください。</li>
 	<li>    これらの値をmyconfig.pyスクリプトにSTEERING_RIGHT_PWMおよびSTEERING_LEFT_PWMとして入力します。</li>
</ol>
<h2>スロットルキャリブレーション</h2>
<ol>
 	<li>    ESCからのケーブルを見つけて、PCAボードに接続されているチャンネルを確認します。これがスロットルチャンネルです。</li>
 	<li>    実行ドンキーキャリブレーション--channel &lt;your_throttle_channel&gt; --bus = 1</li>
 	<li>    PWM値の入力を求められたら、370を入力します。</li>
 	<li>    ESCのビープ音が聞こえ、キャリブレーションが完了したことを示すはずです。</li>
 	<li>    400を入力すると、車のホイールが前方に移動し始めます。そうでない場合、これは逆である可能性が高いため、代わりに330を入力してみてください。</li>
 	<li>    妥当な最大速度が見つかるまでさまざまな値を試し、このPWM値を覚えておいてください。</li>
</ol>
ESCは逆パルス、ゼロパルス、逆パルスを受信して後方に移動し始める必要があるため、RCカーでのリバースは少し注意が必要です。 逆PWM設定を調整するには...
<ol>
 	<li>     上記と同じ手法を使用して、PWM設定をゼロスロットルに設定します。</li>
 	<li>     リバース値、ゼロスロットル値、そしてリバース値をもう一度入力します。</li>
 	<li>     適切な後退速度を見つけるには、後退値の+/- 10の値を入力します。 この逆PWM値を覚えておいてください。</li>
</ol>
myconfig.pyスクリプトを開き、車のPWM値をthrottle_controller部分に入力します。

THROTTLE_FORWARD_PWM =フルスロットルフォワードのPWM値
THROTTLE_STOPPED_PWM =ゼロスロットルのPWM値
THROTTLE_REVERSE_PWM =フルリバーススロットルでのPWM値

&nbsp;