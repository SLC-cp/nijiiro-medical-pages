# にじいろ歯科 診療ページ（プレビュー）

にじいろ歯科おとなこども矯正歯科（happy-hahaha.jp）の、診療案内の下層ページ10本の確認用プレビューです。
静的なHTMLで、ビルドは不要です。GitHub Pagesでそのまま表示できます。

## ページ一覧

| No. | ページ | フォルダ | 公開時のURL（案） |
|---|---|---|---|
| 1 | 虫歯治療 | `tooth-decay/` | `/medical/tooth-decay/` |
| 2 | 親知らずの抜歯 | `wisdom-tooth/` | `/medical/wisdom-tooth/` |
| 3 | 歯周病治療 | `periodontal-treatment/` | `/medical/periodontal-treatment/` |
| 4 | 矯正歯科 | `orthodontics/` | `/medical/orthodontics/` |
| 5 | 小児歯科 | `pediatric-dentistry/` | `/medical/pediatric-dentistry/` |
| 6 | 予防歯科 | `preventive-dentistry/` | `/medical/preventive-dentistry/` |
| 7 | ホワイトニング | `whitening/` | `/medical/whitening/` |
| 8 | インプラント | `implant/` | `/medical/implant/` |
| 9 | 入れ歯 | `denture/` | `/medical/denture/` |
| 10 | 訪問診療 | `home-visit/` | `/medical/home-visit/` |

原稿の元は、コンテンツ制作進捗ボード（Googleスプレッドシート）に載っている各Googleドキュメントです。
2026年11月24日時点の原稿から作成しました。

## 構成

```
index.html              … 10ページの一覧
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
| テキストと画像の2カラム（7：3、右が画像） | `<div class="pv-media"><div class="pv-media-body"><p class="txt">…</p></div><figure class="pv-media-img"><img src="../assets/img/ファイル名.jpg" alt="…"></figure></div>` |
| 症例写真（治療前 → 治療後） | `<div class="pv-case">` の中に、治療前の `<figure class="pv-case-img">`、`<span class="pv-case-arrow">`、治療後の `<figure class="pv-case-img">` の順で並べる |
| 料金表 | `<div class="tbl_default"><table>…</table></div>` |
| 注記 | `<p class="txt pv-note">…</p>` |

タイトルと説明文を変えるときは、ページ先頭の `<title>` と `<meta name="description">`を直します。

## 【要確認】について

本文中の黄色い `【要確認：…】` は、医院への確認が必要な箇所です。

- 確認が取れたら、`<mark class="pv-check">…</mark>` ごと、確認した内容に書き換えるか削除します。
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
