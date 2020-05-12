# README

## 注意

### forty

ポートを指定してサービス起動するとcssを読まない(デフォルトの1313を使う)

## セットアップ

サイト作成

    $ hugo new site buta7-forty

テーマ設定(テーマをカスタマイズせずそのまま使う場合はsubmodule化がよい)

    $ cd buta7-forty
    $ git init
    $ cd themes
    $ git submodule add https://github.com/MarcusVirg/forty.git

サイト設定

    $ cp -pr ./themes/hugo-theme-dream/exampleSite/* .
    $ cp -pr ./themes/hugo-theme-dream/exampleSite/config.toml .
    vi config.toml
    baseURL = "http://buta7.github.io/buta7-forty/"
    languageCode = "ja"
    title = "Buta7 Web Site by Hugo"
    theme = "forty"

## 使い方

### 投稿

新規投稿

    $ hugo new posts/2020/05/helloworld.md
    content/posts/2020/05/helloworld.md created
    
文書作成

    $ vi content/posts/2020/05/helloworld.md
    
下書きモード解除

    $ vi content/posts/2020/05/helloworld.md
    ...
    draft: false
    ...
    
(古い情報)下書きモード解除

    $ hugo undraft content/posts/2020/05/helloworld.md

固定ページの作成(architypeのabout.mdを使う)

    $ hugo new about/_index.md
    ...
    
上記ファイル構成を元にconfig.tomlのメニューを設定

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

プレビュー(http://localhost:1313)

    $ make run

## Github連携

config.tomlに以下の設定

    baseURL = "https://buta7.github.com/blog-hugo/"
    publishDir = "docs"

公開(githubにプッシュ)

    $ make deploy

## Link

* [Forty \| Hugo Themes](https://themes.gohugo.io/forty/)
