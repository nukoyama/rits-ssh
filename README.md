# rits-ssh
ritsのリモートサーバへのssh接続


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

参考：　https://secure.ritsumei.ac.jp/students/rainbow/manual-linuxloginshell/

---

## ローカルへコピー

`scp` コマンドを使う。

リモートサーバのホームディレクトリを、ローカル（自分のPC）へ丸ごとコピー：

```sh
scp -r ~ <Rainbow ID>@remote.ritsumei.ac.jp ~/local-dir
```

自分のPCの `~/local-dir` ディレクトリにコピーされる。
