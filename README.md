# KIYOMITSU サイト — デプロイ手順

## ファイル構成

```
style.css          ← 共通デザイン（すべてのHTMLが参照）
index.html         ← トップページ（H1: 奇門遁甲の研究と実践）
kimon-theory.html  ← 奇門遁甲とは（SEO最重要ページ）
trust.html         ← 奇門遁甲は怖い？危険？（SEO 2位）
compare.html       ← 占術の比較（九星気学・四柱推命との違い）
service.html       ← サービス一覧（coconala誘導）
profile.html       ← プロフィール
faq.html           ← よくある質問（アコーディオン式）
contact.html       ← お問い合わせ（Formspree連携）
privacy.html       ← プライバシーポリシー
legal.html         ← 特定商取引法に基づく表記
```

---

## 無料公開の方法（GitHub Pages）

### ① GitHubアカウントを作成
https://github.com にアクセスして無料アカウントを作成。

### ② 新しいリポジトリを作成
- 「New repository」をクリック
- リポジトリ名を `kiyomitsu` または `kiyomitsu-site` に設定
- 「Public」を選択
- 「Create repository」をクリック

### ③ ファイルをアップロード
- リポジトリページで「Add file → Upload files」をクリック
- このフォルダのファイルをすべて選択してドラッグ&ドロップ
- 「Commit changes」をクリック

### ④ GitHub Pages を有効化
- リポジトリの「Settings」→「Pages」
- Source: 「Deploy from a branch」→ Branch: `main` / `(root)`
- 「Save」をクリック

### ⑤ 公開完了
数分後に `https://[あなたのGitHubユーザー名].github.io/kiyomitsu/` で公開されます。

---

## カスタムドメインを使う場合（推奨）

1. お名前.com / Google Domains などでドメイン取得（例: `kiyomitsu.jp`）
2. GitHub Pages の Settings → Pages → Custom domain に入力
3. DNSの設定でGitHub PagesのIPを向ける

SEO的にはカスタムドメインの方が大幅に有利です。

---

## お問い合わせフォームの設定（Formspree）

1. https://formspree.io で無料アカウント作成
2. 「New Form」でフォームを作成
3. 発行されたフォームIDを `contact.html` の以下の箇所に入力：
   ```html
   <form action="https://formspree.io/f/【ここにID】" method="POST">
   ```

---

## Google Search Console への登録

1. https://search.google.com/search-console にアクセス
2. 「プロパティを追加」でサイトURLを入力
3. 「HTMLタグ」方式で認証コードを取得
4. `index.html` の `<head>` 内に貼り付け
5. サイトマップURL `https://[あなたのURL]/sitemap.xml` を送信

---

## Google Analytics の設定

1. https://analytics.google.com でアカウント作成
2. 測定ID（G-XXXXXXXXXX）を取得
3. 各HTMLファイルの `</head>` 直前に以下を追加：
   ```html
   <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
   <script>
     window.dataLayer = window.dataLayer || [];
     function gtag(){dataLayer.push(arguments);}
     gtag('js', new Date());
     gtag('config', 'G-XXXXXXXXXX');
   </script>
   ```

---

## SEO済みの設定一覧

✅ 全ページに `<title>` タグ（キーワード含む）
✅ 全ページに `<meta name="description">` （120字以内）
✅ H1 に「奇門遁甲」キーワードを含む
✅ H2/H3 で記事構造を明確化
✅ 全ページに `<link rel="canonical">` ← ドメイン確定後に更新
✅ URLが英字スラッグ（.html拡張子）
✅ 内部リンク：全ページ相互リンク済み
✅ モバイル対応（レスポンシブデザイン）
✅ 特定商取引法・プライバシーポリシー完備
✅ coconala・note・X への外部リンク

## カスタマイズについて

デザインや内容を変更したい場合は、Claude（claude.ai）にファイルをアップロードして「〇〇を変更してください」と依頼するのが最も簡単です。
