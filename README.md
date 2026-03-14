# Monthly AI Update — GitHub Copilot Agent Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

> **対象**: VS Code + GitHub Copilot (Agent mode)
> **言語**: 日本語レポート生成

## 概要

OpenAI / Anthropic / Microsoft / Google / Amazon (AWS) / Meta の 6 社を対象に、指定期間内の AI 関連情報を各社**公式情報源のみ**から収集・分析し、クラウド・オンプレ基盤を担当する **IT 技術者向けのマークダウンレポート**を自動生成する GitHub Copilot Agent Skill です。

### 生成されるレポートの内容

- 📅 **リリースタイムライン** — mermaid Gantt チャートで全トピックのリリース時期を可視化
- 🔍 **注目トピックス** — 注目度の高い順に整理。各トピック 300 文字以内の要点解説＋公式情報源 URL
- 💡 **AI 活用提案サマリー** — IT 技術者が実務で検討できる具体的な活用シナリオ（優先度付き）

---

## 対象読者

クラウドとオンプレの基盤製品の**企画・開発・運用**を担当する IT 技術者

---

## ファイル構成

```text
.
├── README.md                           # このファイル
├── LICENSE                             # MIT ライセンス
├── CONTRIBUTING.md                     # コントリビューションガイド
├── .gitignore
├── reports/                            # 生成レポートの出力先
│   ├── README.md
│   └── ai-update-YYYY-MM.md            # 生成時に保存（.gitignore 対象）
└── .github/
    └── skills/
        └── monthly-ai-update/
            ├── SKILL.md                # スキルのメイン手順（エントリーポイント）
            ├── assets/
            │   └── sources.md          # 各社公式情報源 URL リスト
            └── references/
                └── output-format.md    # レポート出力フォーマット仕様
```

### 各ファイルの役割

| ファイル | 役割 |
| -------- | ---- |
| `reports/` | スキルが生成するレポートファイルの出力先（`ai-update-*.md`） |
| `SKILL.md` | スキルのエントリーポイント。情報収集〜レポート生成の5ステップ手順を定義 |
| `assets/sources.md` | 6社の公式情報源 URL リスト。情報収集時の参照先 |
| `references/output-format.md` | レポートのマークダウン構造・テンプレート・記述ルールを定義 |

---

## 前提条件

- [Visual Studio Code](https://code.visualstudio.com/) 最新版
- [GitHub Copilot](https://github.com/features/copilot) サブスクリプション（Agent mode 対応プラン）
- VS Code で Agent mode が有効になっていること

### 推奨モデル

このスキルは **複数 URL のフェッチ・大量テキストの分析・構造化マークダウンの生成** を行うため、コンテキストウィンドウが大きく tool use に対応したモデルを推奨します。

| 優先度 | モデル | 推奨理由 |
| ------ | ------ | -------- |
| ★★★ 最推奨 | **Claude Sonnet 4.5 / 4.6** | 大容量コンテキスト・高精度な tool use・日本語生成品質が高い |
| ★★☆ | **GPT-4o** | Agent mode での tool use 安定性が高い |
| ★★☆ | **Gemini 1.5 Pro / 2.0 Flash** | 100 万トークンのコンテキスト。大量の収集テキスト処理に有利 |
| ★☆☆ | **Claude Haiku 3.5** | 処理速度優先の場合。要約精度はやや劣る |

> **切り替え方法**: Copilot チャットのモデルセレクターからスキル実行前に変更してください。

---

## インストール・セットアップ

### 方法 A: このリポジトリをそのままワークスペースとして使用

```shell
git clone https://github.com/<your-username>/monthly-ai-update.git
code monthly-ai-update
```

### 方法 B: 既存ワークスペースへのコピー

`monthly-ai-update` ディレクトリごと、対象ワークスペースの `.github/skills/` 以下にコピーします。

```shell
cp -r .github/skills/monthly-ai-update /path/to/your-workspace/.github/skills/
```

---

## 使い方

VS Code の Copilot チャット（Agent mode）で `/` を入力し、`monthly-ai-update` を選択します。

```text
/monthly-ai-update
```

**期間を指定する場合:**

```text
/monthly-ai-update 2026-02
/monthly-ai-update 2026-02-01 to 2026-02-28
```

**期間を省略した場合:** 直近 1 ヶ月（実行日から 30 日前〜今日）が自動設定されます。

### 生成されるファイル名

| 期間指定 | ファイル名 |
| -------- | ---------- |
| 月単位（例: 2026-02） | `ai-update-2026-02.md` |
| カスタム期間 | `ai-update-20260201-20260228.md` |

ファイルは `reports/` ディレクトリに保存されます。

---

## 対象企業と情報源

| 企業 | 主な情報源 |
| ---- | ---------- |
| OpenAI | openai.com/news, platform.openai.com/docs/changelog |
| Anthropic | anthropic.com/news |
| Microsoft | blogs.microsoft.com/ai, azure.microsoft.com/updates, github.blog |
| Google | blog.google/technology/ai, cloud.google.com/blog, deepmind.google |
| Amazon (AWS) | aws.amazon.com/blogs/machine-learning, aws.amazon.com/bedrock/whats-new |
| Meta | ai.meta.com/blog, github.com/meta-llama |

詳細な URL リストは [.github/skills/monthly-ai-update/assets/sources.md](.github/skills/monthly-ai-update/assets/sources.md) を参照してください。

---

## カスタマイズ

### 情報源の追加・変更

`assets/sources.md` を編集して情報源 URL を追加・変更できます。

### 対象企業の追加

1. `assets/sources.md` に新しい企業セクションを追加
2. `SKILL.md` のステップ 2「収集フォーカス」テーブルに企業を追加

### 出力フォーマットの変更

`references/output-format.md` のテンプレートを編集することで、レポートの構成・記述スタイルを変更できます。

---

## ライセンス

[MIT License](./LICENSE) © 2026

---

## コントリビューション

[CONTRIBUTING.md](./CONTRIBUTING.md) をご覧ください。
