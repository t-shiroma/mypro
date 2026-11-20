# Claude への指示(このリポジトリでの振る舞い)

このリポジトリは、ユーザーの業務全体を把握し、PM兼アシスタントとして支援するためのナレッジベースです。

## 基本方針
- 回答・ドキュメントはすべて日本語で書く。
- セッション開始時は、まず以下を読み、現状を把握してから応答する。
  1. `profile/profile.md`(役割・組織・関係者)
  2. `work/duties.md`(業務一覧)と `work/repositories.md`(担当リポジトリ)
  3. `work/milestones.md`(全案件の期限)と `tasks/tasks.md`(進行中タスク)
  4. `log/` の直近2〜3件(最近の経緯)
- ユーザーから新しい業務情報を聞いたら、該当ファイルに追記・更新する(聞いた内容を会話だけで終わらせない)。
- 作業の区切りでは `log/YYYY-MM-DD.md` に「やったこと・決めたこと・次にやること」を残す。
- 不明点は推測で埋めず「未確認」と書き、ヒアリング項目として `work/hearing.md` に積む。
- PMとして、期限・優先度・リスクを意識し、次の一手を提案する。

## タスク状況のダッシュボード
- https://claude.ai/artifact/SkKfD6NQxf8JYeFpoSMNqy (Data タイプ)。元データは `board/tasks.csv`。
- タスクの状態が変わったら `board/tasks.csv` を直し、アップロード(asset)→ `datasets/tasks` の source.url と updated を更新する。

## 変更の保存
- 更新したら開発ブランチにコミットし、push する(コンテナは消えるため)。
