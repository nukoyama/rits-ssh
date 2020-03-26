# rits-ssh
ritsのリモートサーバへのssh接続まとめ

## ssh接続

### mac

まず、ritsにvpn接続する。
- 参照： https://secure.ritsumei.ac.jp/rainbow/service-vpn/

以下、ritsにvpn接続しているものとして話を進める。

ターミナルを起動して
```sh
ssh <Rainbow ID>@remote.ritsumei.ac.jp
```
と打つ。

`<Rainbow ID>` には自分のRainbow IDを入れる。

多分、何か聞かれるので `yes` と入力。
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

## マウント

コマンドラインからだといろいろ不便なので、macOSのファイルブラウズアプリFinderでサーバのファイルをブラウズできるようにする。

- 注：Homebrewを知らない人はググってインスコしてください。

Homebrewで次の2つをインスコ：

```sh
brew cask install osxfuse
brew install sshfs
```

マウントするディレクトリを作成：

```sh
mkdir ~/mount
```

ホームディレクトリに `mount` という名前のディレクトリを作成しました。

インスコが終わったら、次のコマンドでサーバ先をマウントする：

```sh
sshfs <Rainbow ID>@remote.ritsumei.ac.jp:<path to dir> ~/mount
```

`<path to dir>` には、例えばサーバのルートから自分のホームディレクトリへの絶対パスを入力する。

- 多分、2016年度入学の学生であれば `/homer/se/16/<Rainbow ID>` でいけるはず。
- ssh接続して `pwd` コマンドを打てばルートからホームディレクトリへの絶対パスが表示されるので、それをメモっておくといい。

また、セキュリティで文句を言われたら、システム環境設定を開いて、許可を出す。

最後に、アンマウントするには、Finderで開いている場合はウインドウを閉じてから、次のコマンドを入力：

```sh
umount ~/mount
```

- 参考：https://techracho.bpsinc.jp/hachi8833/2019_02_05/66454

