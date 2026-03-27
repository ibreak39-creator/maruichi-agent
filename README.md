# x-note Agent Team Template

**note×X（旧Twitter）の収益化を自動化する、Claude Code Agent Teamsテンプレート**

Claude Code の Agent Teams 機能（Opus 4.6）に最適化された、12体のAIエージェントが連携して動作する組織テンプレートです。

---

## 何ができるのか

- note記事の作成・レビュー・装飾を自動パイプライン処理
- X投稿（宣伝・オリジナル・長文・短文）を並列生成
- KPI分析・PDCA・コンテンツ企画・競合調査を一括依頼
- 副業収益化の戦略壁打ち・日次タスク提案
- メルマガ・セールスレターの一気通貫作成

---

## エージェント一覧

| 役割 | エージェント | 担当 |
|------|------------|------|
| Team Lead | **BOSS（司）** | タスク管理・チーム調整・戦略判断 |
| Teammate | **NOTE_CREATOR（紡）** | note記事作成 |
| Teammate | **ARTICLE_REVIEWER（冴）** | 記事レビュー・評価 |
| Teammate | **ARTICLE_STYLIST（彩葉）** | 記事装飾・CTA配置・ハッシュタグ |
| Teammate | **DATA_ANALYST（鑑）** | データ収集・X analytics分析 |
| Teammate | **X_POST_CREATOR（響也）** | X投稿作成 |
| Teammate | **ARCHITECT（匠）** | プロンプト設計・スキル作成 |
| Teammate | **GENESIS（創）** | エージェント設計・作成 |
| Teammate | **GUNSHI（官兵衛）** | 副業全体戦略・参謀コンサルタント |
| Teammate | **OVERSEER（整）** | ディレクトリ構造管理・監査 |
| Teammate | **MAIL_CREATOR（文）** | メールマガジン作成（通常・セールス） |
| Teammate | **LETTER_CREATOR（筆）** | セールスレター作成（商品LP・販売ページ） |

---

## クイックスタート

### 2. 自分の情報を設定

Claude Code に「組織を作って」と話しかけると `setup-org` スキルが自動起動。
対話形式でヒアリングしながら、以下の情報を全エージェントに自動反映する：

- Xアカウント・noteアカウント情報
- ターゲット読者・ペルソナ定義
- 文体・トーン・一人称
- 権威性・実績
- 商品・マネタイズ設計
- コンテンツテーマ・専門領域

### 3. Claude Codeで使い始める

```bash
# 副業戦略を相談したい
claude "戦略を考えたい"

# note記事を作る（→ ARTICLE_STYLISTまで自動連動）
claude "note記事を書いて：[テーマ]"

# X投稿とnote記事を同時作成
claude "note記事とX投稿を同時に作って：[テーマ]"

# 今日やるべきことを確認
claude "今日何するべき？"
```

---

## タスクルーティング

| キーワード | 担当エージェント | スキル |
|-----------|----------------|--------|
| 記事作成、note記事、ブログ | NOTE_CREATOR → ARTICLE_STYLIST（自動連動） | `note-creation` |
| 記事レビュー、評価、レビューして | ARTICLE_REVIEWER | `content-review` |
| 記事装飾、CTA、ハッシュタグ | ARTICLE_STYLIST | - |
| データ収集、データ分析 | DATA_ANALYST | - |
| X分析、analytics、ツイートの数字 | DATA_ANALYST | `x-analytics-analysis` |
| X投稿、ツイート、note宣伝 | X_POST_CREATOR | - |
| プロンプト、スキル作成、SKILL.md | ARCHITECT | `skill-creator` / `prompt-*` |
| エージェント作成 | GENESIS | - |
| 壁打ち、戦略、方向性、商品設計 | GUNSHI | `note-strategy-sparring` |
| コンテンツ企画、記事のネタ、タイトル案 | GUNSHI | `note-content-planning` |
| KPI、PDCA、今月の結果、改善点 | GUNSHI | `note-kpi-pdca` |
| 競合分析、市場調査 | GUNSHI | `note-competitor-analysis` |
| 投稿ネタ、投稿スケジュール、ローンチ投稿 | GUNSHI | `post-schedule-planning` |
| 今日何するべき、優先タスク | BOSS + GUNSHI | `daily-strategy` |
| ディレクトリ監査、ヘルスチェック、整理整頓 | OVERSEER | `directory-audit` / `health-report` |
| メルマガ作成、メルマガを書いて、メール配信 | MAIL_CREATOR | `regular-newsletter` |
| セールスメルマガ、ステップメール、3日間メール | MAIL_CREATOR | `sales-newsletter` |
| レター作成、セールスレター、販売ページ、LP文章 | LETTER_CREATOR | `letter-creation` |
| 状況報告、ステータス確認 | BOSS | `status-report` |
| タスク依頼、これやって | BOSS | `task-request` |

---

## 並列実行パターン

```
記事作成（必須連動）:  NOTE_CREATOR → ARTICLE_STYLIST（常にセット）
フルパイプライン:      NOTE_CREATOR → ARTICLE_REVIEWER → ARTICLE_STYLIST
並列作成:             NOTE_CREATOR + X_POST_CREATOR（同時生成）
ファンアウト:          BOSS → NOTE_CREATOR + X_POST_CREATOR + DATA_ANALYST
```

---

## エージェント詳細

各エージェントの担当スキルと保有するKnowledgeの一覧です。

### BOSS（司）— Team Lead

**担当スキル**: `task-manager` / `task-analyzer` / `daily-strategy` / `status-report`

**Knowledge**
```
organization/BOSS/knowledge/
└── knowhow/
    ├── business-strategy-2025-2026.md  # 副業戦略・商品ライン・収益シミュレーション
    ├── strategy-brief.md               # マスター戦略ブリーフ・次のアクション
    └── strategy-overview.md            # X×noteファネル全体像・エージェント連携フロー
```

---

### NOTE_CREATOR（紡）— note記事作成

**担当スキル**: `note-creation` / `rewriter`

**Knowledge**
```
organization/operations/note-creator-NOTE_CREATOR/knowledge/
├── knowhow/
│   ├── writing-style-profile.md       # AI臭さ排除ルール・文章設計思想（最重要）
│   ├── article-creation-process.md    # 記事作成の基本7ステップ
│   ├── lead-text-patterns.md          # リード文10パターン・パンチライン配置
│   ├── sentence-ending-patterns.md    # 語尾リスト（連続防止用）
│   ├── improvement-checklist.md       # 改善チェックリスト
│   └── creator-achievements.md        # 権威性フレーズ集
└── examples/                          # 参考note記事（複数）

shared/knowledge/
├── noteの心得.md                       # note公式方針・一次情報優先ルール
├── anti-ai-rewrite-master.md          # AI臭さ排除マスタープロンプト
├── hook-design-principles.md          # フック設計原則・7パターン
└── 教育大全.md                         # 顧客教育5段階（見出し設計時に参照）
```

---

### ARTICLE_REVIEWER（冴）— 記事レビュー

**担当スキル**: `content-review`

**Knowledge**
```
organization/operations/article-reviewer-ARTICLE_REVIEWER/knowledge/
├── knowhow/
│   ├── review-criteria.md             # 品質基準・AIっぽさチェック・禁止事項
│   ├── strategy-brief.md              # ターゲット適合性評価軸
│   └── brand-check-criteria.md        # ブランディング原則・絶対使わない表現
└── examples/
    ├── persona-01-problem-solver.md   # ペルソナ①：即課題解決型
    ├── persona-02-skill-investor.md   # ペルソナ②：スキル投資・成長型
    ├── persona-03-community-seeker.md # ペルソナ③：つながり・共感型
    └── persona-04-roi-optimizer.md    # ペルソナ④：ROI最適化型

shared/knowledge/
├── x-note-brand-strategy.md          # ブランド戦略・絶対使わない表現
└── noteの心得.md
```

---

### ARTICLE_STYLIST（彩葉）— 記事装飾・CTA配置

**担当スキル**: なし（NOTE_CREATORから自動連動）

**Knowledge**
```
organization/operations/article-stylist-ARTICLE_STYLIST/knowledge/
├── knowhow/
│   ├── styling-guidelines.md          # 装飾ルール・構成テンプレート（水平線禁止）
│   └── cta-and-navigation.md          # CTA配置基準・回遊設計3点リンク・LOOP誘導
└── examples/
    ├── note-articles-catalog.md       # 関連記事リンク挿入用カタログ
    └── loop-salon-info.md             # LOOP誘導CTA作成用

shared/knowledge/
├── anti-ai-rewrite-master.md
└── noteの心得.md
```

---

### DATA_ANALYST（鑑）— データ分析

**担当スキル**: `x-analytics-analysis`

**Knowledge**
```
organization/operations/data-analyst-DATA_ANALYST/knowledge/
└── knowhow/
    ├── strategy-brief.md              # KPI設計・計測方法・収益直結指標
    └── analysis-methods.md            # データ分析手法
```

---

### X_POST_CREATOR（響也）— X投稿作成

**担当スキル**: `x-note-promo` / `x-long-post` / `x-short-post`

**Knowledge**
```
organization/operations/x-post-creator-X_POST_CREATOR/knowledge/
├── knowhow/
│   ├── writing-style-profile.md       # 発信者の文体・口調（骨格理解が最優先）
│   ├── x-post-best-practices.md       # ベストプラクティス（ハッシュタグ禁止等）
│   ├── x-operation-guide.md           # X運用ガイド・4カテゴリ・3段階設計
│   └── sentence-ending-patterns.md    # 語尾リスト
└── examples/
    ├── x-post-example-1.md
    └── x-post-example-2.md

shared/knowledge/
├── hook-design-principles.md
└── noteの心得.md
```

---

### ARCHITECT（匠）— プロンプト設計・スキル作成

**担当スキル**: `prompt-creator-unified` / `prompt-analyzer` / `prompt-improver` / `skill-creator`

**Knowledge**
```
organization/hr-tech/prompt-engineer-ARCHITECT/knowledge/
├── knowhow/
│   ├── prompt-engineering-principles.md  # 設計原則
│   ├── prompt-patterns.md                # パターン集
│   └── skill-building-guide.md           # スキル構築ガイド
└── examples/
    ├── 口調プロファイリングくん.md
    ├── マインドマップ作るくん.md
    ├── バリューラダー構築くん.md
    └── ローンチスケジュール作るくん.md
```

---

### GENESIS（創）— エージェント設計・作成

**担当スキル**: `prompt-creator-unified`

**Knowledge**
```
organization/hr-tech/agent-designer-GENESIS/knowledge/
└── knowhow/
    ├── agent-design-principles.md     # エージェント設計原則
    └── personality-patterns.md        # 人格設計パターン集
```

---

### GUNSHI（官兵衛）— 副業戦略参謀

**担当スキル**: `note-strategy-sparring` / `note-content-planning` / `note-kpi-pdca` / `note-competitor-analysis` / `post-schedule-planning`

**動作モード**
| キーワード | モード |
|-----------|--------|
| 壁打ちしたい、戦略を考えたい | 戦略壁打ちモード |
| 記事のネタ、タイトル案 | コンテンツ企画モード |
| KPIを見て、数字を振り返りたい | KPI・PDCAモード |
| 競合を調べたい、市場はどうなっている | 競合分析モード（Web検索活用） |
| 投稿ネタ、スケジュール設計 | 投稿計画モード |

**Knowledge**
```
organization/operations/gunshi-GUNSHI/
└── learnings.md                       # 蓄積された戦略知見

shared/knowledge/
└── x-note-brand-strategy.md
```

---

### OVERSEER（整）— ディレクトリ構造管理

**担当スキル**: `directory-audit` / `cleanup-proposal` / `structure-optimizer` / `health-report`

**Knowledge**
```
organization/OVERSEER/knowledge/
└── knowhow/
    └── strategy-brief.md              # 監査基準・構造規約・命名規則
```

> **絶対ルール**: 自動削除禁止。必ず提案ベースで、影響範囲を明示する。

---

### MAIL_CREATOR（文）— メルマガ作成

**担当スキル**: `regular-newsletter` / `sales-newsletter`

**Knowledge**
```
organization/operations/mail-creator-MAIL_CREATOR/knowledge/
├── knowhow/
│   └── writing-style-profile.md       # 発信者の文体プロファイル（setup-orgで記入）
└── examples/
    ├── example-01.md                  # メルマガ事例①
    └── example-02.md                  # メルマガ事例②

shared/knowledge/
└── hook-design-principles.md
```

---

### LETTER_CREATOR（筆）— セールスレター作成

**担当スキル**: `letter-creation`

**Knowledge**
```
organization/operations/letter-creator-LETTER_CREATOR/knowledge/
├── knowhow/
│   └── writing-style-profile.md       # 発信者の文体プロファイル（setup-orgで記入）
└── examples/
    ├── example-01.md                  # レター事例①（構成のみ参照・内容流用禁止）
    └── example-02.md                  # レター事例②（構成のみ参照・内容流用禁止）

shared/knowledge/
└── hook-design-principles.md
```

---

## スキル一覧

`.claude/skills/` に収録されている自動発動スキル（29スキル）：

| カテゴリ | スキル | 概要 |
|---------|--------|------|
| note作成 | `note-creation` | 見出し構成→本文をステップバイステップで作成 |
| note作成 | `note-content-planning` | テーマ・タイトル候補をリスト提示 |
| note作成 | `rewriter` | 既存記事のリライト・トーン変換 |
| 戦略・分析 | `note-strategy-sparring` | ビジネス戦略の対話型壁打ち |
| 戦略・分析 | `note-kpi-pdca` | KPI集計・PDCA提案 |
| 戦略・分析 | `note-competitor-analysis` | 競合分析・市場調査（Web検索活用） |
| 戦略・分析 | `x-analytics-analysis` | X Analytics CSVデータ分析 |
| 戦略・分析 | `post-schedule-planning` | 投稿ネタ出し→スケジューリング |
| レビュー | `content-review` | 4ペルソナによるコンテンツ評価 |
| X投稿 | `x-note-promo` | note記事のX宣伝投稿作成 |
| X投稿 | `x-long-post` | ノウハウ系X長文投稿作成 |
| X投稿 | `x-short-post` | 140文字以内の短文投稿3案作成 |
| メルマガ | `regular-newsletter` | 通常メルマガ作成 |
| メルマガ | `sales-newsletter` | 9通のセールスステップメール作成 |
| レター | `letter-creation` | セールスレター・商品LP文章作成 |
| プロンプト | `prompt-creator-unified` | 新規プロンプト設計・作成 |
| プロンプト | `prompt-analyzer` | プロンプトの問題点詳細分析 |
| プロンプト | `prompt-improver` | 既存プロンプトの改善版作成 |
| プロンプト | `skill-creator` | SKILL.md形式への変換・新規スキル設計 |
| 組織管理 | `setup-org` | 組織初期化・全ファイル生成（ヒアリング形式） |
| 組織管理 | `directory-audit` | 空ディレクトリ・重複・命名違反を検出 |
| 組織管理 | `cleanup-proposal` | 削除・統合・移動の具体的アクション提案 |
| 組織管理 | `structure-optimizer` | 構造の可視化・5観点スコアリング |
| 組織管理 | `health-report` | 6指標100点満点・S〜D判定 |
| 組織管理 | `status-report` | 組織全体のステータス一覧表示 |
| タスク管理 | `task-request` | タスク依頼→最適エージェント分配→実行 |
| タスク管理 | `task-manager` | 複合タスク分解・チームメイト割当設計 |
| タスク管理 | `task-analyzer` | タスク内容分析・最適エージェント判定 |
| タスク管理 | `daily-strategy` | 今日・今週のタスク提案（BOSS+GUNSHI連携） |

---

## ディレクトリ構造

```
x-note-agent-team/
│
├── CLAUDE.md                              # エージェント組織設定（Claude Code読み込み）
│
├── .claude/
│   ├── agents/                            # Claude Code Agent定義（12体）
│   │   ├── BOSS.md
│   │   ├── NOTE_CREATOR.md
│   │   ├── ARTICLE_REVIEWER.md
│   │   ├── ARTICLE_STYLIST.md
│   │   ├── DATA_ANALYST.md
│   │   ├── X_POST_CREATOR.md
│   │   ├── ARCHITECT.md
│   │   ├── GENESIS.md
│   │   ├── GUNSHI.md
│   │   ├── OVERSEER.md
│   │   ├── MAIL_CREATOR.md
│   │   └── LETTER_CREATOR.md
│   │
│   └── skills/                            # スキル定義（29スキル）
│       ├── note-creation/
│       ├── note-content-planning/
│       ├── rewriter/
│       ├── content-review/
│       ├── x-analytics-analysis/
│       ├── x-note-promo/
│       ├── x-long-post/
│       ├── x-short-post/
│       ├── post-schedule-planning/
│       ├── note-strategy-sparring/
│       ├── note-kpi-pdca/
│       ├── note-competitor-analysis/
│       ├── regular-newsletter/
│       ├── sales-newsletter/
│       ├── letter-creation/
│       ├── prompt-creator-unified/
│       ├── prompt-analyzer/
│       ├── prompt-improver/
│       ├── skill-creator/
│       ├── setup-org/
│       ├── directory-audit/
│       ├── cleanup-proposal/
│       ├── structure-optimizer/
│       ├── health-report/
│       ├── status-report/
│       ├── task-request/
│       ├── task-manager/
│       ├── task-analyzer/
│       └── daily-strategy/
│
└── ai-agent-organization/
    │
    ├── inbox/                             # 未処理タスク・CSVデータの投入先
    │
    ├── system/
    │   └── config.yaml                    # システム設定
    │
    ├── shared/
    │   ├── knowledge/                     # 全エージェント共通知識
    │   │   ├── noteの心得.md              # note公式方針・一次情報優先ルール
    │   │   ├── anti-ai-rewrite-master.md  # AI臭さ排除マスタープロンプト
    │   │   ├── x-note-brand-strategy.md   # X×noteブランド戦略・絶対使わない表現
    │   │   ├── hook-design-principles.md  # フック設計原則・7パターン
    │   │   └── 教育大全.md                # 顧客教育5段階フレームワーク
    │   └── templates/
    │       └── agent-template/
    │           └── STATUS-TEMPLATE.yaml
    │
    ├── organization/
    │   │
    │   ├── BOSS/
    │   │   ├── knowledge/knowhow/
    │   │   │   ├── business-strategy-2025-2026.md
    │   │   │   ├── strategy-brief.md
    │   │   │   └── strategy-overview.md
    │   │   ├── directives/                # チームへの指示書
    │   │   ├── HISTORY.md
    │   │   ├── learnings.md
    │   │   └── STATUS.yaml
    │   │
    │   ├── OVERSEER/
    │   │   ├── knowledge/knowhow/
    │   │   │   └── strategy-brief.md      # 監査基準・構造規約・命名規則
    │   │   ├── HISTORY.md
    │   │   ├── learnings.md
    │   │   └── STATUS.yaml
    │   │
    │   ├── hr-tech/                       # 技術系エージェント
    │   │   ├── prompt-engineer-ARCHITECT/
    │   │   │   ├── knowledge/
    │   │   │   │   ├── knowhow/
    │   │   │   │   │   ├── prompt-engineering-principles.md
    │   │   │   │   │   ├── prompt-patterns.md
    │   │   │   │   │   └── skill-building-guide.md
    │   │   │   │   └── examples/
    │   │   │   │       ├── 口調プロファイリングくん.md
    │   │   │   │       ├── マインドマップ作るくん.md
    │   │   │   │       ├── バリューラダー構築くん.md
    │   │   │   │       └── ローンチスケジュール作るくん.md
    │   │   │   ├── HISTORY.md
    │   │   │   ├── learnings.md
    │   │   │   └── STATUS.yaml
    │   │   └── agent-designer-GENESIS/
    │   │       ├── knowledge/knowhow/
    │   │       │   ├── agent-design-principles.md
    │   │       │   └── personality-patterns.md
    │   │       ├── HISTORY.md
    │   │       ├── learnings.md
    │   │       └── STATUS.yaml
    │   │
    │   └── operations/                    # コンテンツ・事業系エージェント
    │       ├── note-creator-NOTE_CREATOR/
    │       │   ├── knowledge/
    │       │   │   ├── knowhow/
    │       │   │   │   ├── writing-style-profile.md
    │       │   │   │   ├── article-creation-process.md
    │       │   │   │   ├── lead-text-patterns.md
    │       │   │   │   ├── sentence-ending-patterns.md
    │       │   │   │   ├── improvement-checklist.md
    │       │   │   │   └── creator-achievements.md
    │       │   │   └── examples/          # 参考note記事
    │       │   ├── HISTORY.md
    │       │   ├── learnings.md
    │       │   └── STATUS.yaml
    │       ├── article-reviewer-ARTICLE_REVIEWER/
    │       │   ├── knowledge/
    │       │   │   ├── knowhow/
    │       │   │   │   ├── review-criteria.md
    │       │   │   │   ├── strategy-brief.md
    │       │   │   │   └── brand-check-criteria.md
    │       │   │   └── examples/
    │       │   │       ├── persona-01-problem-solver.md
    │       │   │       ├── persona-02-skill-investor.md
    │       │   │       ├── persona-03-community-seeker.md
    │       │   │       └── persona-04-roi-optimizer.md
    │       │   ├── HISTORY.md
    │       │   ├── learnings.md
    │       │   └── STATUS.yaml
    │       ├── article-stylist-ARTICLE_STYLIST/
    │       │   ├── knowledge/
    │       │   │   ├── knowhow/
    │       │   │   │   ├── styling-guidelines.md
    │       │   │   │   └── cta-and-navigation.md
    │       │   │   └── examples/
    │       │   │       ├── note-articles-catalog.md
    │       │   │       └── loop-salon-info.md
    │       │   ├── HISTORY.md
    │       │   ├── learnings.md
    │       │   └── STATUS.yaml
    │       ├── data-analyst-DATA_ANALYST/
    │       │   ├── knowledge/knowhow/
    │       │   │   ├── strategy-brief.md
    │       │   │   └── analysis-methods.md
    │       │   ├── HISTORY.md
    │       │   ├── learnings.md
    │       │   └── STATUS.yaml
    │       ├── x-post-creator-X_POST_CREATOR/
    │       │   ├── knowledge/
    │       │   │   ├── knowhow/
    │       │   │   │   ├── writing-style-profile.md
    │       │   │   │   ├── x-post-best-practices.md
    │       │   │   │   ├── x-operation-guide.md
    │       │   │   │   └── sentence-ending-patterns.md
    │       │   │   └── examples/
    │       │   │       ├── x-post-example-1.md
    │       │   │       └── x-post-example-2.md
    │       │   ├── HISTORY.md
    │       │   ├── learnings.md
    │       │   └── STATUS.yaml
    │       ├── gunshi-GUNSHI/
    │       │   ├── knowledge/knowhow/     # （setup-orgで戦略情報を記入）
    │       │   ├── HISTORY.md
    │       │   └── learnings.md
    │       ├── mail-creator-MAIL_CREATOR/
    │       │   ├── knowledge/
    │       │   │   ├── knowhow/
    │       │   │   │   └── writing-style-profile.md
    │       │   │   └── examples/
    │       │   │       ├── example-01.md
    │       │   │       └── example-02.md
    │       │   ├── HISTORY.md
    │       │   ├── learnings.md
    │       │   └── STATUS.yaml
    │       └── letter-creator-LETTER_CREATOR/
    │           ├── knowledge/
    │           │   ├── knowhow/
    │           │   │   └── writing-style-profile.md
    │           │   └── examples/          # 構成のみ参照・内容流用禁止
    │           │       ├── example-01.md
    │           │       └── example-02.md
    │           ├── HISTORY.md
    │           ├── learnings.md
    │           └── STATUS.yaml
    │
    └── workspace/                         # 成果物保存先（YYYY-MM-DD_NN/形式）
```

---

## 成果物の保存

タスク完了後、成果物は以下のパスに自動保存される：

```
ai-agent-organization/workspace/YYYY-MM-DD_NN/[type]-[topic].md
```

同一セッション内の複数成果物は同じフォルダ（`YYYY-MM-DD_NN/`）にまとめられる。

| エージェント | 保存プレフィックス |
|------------|-----------------|
| NOTE_CREATOR | `note-[topic].md` |
| ARTICLE_REVIEWER | `review-[topic].md` |
| ARTICLE_STYLIST | `styled-[topic].md` |
| DATA_ANALYST | `data-[topic].md` |
| X_POST_CREATOR | `x-post-[topic].md` |
| ARCHITECT | `prompt-[topic].md` |
| GENESIS | `agent-design-[topic].md` |
| GUNSHI | `strategy-[topic].md` |
| MAIL_CREATOR | `mail-[topic].md` |
| LETTER_CREATOR | `letter-[topic].md` |

---

## 動作環境

- **Claude Code CLI**（必須）
- **モデル**: Claude Opus 4.6（Agent Teams最適化）

---

## ライセンス

MIT

---

**Powered by Claude Code Agent Teams**
