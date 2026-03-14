# コントリビューションガイド

このリポジトリへのコントリビューションを歓迎します。

---

## コントリビューションの種類

- **情報源の追加・修正** — 情報源 URL の追加・変更・廃止URLの更新
- **対象企業の追加** — 新規企業の情報源とフォーカス定義の追加
- **出力フォーマットの改善** — テンプレート・記述ルールの改善提案
- **バグ報告** — スキルの動作不具合の報告

---

## 手順

### 1. Issue の作成

変更内容を事前に Issue で共有してください。  
重複作業を避けるため、実装前に方針を確認します。

### 2. Fork & ブランチ作成

```bash
git clone https://github.com/<your-username>/monthly-ai-update.git
cd monthly-ai-update
git checkout -b feature/your-feature-name
```

ブランチ命名規則:

| 種類 | 命名例 |
| ---- | ------ |
| 情報源追加・修正 | `fix/sources-openai-changelog` |
| 新規企業追加 | `feature/add-ibm-sources` |
| フォーマット改善 | `improve/output-format-timeline` |
| バグ修正 | `fix/skill-step2-fetch-error` |

### 3. 変更の実施

変更対象ファイル:

| 変更内容 | 対象ファイル |
| -------- | ------------ |
| 情報源の追加・修正 | `.github/skills/monthly-ai-update/assets/sources.md` |
| 対象企業の追加 | `assets/sources.md` ＋ `SKILL.md`（ステップ2テーブル） |
| 出力フォーマット変更 | `.github/skills/monthly-ai-update/references/output-format.md` |
| 手順変更 | `.github/skills/monthly-ai-update/SKILL.md` |

### 4. Pull Request の作成

- PR タイトルは変更内容を簡潔に記述してください（日本語可）
- 変更理由・変更内容を PR 本文に記載してください
- 廃止 URL の修正の場合は、旧 URL と新 URL を明記してください

---

## 情報源の追加・修正ガイドライン

- **公式情報源のみ** を追加してください（企業の公式ドメインのもの）
- URL は定期的に変更されることがあります。廃止 URL の修正 PR も歓迎します
- 追加する情報源には「収集内容」（何の情報が得られるか）を必ず記載してください

---

## 行動規範

このプロジェクトでは、オープンで友好的なコミュニティを維持するため、敬意ある丁寧なコミュニケーションをお願いします。

---

## ライセンス

Pull Request を提出することで、あなたの貢献が [MIT License](./LICENSE) のもとで公開されることに同意したものとみなします。
