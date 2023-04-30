
# Python実行環境の構築

プログラミング言語Pythonの実行環境を構築するために必要な知識を紹介します。

## 前提知識

CUIのシェルを使ったコンピュータの操作が必要です。Windows系OSではPowerShell、macOSではターミナルと呼ばれるソフトウェアです。pipやcondaといったコマンドをシェルに入力して実行します。

## Python環境設定の基礎

### 標準ライブラリと外部ライブラリ

Pythonは普通のアプリケーションと同じようにPCにインストールできます。ただ、Pythonだけをインストールした状態では、**標準ライブラリ**しか利用することができません。Webアプリの開発やデータサイエンスなど、専門的な作業をするためには、**外部ライブラリ**を追加でセットアップする必要があります。外部ライブラリのインストールには通常、ターミナルなどのシェルから`pip`コマンドを使います。

```
> pip install パッケージ名
```

### Pythonの配布形態

広く使われいるPythonのインストーラーは2種類あります。1つは、[本家python.org](https://www.python.org/)が配布するもの、もう1つは[Anaconda社](https://www.anaconda.com)が配布する[Anaconda](https://www.anaconda.com/download/)です。

Anacondaは、Pythonの標準実装に加えAnaconda社が開発した`conda`コマンドなどが追加され機能が強化されています。また、よく使われる外部ライブラリがAnacondaに同梱されているので、Anacondaをインストールするだけで多くの外部ライブラリが利用できる状態になっています。Anacondaでは、`conda`コマンドを使って外部ライブラリを管理しますが、`pip`コマンドの利用も可能です。

以下では、配布形態ごとに利点と欠点をまとめます。

### 本家のPythonを使う

使っているOSに応じてPythonをダウンロードしてインストールします。外部ライブラリの追加は`pip`コマンドを使います。シンプルな構成なので慣れればあまり困ることはありませんが、稀に`pip`でうまくインストールできないライブラリがあるかもしれません。

### Anacondaを使う

Anacondaをインストールして、`conda`コマンドで外部ライブラリを管理します。有名な外部ライブラリの多くはAnacondaに同梱されているので便利です。AnacondaでセットアップしたPython環境に`pip`コマンドで外部ライブラリを追加することは可能ですが、環境が壊れる可能性があるので、`conda`コマンドに統一した方がよいです。

### その他の方法

ちょっとしたPythonコードの実行から、本格的なデータサイエンスの実践まで、[Google Colab](https://colab.research.google.com)が便利です。ファイルをアップロードしたりダウンロードするためには、[Google driveとの連携](https://colab.research.google.com/github/tom2rd/Googlecolabutils/blob/master/Mount_Google_Drive.ipynb)が必要です。


## Python環境設定に関するすこし高度な話

### 仮想環境

Pythonは世界的に人気がある言語です。これは、外部ライブラリの豊富さに支えられている部分もあります。外部ライブラリが豊富なため、ソフトウェアの開発が楽になり、開発者の人気が集まってさらに外部ライブラリが豊富になるという好循環です。

こうした豊富なライブラリは、それぞれ別のライブラリに依存していることが多く、こうした依存関係にバージョンの問題が発生することがあります。この問題を解決するのが**仮想環境**です。仮想環境を利用すると、外部ライブラリをインストールするPythonの環境を切り分けることができます。

<!-- ![仮想環境の説明図](https://github.com/tsjshg/pysetup/blob/gh-pages/figs/img.png?raw=true "仮想環境の説明") -->


仮想環境を構築するための具体的な方法は、以下のリンクが参考になります。

[Windows](https://www.python.jp/install/windows/venv.html)

[macOS](https://www.python.jp/install/macos/virtualenv.html)

仮想環境は通常、標準ライブラリvenvを使って作ります。Anacondaでは`conda`コマンドを使って外部ライブラリのインストールだけではなく、仮想環境の管理もできます。`conda`コマンドは標準実装Pythonの`pip`と`venv`を統合した機能を持っているとも言えます。

### パッケージのレポジトリ

外部ライブラリは、パッケージとしてまとめられ、レポジトリと呼ばれるWeb上のサーバに保管されています。`pip`コマンドは、[Python Package Index (PyPI)](https://pypi.org/)に接続して指定されたライブラリを検索してダウンロードします。一方、`conda`コマンドは[Anaconda社が管理するレポジトリ](https://anaconda.org/anaconda/repo)へ接続します。これらの接続先はコマンドラインオプションで変更することもできます。

接続するレポジトリが違うこともあり、通常`pip`と`conda`でインストールされるライブラリは名前が同じでもバージョンが違うことがあります。これを避けるためにバージョンを指定してインストールすることも可能です。pipを使ってバージョンを指定して外部ライブラリをインストールするコマンドは次のようになります。[bottle](https://bottlepy.org/docs/dev/)というライブラリのバージョン0.12.19をインストールする例です。

```
> pip install bottle==0.12.19
```

### Anaconda有償化対策

`conda`コマンドが使えるAnacondaは完全に無料で利用できるソフトウェアではありません。所属組織の種類や大きさでライセンス料が発生する可能性があるので注意が必要です。一方で、`conda`コマンドが使える環境は便利です。こうした背景もあり、無料で`conda`コマンドを使うことができる環境を構築も可能です。

まずPython本体を[miniforge](https://github.com/conda-forge/miniforge)でインストールします。これで`conda`コマンドが使える環境ができます。`conda`で外部ライブラリを追加する場合、接続するレポジトリを[conda-forge](https://conda-forge.org/)へ変更します。

```
> conda install -c conda-forge パッケージの名前
```

## 参考資料

[Python環境構築ガイド](https://www.python.jp/install/install.html)
Pythonの環境構築に関して詳しい情報があります。ぜひ参考にしてください。
