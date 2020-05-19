# README

## 注意

### forty

ポートを指定してサービス起動するとcssを読まない(デフォルトの1313を使う)

## セットアップ

サイト作成

```shell
hugo new site buta7-forty
```

テーマ設定(テーマをカスタマイズせずそのまま使う場合はsubmodule化がよい)

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

既存のレポジトリからクローンする場合

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
...
draft: false
...
```

(古い情報)下書きモード解除

```shell
hugo undraft content/posts/2020/05/helloworld.md
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

## Github連携

config.tomlに以下の設定

```toml
baseURL = "https://buta7.github.com/blog-hugo/"
publishDir = "docs"
```

公開(githubにプッシュ)

```shell
make deploy
```
## Link

* [Forty \| Hugo Themes](https://themes.gohugo.io/forty/)
