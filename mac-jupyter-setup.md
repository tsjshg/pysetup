
# Jupyter環境をセットアップする（macOS）

[Jupyter](https://jupyter.org/)環境を使ってPythonを使ったプログラミングを実行するための環境を構築します。（2023年5月更新）

手順は以下の通りです。
1. Pythonをインストールする
1. シェルを使った確認
    1. Pythonの起動
    1. pipコマンド
1. JupyterLabのインストール
1. JupyterLabの起動

## Pythonのインストール

[こちらのサイト](https://www.python.org/downloads/)から、Pythonのインストーラをダウンロードします。バージョン表記は、3.11.3のようにドットで3つに区切られていて、一番左側から右へいくほど細かく頻繁に更新される番号です。ここでは、Python3をインストールするので、一番左側は3です。次の番号は、10や11より大きければ比較的新しいので問題ありません。一番右はほとんど気にする必要がありませんが、その時点でもっとも大きな数字のバージョンを選びます。

ダウンロードしたインストーラを起動します。インストールの途中で変更すべき設定はないのでそのままインストールを実行します。

インストールの最後で、「Install Certificates.command」の実行を促されますので、指定のファイルをダブルクリックしてインストールします。あとからやる場合は、アプリケーション > Python3.11 > Install Certificates.commandを実行します。

## シェルを使った確認

ターミナルを起動します。シェルを使った操作が分からない方は[こちら](https://tsjshg.github.io/pysetup/cui-shell)のページも参考にしてください。

### Pythonの起動

次のコマンドでPythonの起動を確認します。

```
python3
```

シェルの対話相手がPythonインタラクティブシェルに変わるので、プロンプトが`>>>`になります。ここで、インストールしたバージョンが正しいことを確認します。これが違う場合は、何らかの問題があります。ターミナルを再起動しても問題が解決しない場合は、Python自体のインストールをもう1度実行してみてください。

```
Python 3.11.3 (v3.11.3:f3909b8bc8, Apr  4 2023, 20:12:10) [Clang 13.0.0 (clang-1300.0.29.30)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

`quit()`とするとPythonインタラクティブシェルを抜けられます。

### pipコマンド

`pip`は標準Pythonの機能を拡張するために、外部ライブラリをインストールするためのコマンドです。Pythonインタラクティブシェルを抜けて、OSのシェルが起動している状態で

```
pip3
```

とだけ入力して次のようにpipのヘルプが表示されればpipコマンドが使える状態になっています。

```
Usage:   
  pip3 <command> [options]

Commands:
  install                     Install packages.
  download                    Download packages.
  uninstall                   Uninstall packages.
  freeze                      Output installed packages in requirements format.
  list                        List installed packages.
  show                        Show information about installed packages.
  check                       Verify installed packages have compatible dependencies.
（以下省略）
```

念のため、インストールしたPythonと同じ位置にあるpipが起動しているかどうかを調べます。

```
which pip3
```
```
/Library/Frameworks/Python.framework/Versions/3.11/bin/pip3
```
ここで表示されるPythonのバージョンが正しいことを確認します。3.11.3をインストールしても一番右の数字は省略されるので3.11となっていれば問題ありません。

## JupyterLabのインストール

`pip`コマンドを使って[JupyterLab](https://jupyterlab.readthedocs.io/en/stable/)をインストールします。

OSのシェルから次のように入力します。

```
pip3 install jupyterlab
```

JupyterLabをセットアップするのに必要な別の外部ライブラリも合わせてインストールされるためすこし時間がかかります。

```
Successfully installed MarkupSafe-2.1.2 aiofiles-22.1.0 aiosqlite-0.19.0 (...略...) jsonpointer-2.3 jsonschema-4.17.3 jupyter-client-8.2.0 jupyter-core-5.3.0 jupyter-events-0.6.3 jupyter-server-2.5.0 jupyter-server-fileid-0.9.0 jupyter-server-terminals-0.4.4 jupyter-server-ydoc-0.8.0 jupyter-ydoc-0.2.4 jupyterlab-3.6.3 jupyterlab-pygments-0.2.2 jupyterlab-server-2.22.1 matplotlib-inline-0.1.6 mistune-2.0.5 nbclassic-1.0.0 nbclient-0.7.4  (...略)
```

このような表示が出ればインストールは成功です。

以下のような表示も出る場合は、pip自体のバージョンアップが可能です。

```
[notice] A new release of pip available: 22.3.1 -> 23.1.2
[notice] To update, run: pip3 install --upgrade pip
```

次のコマンドでpipのアップデートをします。

```
pip3 install -U pip
```

## JupyterLabの起動

ターミナルから次のコマンドでJupyterLabを起動します。

```
jupyter-lab
```

Webブラウザが起動して、JupyterLabの画面が表示されれば完了です。

JupyterLabを終了するには、FileメニューからShut Downを選びます。または、JupyterLabを起動したターミナルの画面へ移動し「Ctrl−C」と入力したあと、yを選んでも終了できます。
