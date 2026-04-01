# スキル一覧リファレンス

ユーザーが「このスキルを使って」と言ったとき、または新規スキル追加時はここを更新する。
CLAUDE.md のルーティング表は更新不要。このファイルが全スキルの一次情報。

---

## スキル → 担当エージェント 対応表

| スキル名 | 担当エージェント | 用途 |
|---------|----------------|------|
| `note-creation` | NOTE_CREATOR | note記事の見出し構成・本文作成 |
| `content-ideation` | NOTE_CREATOR | ターゲットペルソナ設計・コンテンツ案生成（外部スキル） |
| `content-review` | ARTICLE_REVIEWER | 4ペルソナ視点でのコンテンツレビュー |
| `note-strategy-sparring` | GUNSHI | note×X収益化戦略の壁打ち |
| `note-content-planning` | GUNSHI | 戦略的noteコンテンツ企画立案 |
| `note-kpi-pdca` | GUNSHI | KPI分析・PDCAサイクル |
| `note-competitor-analysis` | GUNSHI | 競合分析・差別化戦略 |
| `daily-strategy` | BOSS + GUNSHI | 今日・今週やるべきことの提案 |
| `post-schedule-planning` | GUNSHI | 投稿ネタ設計・スケジューリング |
| `x-short-post` | X_POST_CREATOR | 140文字以内X短文投稿（3案） |
| `x-long-post` | X_POST_CREATOR | X長文投稿（ノウハウ発信） |
| `x-article` | X_POST_CREATOR | バズ狙いX記事（10万imp目標） |
| `x-note-promo` | X_POST_CREATOR | note記事のX宣伝投稿 |
| `x-rewrite-morning` | X_POST_CREATOR | 過去高インプ投稿のリライト（朝版） |
| `x-intent-trace` | X_POST_CREATOR | バズ投稿の設計意図解剖・テンプレ化 |
| `x-analysis` | DATA_ANALYST | 競合Xアカウント比較分析 |
| `x-analytics-analysis` | DATA_ANALYST | X analytics CSVデータ分析 |
| `regular-newsletter` | MAIL_CREATOR / DAILY_STARTER | 通常メルマガ作成 |
| `maruichi-merumaga` | MAIL_CREATOR | まるいちスタイルのメルマガ執筆・保存 |
| `sales-newsletter` | MAIL_CREATOR | 3日間・9通セールスメールシナリオ |
| `letter-creation` | LETTER_CREATOR | セールスレター（LP文章）作成 |
| `paid-note-planning` | PAID_NOTE_CREATOR | 有料note企画設計（HARM分析・価格設定） |
| `paid-note-sales-page` | PAID_NOTE_CREATOR | 有料note販売ページ作成 |
| `today-start` | DAILY_STARTER | 朝のコンテンツ一括生成（メルマガ+X投稿） |
| `today-finish` | TODAY_FINISHER | 日誌音声ログ分析・コンテンツネタ転記 |
| `output-check` | 全エージェント共通 | 6軸60点満点の品質チェック（提出前必須） |
| `rewriter` | 全エージェント共通 | 既存文章のリライト |
| `directory-audit` | OVERSEER | ディレクトリ全体スキャン・問題検出 |
| `health-report` | OVERSEER | プロジェクト健全性スコアリング |
| `cleanup-proposal` | OVERSEER | クリーンアップ具体アクション提案 |
| `structure-optimizer` | OVERSEER | プロジェクト構造の可視化・改善提案 |
| `skill-creator` | ARCHITECT | プロンプト→SKILL.md形式変換・新規スキル設計 |
| `prompt-creator-unified` | ARCHITECT | 新規プロンプト設計・作成 |
| `prompt-analyzer` | ARCHITECT | プロンプト問題点の詳細分析 |
| `prompt-improver` | ARCHITECT | 既存プロンプトの改善・最適化 |
| `setup-org` | BOSS | 組織初期セットアップ |
| `status-report` | BOSS | 組織全体ステータス一覧表示 |
| `task-request` | BOSS | タスク依頼→エージェント分配・実行 |
| `task-manager` | BOSS | 複合タスク分解・チーム連携調整 |
| `task-analyzer` | BOSS | タスク内容分析→最適エージェントルーティング |
| `cs-coaching` | CS_RESPONDER | CS返信（コーチング文脈）（外部スキル） |
| `cs-mentor` | CS_RESPONDER | CS返信（メンタリング文脈）（外部スキル） |
| `comparison-example-design` | ARCHITECT / GUNSHI | 比較例の設計・主張補強 |

---

## スキル追加ルール

新しいスキルを作成したら、このファイルの表に1行追加するだけでOK。
CLAUDE.md の編集は不要。

```
| `スキル名` | 担当エージェント | 用途の一言説明 |
```
