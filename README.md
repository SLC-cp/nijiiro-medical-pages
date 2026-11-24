# にじいろ歯科 診療ページ（プレビュー）

にじいろ歯科おとなこども矯正歯科（happy-hahaha.jp）の、診療案内の下層ページ8本の確認用プレビューです。
静的なHTMLで、ビルドは不要です。GitHub Pagesでそのまま表示できます。

## ページ一覧

| No. | ページ | フォルダ | 公開時のURL（案） |
|---|---|---|---|
| 1 | 一般歯科 | `general-dentistry/` | `/medical/general-dentistry/` |
| 2 | 矯正歯科 | `orthodontics/` | `/medical/orthodontics/` |
| 3 | 小児歯科 | `pediatric-dentistry/` | `/medical/pediatric-dentistry/` |
| 4 | 予防歯科 | `preventive-dentistry/` | `/medical/preventive-dentistry/` |
| 5 | ホワイトニング | `whitening/` | `/medical/whitening/` |
| 6 | インプラント | `implant/` | `/medical/implant/` |
| 7 | 入れ歯 | `denture/` | `/medical/denture/` |
| 8 | 訪問診療 | `home-visit/` | `/medical/home-visit/` |

原稿の元は、コンテンツ制作進捗ボード（Googleスプレッドシート）に載っている各Googleドキュメントです。
2026年11月24日時点の原稿から作成しました。

## 構成

```
index.html              … 8ページの一覧
<フォルダ名>/index.html  … 各ページ本体
medical/index.html      … 既存の診療案内ページに、各ページへのリンクボタンを追加した案
assets/preview.css      … プレビュー用の補助スタイル
.nojekyll               … GitHub PagesでJekyll処理を無効にする空ファイル
```

ヘッダー・フッター・見出しなどのデザインは、公開サイトのテーマCSSを直接読み込んでいます。
そのため、インターネットにつながっていないと表示が崩れます。

## 診療案内ページのリンクボタン

`medical/` は、公開中の診療案内（https://happy-hahaha.jp/medical/ ）を2026年11月24日時点で写したものです。
各診療項目の最後に「◯◯ページ」ボタンを追加し、対応する下層ページへ進めるようにしています。
「小児矯正」には専用の下層ページがないため、矯正歯科のページへ進みます。

本番では、テーマの `page.php` に同じボタンを組み込んでいます。下層ページを公開した項目だけ、自動でボタンが出ます。

## 修正のしかた

1. 修正したいページの `index.html` を開きます（GitHub上なら鉛筆アイコンで編集できます）。
2. `ここから本文` と `ここまで本文` のコメントの間を書き換えます。
3. 保存（コミット）すると、数分でGitHub Pagesに反映されます。

本文で使っている主なタグは次のとおりです。

| 内容 | 書き方 |
|---|---|
| 大見出し | `<section id="sec01">` の中の `<h2>…</h2>` |
| 小見出し | `<h3 class="copy kozuka">…</h3>` |
| 本文 | `<p class="txt">…</p>` |
| 箇条書き | `<ul class="list_default pv-list"><li>…</li></ul>` |
| 流れ（ステップ） | `<ol class="pv-flow">` の中に `<li class="pv-flow-item"><h3 class="pv-flow-ttl kozuka">見出し</h3><p class="txt">…</p></li>` を並べる（STEP番号と矢印は自動） |
| 料金表 | `<div class="tbl_default"><table>…</table></div>` |
| 注記 | `<p class="txt pv-note">…</p>` |

タイトルと説明文を変えるときは、ページ先頭の `<title>` と `<meta name="description">`、ページ下部の確認事項ブロックの両方を直します。

## 【要確認】について

本文中の黄色い `【要確認：…】` は、医院への確認が必要な箇所です。

- 確認が取れたら、`<mark class="pv-check">…</mark>` ごと、確認した内容に書き換えるか削除します。
- 各ページ下部の「公開前の確認事項」ブロック（`<aside class="pv-review">`）は、公開時に丸ごと削除します。
- 料金・症例・リスクなどの記載は、医療広告ガイドラインに関わります。公開前に必ず院長の確認を取ってください。

## GitHub Pagesで見る手順

1. GitHubで新しいリポジトリを作成します。
2. このフォルダをプッシュします。
3. リポジトリの Settings → Pages で、Branch を `main`（root）に設定します。
4. 数分後、`https://<ユーザー名>.github.io/<リポジトリ名>/` で一覧ページが表示されます。

## 注意

- すべてのページに `noindex,nofollow` を入れています。プレビュー用で、そのまま本番に使うものではありません。
- 本番（WordPress）への反映は別作業です。本文をWordPressの固定ページに移し、テーマ側でメニューとリンクを張り替えます。
- ページ同士のリンク（例：一般歯科 → 予防歯科）は、このプレビュー内の相対リンクです。本番では `/medical/<フォルダ名>/` に読み替えます。
- 原稿では、診療案内の旧アンカー（`/medical/#medical05` など）へのリンクでした。独立ページ化に合わせて、プレビューでは新しい各ページへのリンクに置き換えています。
- アクセス解析のタグ（Googleアナリティクス・タグマネージャー）は入れていません。
