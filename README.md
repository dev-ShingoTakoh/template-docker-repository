<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/github-markdown-css/5.1.0/github-markdown.min.css">

# テンプレート

## 概要

## 目次

- [事前準備](#anchor1)
- [Gitブランチ戦略](#anchor2)
- [環境の詳細](#anchor3)
- [環境の構築](#anchor4)
- [etc](#anchor5)
- [参考リンク](#anchor6)

<a id="anchor1"></a>

## 事前準備

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

<a id="anchor5"></a>

## etc

<a id="anchor6"></a>

## 参考リンク

- [github-markdown-css CDN](https://cdnjs.cloudflare.com/ajax/libs/github-markdown-css/5.1.0/github-markdown.min.css)
- [Githubで特定のブランチを保護して、直pushや削除を防止する](https://maasaablog.com/development/git/github/2881/#toc3)
