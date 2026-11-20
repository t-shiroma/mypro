# 依頼中の作業セッション

| 依頼日 | セッション | リポジトリ | 内容 | 状態 |
|---|---|---|---|---|
| 2026-11-20 | session_01GybB6zdQTAUHdARqTAYuJE | ryus-apps | 変形労働時間制に対応する勤怠集計の設計(tsumiki 統合)。設計のみ、PR は develop 向け | **完了**:[ryus-apps#31](https://github.com/ryussystem/ryus-apps/pull/31)。**#31 マージ済み(2026-11-20)。ただし develop に入ったのは最初の版 b84788d のみ**(GitHub の PR head 更新遅れ)。追加分は [ryus-apps#33](https://github.com/ryussystem/ryus-apps/pull/33) で提出(PR head ec2b0b4 を確認済み)。**ユーザーのマージ待ち** |
| 2026-11-20 | session_01GybB6yr2wQMja6AxT8rYKP | ashibi | お試し環境の準備(同居のための Cookie・CSRF 対策、KAGOYA 配置手順、Resend、自動バックアップ、規約の下書き、一括登録、利用案内) | 作業中(2026-11-20 時点) |
| 2026-11-20 | session_01GybB71qahbVKUroHchPPAM | ryus-apps | ログイン共有を親ドメイン Cookie から中央ログイン + アプリ専用 Cookie へ変更。PR は develop 向け | **完了**:[ryus-apps#32](https://github.com/ryussystem/ryus-apps/pull/32)。**マージ済み(2026-11-20)**。開発サーバーへ自動反映 → 開発サーバーの利用者は再ログインが必要 |

## 運用ルール
- 依頼したセッションの成果物は PR。**マージは必ずユーザーが行う**(各リポジトリの規約で Claude はマージしない)。
- このセッション(PM)が進捗を確認し、PR の要点・判断が必要な点・ユーザーの作業を要約して渡す。
- **PR が出たら PM セッションがユーザーに知らせる → ユーザーが確認してマージ**(2026-11-20 ユーザー指示)。完了の通知は来ないことがあるため、PM セッションが 30 分ごとに確認する(send_later で予約)。
