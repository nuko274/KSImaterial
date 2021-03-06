# Linux Tips

## ターミナルで、緑の部分が長くて困っている人へ
- ターミナルを開き、以下のコマンドを入力する。

```
$ nano ~/.bashrc
```

- nanoが開くので、一番下に（例えば）以下の一行を書き足す。

```
PS1="\[\e[1;32m\]\w\[\e[m\]$ "
```

**イコールの前後には半角スペースを入れないように！**

- Ctrl + X → Y → Enter で保存し、`exit`する。
- その後ターミナルを再起動し、緑の部分がなくなっていることを確認する。

##### ステップ2において、以下の一行に変更した場合どうなるか検証してみよう！ 

```
PS1="$ "
```

「Linux PS1」でググると、いろいろ出てくるので、好きなようにカスタマイズしよう！

## `apt`を使ってパッケージを入れる。
Debianではソフトウェア管理にapt-getというコマンドを使います。Debian をベースとした Linux ディストリビューションである Ubuntu も同じです。

例えば xterm を使いたいのに入っていなかったら、

```
$ sudo apt install xterm
```

とします。

後述にもありますが、システムおよび追加インストールしたパッケージのアップデートには

```
sudo apt update
sudo apt dist-upgrade
```

を行います。

このようにしてインストールしたパッケージは

```
$ sudo apt remove [パッケージ名]
$ sudo apt purge [パッケージ名]
```

のいずれかで削除できます。（違いは`man`コマンドで確認）

- おまけ
パッケージ`sl`をインストールした後、端末で

```
$ sl
```
と入力したら…？

`man`コマンドで何のためのコマンドか確かめておくこと。オプションを試してみてもよい。（さらに謎のヒント　`$ ls /usr/games`)

## ソフトウェアの更新方法

Ubuntuにはかなり頻繁にソフトウェアアップデートが出ています。

本体だけではなく、`apt`でインストールしたアプリケーションソフトウェアに対してもアップデートが行われます。

動作中にはバックグラウンドで自動アップデートが行われますが，授業時間以外はシステム停止しているので**毎受講時のはじめに次を実行してください**。

```
$ sudo apt update
$ sudo apt dist-upgrade
```

アップデートによってカーネルが置き換えられた場合は再起動が必要です。
自動アップデートが実行中の場合など、エラーが発生した際には，出力されたメッセージの指示に従ってください。