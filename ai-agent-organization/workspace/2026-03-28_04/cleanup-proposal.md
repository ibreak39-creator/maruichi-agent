# クリーンアップ提案書
作成日: 2026-03-28
リスク許容度: conservative

---

## サマリー

| アクション | 件数 | リスク |
|-----------|------|--------|
| 削除 | 5 | 低〜中 |
| 移動/修正 | 1 | 中 |
| 作成（必須ファイル追加） | 2 | 低 |
| 保留 | 4 | - |

---

## 削除提案

| # | 対象 | 理由 | 影響範囲 | リスク |
|---|------|------|---------|--------|
| 1 | `ai-agent-organization/workspace/2026-03-28_01/`（空ディレクトリ） | `mail-weapons-vs-using.md` が削除され、空フォルダが残存。機能に影響なし | なし | 低 |
| 2 | `ai-agent-organization/inbox/02_音声/無料コンサル/2025/`（空） | 中身なし。コンサル音声は別途ファイルで管理されている | なし | 低 |
| 3 | `ai-agent-organization/inbox/02_音声/無料コンサル/2026/`（空） | 中身なし | なし | 低 |
| 4 | `ai-agent-organization/inbox/02_音声/MTG/azusaさん/`（空） | 中身なし（azsさんとは別のディレクトリ） | なし | 低 |
| 5 | `ai-agent-organization/inbox/03_知識ベース/00_コンテキストログ/`（空） | 中身なし。用途不明 | なし | 低 |

---

## 移動/修正提案

| # | 現在地 | 移動先 | 理由 | 影響範囲 | リスク |
|---|--------|--------|------|---------|--------|
| 1 | `.claude/skills/.claude/skills/x-analysis.md/SKILL.md` | `.claude/skills/x-analysis/SKILL.md` | パスが `.claude/skills/.claude/skills/x-analysis.md/` という誤ったネスト構造になっている。ディレクトリ名も `x-analysis.md`（拡張子付き）は命名規則違反。正しくは `.claude/skills/x-analysis/` に配置すべき | スキルの呼び出しパスが変わるため、参照箇所の確認が必要 | 中 |

---

## 作成提案（必須ファイルの追加）

| # | 作成場所 | 作成内容 | 理由 | リスク |
|---|---------|---------|------|--------|
| 1 | `organization/operations/` 配下に `daily-starter-DAILY_STARTER/` を新設 | `HISTORY.md`、`learnings.md`、`STATUS.yaml`、`knowledge/knowhow/` を作成 | DAILY_STARTERは `.claude/agents/DAILY_STARTER.md` と `CLAUDE.md` に登録済みだが、organization知識ベースが存在しない | 低 |
| 2 | `organization/operations/` 配下に `today-finisher-TODAY_FINISHER/` を新設 | `HISTORY.md`、`learnings.md`、`STATUS.yaml`、`knowledge/knowhow/` を作成 | TODAY_FINISHERも同様に組織エントリが欠如している | 低 |

---

## 保留（ご判断をお願いいたします）

| # | 対象 | 状況 | 判断が必要な理由 |
|---|------|------|----------------|
| 1 | `ai-agent-organization/shared/common-workflow.md` | どのエージェントからも参照されていない孤立ファイル | 過去に設計されたが現在未使用。削除してよいか、あるいは特定エージェントから参照させるべきかはビジネス判断 |
| 2 | `ai-agent-organization/shared/learnings-index.md` | 同様に孤立ファイル | 全エージェントのlearnings.mdを集約する設計意図があったが現在未使用。廃止か活性化かご判断ください |
| 3 | `organization/operations/paid-note-creator-PAID_NOTE_CREATOR/` | organizationには存在するが、CLAUDE.mdのチーム構成に記載なし。knowledge/ディレクトリもなし | PAID_NOTE_CREATORを正式エージェントとしてCLAUDE.mdに追加登録するか、削除するかご判断ください |
| 4 | `inbox/04_アウトプット/08_販売/` 配下15個の空ディレクトリ | 販売用フォルダの骨格として意図的に作られた可能性がある | 今後ファイルを格納する予定があるなら保持。なければ削除。用途によって判断が変わります |

---

## 実行手順（承認後）

### Step 1: 削除（低リスク・即実行可）
```bash
# 空ワークスペースフォルダ
rmdir "ai-agent-organization/workspace/2026-03-28_01"

# inbox空ディレクトリ群
rmdir "ai-agent-organization/inbox/02_音声/無料コンサル/2025"
rmdir "ai-agent-organization/inbox/02_音声/無料コンサル/2026"
rmdir "ai-agent-organization/inbox/02_音声/MTG/azusaさん"
rmdir "ai-agent-organization/inbox/03_知識ベース/00_コンテキストログ"
```

### Step 2: スキルの移動/修正（要確認）
```bash
# 正しいパスにディレクトリを作成してSKILL.mdを移動
mkdir -p ".claude/skills/x-analysis"
mv ".claude/skills/.claude/skills/x-analysis.md/SKILL.md" ".claude/skills/x-analysis/SKILL.md"
rm -rf ".claude/skills/.claude"
```

### Step 3: 必須ディレクトリの作成（低リスク）
- `organization/operations/daily-starter-DAILY_STARTER/` の作成
- `organization/operations/today-finisher-TODAY_FINISHER/` の作成

### Step 4: 保留項目の確認
- [ ] `shared/common-workflow.md` の扱いをご決定ください
- [ ] `shared/learnings-index.md` の扱いをご決定ください
- [ ] `PAID_NOTE_CREATOR` の正式化または削除をご決定ください
- [ ] `inbox/08_販売/` 配下の空ディレクトリを保持するかご決定ください
