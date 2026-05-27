# Tetsuo Nakae — Portfolio Site

中江 哲夫の個人ポートフォリオサイト（GitHub Pages 公開用）。

- **公開URL（予定）**: https://tetsuN-0320.github.io/
- **デザイン**: 株式会社ダイアローグ研究所ブランド（深紺×橙）
- **構成**: PROFILE / SKILL / SERVICES / WORKS / CONTACT のシングルページ
- **WORKS リンク先**:
  1. [e-Stat 人口動態予測](https://tetsuN-0320.github.io/estat-population-forecast/)
  2. [ふるさと納税 トレンド分析](https://tetsun-0320.github.io/furusato-nozei-trends/)
  3. [Stack Overflow 学習者つまづき分析](https://tetsuN-0320.github.io/stackoverflow-learner-pitfalls/)

---

## ファイル構成

```
portfolio_site/
├── index.html              ← 本体（HTML + CSS インライン）
├── README.md               ← このファイル
└── assets/
    ├── og.png              ← OG画像（1200×630）
    ├── favicon.png         ← ファビコン（モノグラム DI）
    └── profile.jpg         ← プロフィール写真（差し替え推奨／なくても自動でモノグラム表示）
```

`assets/profile.jpg` は **任意**。配置されていない場合は自動的に「TN」というモノグラム表示にフォールバックします。新しいプロフィール写真が撮影でき次第、同名で `assets/profile.jpg` に差し替えてください。

---

## ローカルでのプレビュー

ターミナルで以下を実行し、ブラウザで http://localhost:8000 を開きます。

```bash
cd portfolio_site
python3 -m http.server 8000
```

---

## GitHub Pages への公開手順（初回のみ）

### ステップ 1 — GitHub リポジトリを作成

1. https://github.com/ にログイン
2. 右上の「+」→「New repository」
3. **Repository name**: `tetsuN-0320.github.io`（**この名前のリポジトリ名でなければユーザーサイトになりません**）
4. **Public** を選択（GitHub Pages の無料プランは Public 必須）
5. 「Add a README file」のチェックは **入れない**（後でファイルを push するため）
6. 「Create repository」をクリック

### ステップ 2 — このフォルダの中身を push

ターミナルでこのフォルダ（`portfolio_site/`）に移動し、以下を実行します。

```bash
cd /Users/nakaetetsuo/Library/CloudStorage/Dropbox/portfolio/portfolio_site

# Git の初期化
git init
git add .
git commit -m "Initial commit: portfolio site"

# main ブランチに設定（GitHub Pages のデフォルト）
git branch -M main

# GitHub の自分のリポジトリと紐付け
git remote add origin https://github.com/tetsuN-0320/tetsuN-0320.github.io.git

# push
git push -u origin main
```

> **認証エラーが出た場合**: GitHub は2021年からパスワード認証を廃止しているため、Personal Access Token (PAT) を使います。Settings → Developer settings → Personal access tokens (classic) → Generate new token から `repo` 権限のトークンを発行し、push 時のパスワード欄に貼り付けてください。

### ステップ 3 — GitHub Pages を有効化

1. リポジトリページ → Settings → Pages
2. **Source**: 「Deploy from a branch」を選択
3. **Branch**: `main` / `/ (root)` を選択 → Save
4. 1〜2分待つと https://tetsuN-0320.github.io/ で公開されます

---

## 更新の流れ（2回目以降）

`index.html` などを編集した後：

```bash
cd /Users/nakaetetsuo/Library/CloudStorage/Dropbox/portfolio/portfolio_site
git add .
git commit -m "Update: 変更内容を一言で"
git push
```

push してから1〜2分で本番サイトに反映されます。

---

## ブランドカラー（メンテ用メモ）

| 用途         | カラー                   |
| ---------- | --------------------- |
| プライマリー（深紺） | `#0F2C5C`             |
| セカンダリー（青）  | `#1E5BAC`             |
| アクセント（橙）   | `#FF8C32` / `#FFC857` |
| ウォーム背景     | `#FCF8F2` / `#F5EDE1` |
| ウォームアクセント  | `#CE662A`             |

`index.html` の `<style>` 内 `:root { ... }` の CSS 変数を差し替えれば、サイト全体に反映されます。

---

## 制作メモ

- 参考にしたサイト: https://takanek07.github.io/
- 構成は同サイトを踏襲（PROFILE / SKILL / WORKS / CONTACT）し、SERVICES と「ABOUT 詳細プロフィール」「dken.jp 誘導」を追加
- フォントは `Noto Sans JP` + `Inter`（Google Fonts、CDN）
- フレームワーク不使用（生 HTML + CSS のみ）。ビルド不要
- レスポンシブ対応済み（720px / 640px ブレークポイント）
