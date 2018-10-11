# CSSの作成方法

```bash
npm run css-build
```

https://bulma.io/documentation/customize/with-node-sass/

## パラメータ

### グローバル

* `tagMark`: タグに付くマーク
    * 例: 将棋のコマ(先手): "&#x2617;"
* `showSectionToTitle`: タイトルにセクション名を付けるかどうか(デフォルト: false)
* `showTocDefault`: デフォルトで目次を表示するかどうか(デフォルト: false)
* `showTocWords`: 目次を表示するかどうかの基準(デフォルト: 200語)
* `navbarColor`: Navbarのカラー
    * https://bulma.io/documentation/components/navbar/
* `getTagTitleFromSections`: タグ名を上書きするセクション(Array)
* `useAdsense`: Google AdSenseを使用可能にするかどうか(デフォルト: true)

#### トップページ

* `topPageType`: トップページのタイプ(デフォルト: `latestArticles`)
    * `latestArticles`: 最新記事一覧
    * `contentsOnly`: コンテンツのみ
* `latestPageNum`: トップページに表示される最新の数(デフォルト: 10)
* `latestPageBy`: トップページに表示される記事のソート順(デフォルト: lastmod)
    * 現在指定可能なのは`date`のみ。
* `showTagsOnTopPage`: トップページにタグ一覧を出力するかどうか(デフォルト: false)

### セクション

セクションの`_index.md`に設定します。

* `showtitle`: タイトルにセクション名を設定するかどうか(デフォルト: true)
* `grouping`: グループ化して表示するかどうか(デフォルト: false)
* `orderby`: ソート方法(デフォルト: `title`)
    * `title`: タイトル
    * `date`: 作成日

### 記事

各記事に設定します。

* `noadsense`: trueにすると、その記事ではGoogle AdSenseを表示しません。
* `toc`: 目次を表示するかどうか
    * config.tomlの `showTableOfContents` より優先されます。

## テーマのカスタマイズ方法

テーマディレクトリ以下の `assets/sass/custom.scss` を、
Hugoのルートディレクトリ以下の `assets/sass/custom.scss` としてコピーします。

そのあと、SCSSファイルをカスタマイズしてください。
ただし先頭の以下の2行は消さないでください。

```
@charset "utf-8";
@import "./main.scss";
```

Netlifyにデプロイする時は以下のようにしてください。

```bash
hugo
git rm -r resources/_gen/assets/scss/sass
git add -f resources/_gen/assets/scss/sass
git commit
```
