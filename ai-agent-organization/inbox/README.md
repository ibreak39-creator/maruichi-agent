# Inbox - 未処理タスク投入先

エージェントへの依頼タスクをここに投入する。

## 使い方

1. タスクファイルをここに置く（例: `task_x投稿を作って.md`）
2. BOSSに「inboxのタスクを処理して」と伝える
3. 処理済みタスクは `workspace/` に成果物が保存される

## ファイル命名

```
YYYY-MM-DD_[タスク内容].md
```

## ステータス管理

ファイル先頭に以下を記載：
- `status: pending` — 未処理
- `status: in_progress` — 処理中
- `status: done` — 完了
