# Getting Started

このガイドは、本リポジトリで記事を執筆・プレビュー・公開するための手順をまとめたものです。

記事を追加して `main` へマージすると、GitHub Actions がサイトをビルドし `gh-pages` ブランチへ配信します。公開サイトは https://jpd365erpsup.github.io/blog/ で確認できます。

## Prerequisites

このガイドでは `git`、`docker`、`docker-compose` を使用します。

### Git

* Windows: [git](https://git-scm.com/download/win) をインストールします。
* Mac: [Homebrew](https://brew.sh/)、[MacPorts](http://www.macports.org/)、または [インストーラー](http://sourceforge.net/projects/git-osx-installer/) でインストールします。
* Linux (Ubuntu): `sudo apt-get install git-core`

### Docker

* Windows / Mac
  * https://www.docker.com/products/docker-desktop
* Linux (Ubuntu)
  * `docker`: https://docs.docker.com/engine/install/ubuntu/
  * `docker-compose`: https://docs.docker.com/compose/install/

次のコマンドが実行できることを確認します。

```shell
$ git
$ docker
$ docker-compose
```

## Clone the repository

```shell
# 作業ディレクトリへ移動
$ cd {YOUR_WORKING_DIR}

# リポジトリをクローン
$ git clone <repository-url>
$ cd <repository>
```

### Initialize the blog theme

テーマ（.css, .js など）は git submodule で管理しています。本ブログは [jpazureid/hexo-theme-jpazure](https://github.com/jpazureid/hexo-theme-jpazure) を使用しています。

```shell
# テーマの初期化・更新
$ git submodule update -i
```

## Site configuration

サイト全体の設定は [_config.yml](../_config.yml) で管理しています。主な項目は次のとおりです。すでに本ブログ向けに設定済みのため、通常は変更不要です。

- `title` / `subtitle`: サイト上部に表示されるタイトルとサブタイトル
- `url` / `github`: 公開 URL（`https://jpd365erpsup.github.io/blog/`）と GitHub リポジトリ
- `root`: サブディレクトリ公開時のルート（`/blog/`）
- `disclaimer`: 各記事末尾に表示される注意書き（記事 front matter で `disableDisclaimer: true` を指定すると非表示）

## Writing articles

記事は `articles/{root-tag}/{slug}.md` に作成します。画像は同名フォルダ `articles/{root-tag}/{slug}/` に置き、相対パスで参照します。

```shell
# 新しいブランチを作成
$ git checkout -b add_article

# 記事を作成・編集
$ vim articles/FinOps-Platform/your-article.md
```

### Start / Stop the local preview server

ローカルプレビューは次のコマンドで起動します。`http://localhost:4000/` で確認できます。ファイルを変更すると自動でリロードされます（ブラウザは手動で再読み込みしてください）。

```shell
# サーバー起動
$ docker-compose up
 ...
blog_1  | INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
```

停止するには `Ctrl+C` のあと `docker-compose down` を実行します。

```shell
$ docker-compose down
```

## Publish

### Commit and create a pull request

```shell
# 変更をコミット
$ git add .
$ git commit -m 'Add article'

# ブランチを push
$ git push origin add_article
```

push 後、`add_article` から `main` への Pull Request を作成します。

### Merge and deploy

`main` にマージされると、GitHub Actions が記事をビルドし、生成されたサイトを `gh-pages` ブランチへアップロードします。ワークフローの実行状況は `Actions` タブで確認できます。

### Result

配信が完了すると、サイトに反映されます。

`https://jpd365erpsup.github.io/blog/`

反映には数分かかる場合があります。404 が表示される場合は、しばらく待ってから再度アクセスしてください。
