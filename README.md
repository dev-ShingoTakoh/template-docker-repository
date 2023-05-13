<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/github-markdown-css/5.1.0/github-markdown.min.css">

# テンプレートdockerリポジトリ

## 概要

- docker containerを利用する際のテンプレートリポジトリです。
- こちらのリポジトリを使用して各々の開発を進めます。

## 目次

- [事前準備](#anchor1)
- [Gitブランチ戦略](#anchor2)
- [環境の詳細](#anchor3)
- [環境の構築](#anchor4)
- [Make基本コマンド一覧](#anchor5)
- [etc](#anchor6)
- [参考リンク](#anchor7)

<a id="anchor1"></a>

## 事前準備

- Makefileを一部使用しています。Macの場合はHomebrewをインストールしていると使用できると思いますが、Windowsの場合は下記リンクを参考に実行環境を整えてください。

  [Windows10環境でmakeをする方法](https://camedphone.com/archives/1192)

  ※MacでHomebrewをインストールしていない場合は下記リンクからインストールしてください。  
  [Homebrew](https://brew.sh/index_ja)
  
- RESTAPIへのリクエスト
  - VSCodeの拡張機能である「REST Client」を使用する
  - .rest拡張子のファイルを作成してリポジトリで管理すると別の開発者もAPIの動作確認がしやすくなる
    - 詳細の使い方については[リンク](https://shiraberu.tech/2021/11/28/vscode-extension-rest/)を参照のこと。　
  

<a id="anchor2"></a>

## Gitブランチ戦略

git-flowをデフォルトとしています。  

### ブランチ一覧

- main
- hotfix
- release branches
- develop
- feature branches

### ブランチルール

- developはmainの最新から作成
- featureはdevelopの最新から作成
- releaseはリリース対象featureマージ済developの最新から作成
- 各featureのマージ先はdevelop
- releaseはリリース時のバージョン調整などに使用
- リリースモジュールはmainから作成
- リリースバージョンが上がるタイミングでreleaseからmainにマージ
- マージ済featureは削除
- hotfixは致命的バグが発生した場合に使用

### ブランチ命名規則

- feature branches : feature/add_new_function/{issue番号} or feature/functional_improvement/{issue番号}
- release branches : release/{tagバージョン}
- hotfix : hotfix/{tagバージョン}

### Tagルール

- メジャーバージョン・マイナーバージョン・累積バージョンで記載する
  - メジャーバージョン
    - add_new_function時に数字を上げるメジャーバージョンを上げた場合はマイナーバージョン・累積バージョンは0に戻す
  - マイナーバージョン
    - functional_improvement時に数字を上げるマイナーバージョンを上げた場合は累積バージョンは0に戻す
  - 累積バージョン
    - hotfix時に数字を上げる


<a id="anchor3"></a>

## 環境の詳細

<a id="anchor4"></a>

## 環境の構築

- リポジトリクローン直後には下記コマンドを実行

~~~sh
make first-up-build
~~~

<a id="anchor5"></a>

## Make基本コマンド一覧

### コンテナ起動・作成系

- コンテナのビルド

~~~sh
make build
~~~

- コンテナのビルドと起動

~~~sh
make build-up
~~~

- コンテナの起動

~~~sh
make up
~~~

- コンテナのリスタート

~~~sh
make restart
~~~

### コンテナ停止・削除系

- コンテナを削除

~~~sh
make down 
~~~

- docker-compose.ymlで記述しているコンテナ・ボリューム・イメージ・ネットワーク全て削除

~~~sh
make down-rmi
~~~

- 全ての未使用なコンテナ, イメージ, ボリューム、ネットワークを一括削除

~~~sh
make down-all
~~~

### コンテナ情報系

- docker-compose.ymlで記述しているコンテナの一覧を表示

~~~sh
make ps
~~~

- docker-compose.ymlで記述しているコンテナサービスログの出力

~~~sh
make logs
~~~

<a id="anchor6"></a>

## etc


<a id="anchor7"></a>

## 参考リンク

- [github-markdown-css CDN](https://cdnjs.cloudflare.com/ajax/libs/github-markdown-css/5.1.0/github-markdown.min.css)
- [Githubで特定のブランチを保護して、直pushや削除を防止する](https://maasaablog.com/development/git/github/2881/#toc3)
