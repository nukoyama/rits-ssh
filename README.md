# rits-ssh
ritsのリモートサーバへのssh接続

## ssh接続

### mac

ritsにvpn接続する。
- 参照： https://secure.ritsumei.ac.jp/rainbow/service-vpn/

ターミナルを起動して
```sh
ssh <Rainbow ID>@remote.ritsumei.ac.jp
```
と打つ。

何か聞かれるので `yes` と入力。
その後Rainbowのpasswordを入力すればritsのlinuxに入れる。

ssh接続を終了するには `exit` と入力してエンター。

### win

teraterm とかいうのを使えばいいらしい
- https://secure.ritsumei.ac.jp/students/rainbow/manual-remotelogin/#step1

## ログインシェルの変更

[RAINBOWユーザーID設定ページ](https://idminfo.ritsumei.ac.jp/webmtn/sso-joint)から、
[ユーザ設定] -> [ログインシェル] とタブを選んで、
```
/bin/bash
```
となっているところを、例えば
```
/bin/zsh
```
に変更する。あとは [保存] を押せばいい。

参考： https://secure.ritsumei.ac.jp/students/rainbow/manual-linuxloginshell/

## ローカルへコピー

`scp` コマンドを使う。

- 注：ssh接続は終了して、自分のPCのシェルで実行してください。

リモートサーバのホームディレクトリ `~` 以下を、ローカル（自分のPC）へ丸ごとコピー：

```sh
scp -r <Rainbow ID>@remote.ritsumei.ac.jp:~ ~/local-dir
```

自分のPCの `~/local-dir` ディレクトリにコピーされる。

- 参考： https://webkaru.net/linux/scp-command/

## Finder でサーバを開く？

コマンドラインからだといろいろ不便なので、macOSのファイルブラウズアプリFinderでサーバへアクセスする。

Homebrewを知らない人はググってインスコしてください。

Homebrewで次の2つをインスコ：





