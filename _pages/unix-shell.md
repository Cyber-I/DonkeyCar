---
ID: 282
post_title: UNIX command
author: gameshell_d7l6g7
post_excerpt: ""
layout: page
permalink: https://donkeycar.jp/unix-shell/
published: true
post_date: 2019-08-21 13:26:25
---
<h4>Unix, Linux の基本操作コマンドを説明する</h4>
<h1>ログイン</h1>
Raspberry Pi 以下の初期ユーザ名：パスワードを入力し、ログインします。
<table border="2" width="282">
<tbody>
<tr>
<td>ユーザ名</td>
<td>pi</td>
</tr>
<tr>
<td>パスワード</td>
<td>raspberry</td>
</tr>
</tbody>
</table>
<h4></h4>
ユーザpiをipのサーバにログインとする。
$ ssh pi@ip
サーバの中身が入れ替わり、ログインできない場合、~.ssh/know_hostに該当する項目を削除してください。
<h1>ログアウト</h1>
$ logout
<h1>パスワード変更</h1>
$ passwd pi
<h1>停止と再起動</h1>
停止

$ sudo shutdown -H now

再起動

$ sudo reboot
<h1>相対パス／絶対パス</h1>
ルートディレクトリからパスを順番に下ってパスを表す方法を<strong>絶対パス</strong>と呼びます。<strong>フルパス</strong>と呼ぶ場合もあります。

コマンドラインで現在作業中のディレクトリを<strong>カレントディレクトリ</strong>と呼びます。カレントディレクトリからの相対的なパスを<strong>相対パス</strong>と呼びます。

&nbsp;