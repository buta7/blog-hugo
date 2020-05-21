# README

## 注意

### forty

ポートを指定してサービス起動するとcssを読まない(デフォルトの1313を使う)

## セットアップ

サイト作成

```shell
hugo new site buta7-forty
```

テーマ設定

```shell
cd buta7-forty
git init
cd themes
git submodule add https://github.com/MarcusVirg/forty.git
```

サイト設定

```shell
cp -pr ./themes/hugo-theme-dream/exampleSite/* .
cp -pr ./themes/hugo-theme-dream/exampleSite/config.toml .
```
config.toml

```toml
baseURL = "http://buta7.github.io/buta7-forty/"
languageCode = "ja"
title = "Buta7 Web Site by Hugo"
theme = "forty"
```

> github pagesやnetlifyで使う場合はbaseURLのプロトコルはhttpsにすること

Githubレポジトリ作成後

```shell
cp somplace/{Makefile,deploy.sh} .
git remote add origin git@github.com:higebobo/hugo-frances.git
make deploy
```

Github>Settings>Gighub Pages>Source>gh-pages branch

## Github Actionsの利用

* .github/workflows/gh-pages.yamlを作成
    * ソースはmasterブランチ
    * 出力はpublicフォルダの内容をgh-pagesブランチ

## 既存のレポジトリからクローンする場合

```shell
git clone git@github.com:buta7/hugo-forty.git buta7-forty
cd buta7-forty/
git submodule update --init --recursive
```

## 使い方

### 投稿

新規投稿

```shell
hugo new posts/2020/05/helloworld.md
content/posts/2020/05/helloworld.md created
```

文書作成

```shell
vi content/posts/2020/05/helloworld.md
```

下書きモード解除

```shell
vi content/posts/2020/05/helloworld.md
draft: false
```


固定ページの作成(architypeのabout.mdを使う)

```shell
hugo new about/_index.md
```

上記ファイル構成を元にconfig.tomlのメニューを設定

```toml
[[menu.main]]
  name = "Blog"
  url = "posts"
  weight = 1

[[menu.main]]
  name = "Tags"
  url = "tags"
  weight = 2

[[menu.main]]
  name = "About"
  url = "page/about/"
  weight = 3
```

プレビュー(http://localhost:1313)

```shell
make run
```

公開(githubにプッシュ)

```shell
make deploy
```
## Link

* [Forty \| Hugo Themes](https://themes.gohugo.io/forty/)
