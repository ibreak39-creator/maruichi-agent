# ディレクトリ監査レポート
監査日: 2026-03-28
対象: c:\Users\81804\product\maruichi-agent（プロジェクトルート）

---

## サマリー

| 重大度 | 件数 |
|--------|------|
| CRITICAL | 6 |
| WARNING | 5 |
| INFO | 2 |
| **合計** | **13** |

---

## CRITICAL（機能影響）

| # | カテゴリ | パス | 問題内容 |
|---|---------|------|---------|
| 1 | 必須ファイル欠損 | `organization/operations/paid-note-creator-PAID_NOTE_CREATOR/` | `knowledge/` ディレクトリが存在しない。learnings.mdはルート直下にあるが、knowledge/knowhow/ 構造が未整備 |
| 2 | 必須ファイル欠損 | `organization/` 配下全体 | DAILY_STARTER・TODAY_FINISHER の organization エントリが存在しない。`.claude/agents/` にはMDがあるが、organization配下に対応ディレクトリ（知識ベース）がない |
| 3 | 構造破損 | `.claude/skills/.claude/skills/x-analysis.md/SKILL.md` | スキルディレクトリが誤ったパスに配置されている。`.claude/skills/` 直下に置くべきところ、`.claude/skills/.claude/skills/` という不正なネスト構造になっている |
| 4 | 命名規則違反（CRITICAL） | `.claude/skills/.claude/skills/x-analysis.md/` | ディレクトリ名が `x-analysis.md`（拡張子付き）。スキルディレクトリは小文字ケバブケースで拡張子なしが規約 |
| 5 | 空ディレクトリ | `ai-agent-organization/workspace/2026-03-28_01/` | ファイルが0件（git statusでも `mail-weapons-vs-using.md` が削除済みとなっており、空フォルダが残存） |
| 6 | 孤立ファイル（CRITICAL） | `ai-agent-organization/shared/common-workflow.md` | どのエージェントMDからも参照されていない孤立ファイル（memory記録より既知の問題） |

---

## WARNING（品質影響）

| # | カテゴリ | パス | 問題内容 |
|---|---------|------|---------|
| 1 | 空ディレクトリ群 | `inbox/02_音声/無料コンサル/2025/`、`inbox/02_音声/無料コンサル/2026/`、`inbox/02_音声/MTG/azusaさん/` | いずれも中身が0件の空ディレクトリ |
| 2 | 空ディレクトリ群 | `inbox/04_アウトプット/04_X画像/`、`inbox/04_アウトプット/05_Note/有料/`、`inbox/04_アウトプット/05_Note/無料/`、`inbox/04_アウトプット/06_Note画像/` | 中身が0件の空ディレクトリ |
| 3 | 空ディレクトリ群（販売） | `inbox/04_アウトプット/08_販売/` 配下15ディレクトリ（各商品の `00_販売前企画/`〜`03_レター/`） | 販売フォルダ配下のほぼ全サブディレクトリが空 |
| 4 | 孤立ファイル | `ai-agent-organization/shared/learnings-index.md` | どのエージェントからも参照されていない（memory記録より既知） |
| 5 | エージェント整合性 | `organization/operations/paid-note-creator-PAID_NOTE_CREATOR/` | CLAUDE.mdのチーム構成表に `PAID_NOTE_CREATOR` の記載なし。`.claude/agents/PAID_NOTE_CREATOR.md` は存在するが、公式エージェントとして登録されていない |

---

## INFO（軽微）

| # | カテゴリ | パス | 問題内容 |
|---|---------|------|---------|
| 1 | 孤立ファイル | `inbox/03_知識ベース/00_コンテキストログ/`（空） | コンテキストログ格納先が空のまま運用されている |
| 2 | 構造的不整合 | `inbox/04_アウトプット/00_メルマガ/01_一斉配信/` | 過去の成果物（inbox）と新規のworkspace成果物が二重に存在する運用になっている。inboxのアウトプットは `workspace/` に一元化されつつあるが、移行が途中 |

---

## 検出されなかった問題

- `.DS_Store`: プロジェクトルートに存在しないことを確認（以前のmemory記録では存在していたが、現時点では確認されず）
- `*.bak`, `*.tmp`: 存在しない
- 90日以上古いworkspaceファイル: workspace/の最古が2026-03-22のため該当なし
- エージェントMDの命名規則: 全て大文字スネークケースで適合

---

## 構造サマリー

```
.claude/
├── agents/           # 15ファイル（PAID_NOTE_CREATORがCLAUDE.mdに未登録）
└── skills/
    ├── .claude/      # 【異常】誤配置されたスキルディレクトリ
    │   └── skills/
    │       └── x-analysis.md/   # ディレクトリ名に拡張子付き（CRITICAL）
    └── [正常なスキル37個]

ai-agent-organization/
├── inbox/            # 空ディレクトリ多数（WARNING）
├── organization/
│   ├── BOSS/         # 正常
│   ├── OVERSEER/     # 正常
│   ├── hr-tech/      # 正常（GENESIS, ARCHITECT）
│   └── operations/   # DAILY_STARTER/TODAY_FINISHERのエントリなし（CRITICAL）
├── shared/
│   ├── common-workflow.md    # 孤立ファイル（CRITICAL）
│   ├── learnings-index.md    # 孤立ファイル（WARNING）
│   ├── knowledge/    # 正常（6ファイル）
│   └── templates/    # 正常
├── system/           # 正常
└── workspace/        # 2026-03-28_01が空（CRITICAL）
```
