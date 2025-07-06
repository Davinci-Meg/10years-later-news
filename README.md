# 10年後のネットニュースサイト

## プロジェクト概要
このリポジトリは、**10年後の今日**に配信される未来のニュース記事を、Google スプレッドシートを軽量CMSとして運用し、GitHub Pagesで静的ホスティングするテンプレートを提供します。

## ファイル構成
- `index.html`  
  HTML/CSS/JavaScriptを1ファイルにまとめたメインファイル。

## スプレッドシート設定
1. 新規または既存のGoogle スプレッドシートを用意
2. 以下のテンプレートをA1セルに貼り付け

```csv
id,title,author,date,content,imageUrl,slug,relatedLinks
1,"【未来の東京】地上から木が消えた──温暖化と人口爆発で“地下都市化”が加速","G-NEWS編集部","2045-07-05","太陽の下で木陰を探すことは、もはや“贅沢な記憶”になった。\n10年前、都心の街路樹が姿を消すと誰が予想していただろうか。2045年の東京はもはや地上の都市ではない。…","https://example.com/images/undercity.jpg","future-tokyo","[{\"label\":\"地下で生まれ育った子どもたちの心理的影響 (国立心理研究所レポート)\",\"url\":\"https://example.com/report.pdf\"},{\"label\":\"環境破壊が引き起こす都市設計のパラドクス (東京工業未来大学教授インタビュー)\",\"url\":\"https://example.com/interview\"}]"
```

3. メニュー「ファイル」→「ウェブに公開」→「リンクを取得」→公開設定を自動更新
4. 公開されたURLのシートIDを控える
   ```
   https://docs.google.com/spreadsheets/d/<SPREADSHEET_ID>/gviz/tq?tqx=out:json
   ```

## HTML ファイル利用方法
1. `index.html` を開き、`<script>` 内の `const SHEET_ID = '<あなたのシートID>';` を自分のシートIDに置き換え
2. GitHub Pages用リポジトリ（例: `yourname.github.io`）を作成し、`index.html` をコミット
3. GitHub Pagesの設定で `main` ブランチを公開ブランチに指定
4. 数分待つと `https://yourname.github.io/` で公開され、10年後の今日の記事が表示されます

### 仕組み概要
- ページ読み込み時にJavaScriptがスプレッドシートからJSONを取得
- `date` が「今日＋10年」の記事をフィルタ
- 記事を `<article>` 要素としてレンダリング

## カスタマイズ
- 列を追加して `category` や `tags`、`authorUrl` などを管理
- デザイン調整は `<style>` 内を編集
- CI/CDでビルド時に静的化したい場合はGitHub Actions等を導入
- カスタムドメインを使用する場合は `CNAME` ファイルをルートに追加

---

© 2025 Megumu Isshiki
