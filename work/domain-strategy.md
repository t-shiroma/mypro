# ドメイン・ブランド方針(案)

> 作成: 2026-11-20 / **決定(2026-11-20):自社製品は ryus-apps.jp にまとめる**(下の「追加検討」の案。条件1〜5を満たすこと)

## 前提(調査結果)
- **ryus-apps.jp**:RYU'S Apps は、ログイン共有のため **親ドメインの Cookie(`Domain=.ryus-apps.jp`、`ryus_session`)** を使っている(`ryus-apps/docs/design.md`、`packages/http/src/config.ts`)。
  → `*.ryus-apps.jp` に置いたアプリには、RYU'S Apps 利用者のログイン Cookie がすべて送られる。別製品(しかも一般利用者が登録する ashibi)を同居させると、そのアプリの脆弱性やログから RYU'S Apps のセッションが漏れる経路ができる。**「ryus-apps.jp に含めない方がよい」という助言は正しい。**
- **ryussystem.co.jp**:会社のドメイン。メール(Exchange Online)、コーポレートサイト、社内開発環境(`dev.*.ryussystem.co.jp`)、受託顧客向けの環境(`lifecorp.ryussystem.co.jp` など)が同居している。

## 方針(提案):ドメインは「信頼の境界」で分ける

| ドメイン | 置くもの | 置かないもの |
|---|---|---|
| **ryussystem.co.jp** | 会社の顔(コーポレートサイト・会社のメール)、社内システム(work-app)、社内開発環境、**受託顧客向けのシステム**(facility-booking、不動産、otc-kk など) | 一般の人が登録する自社製品 |
| **ryus-apps.jp** | **共通ログイン(accounts)を使う SaaS だけ**(勤怠、将来取り込む保育園向け勤怠 など) | 共通ログインを使わない製品(ashibi・宿泊税 SaaS・SecuBase) |
| **製品ごとの独自ドメイン**(新規取得) | 独立した自社製品:**ashibi**、宿泊税 SaaS、SecuBase | — |

### ashibi の具体案
- 製品ドメインを取得(例:`ashibi.jp` などの空き状況を確認)。年間数千円で、当日中に使える。
- 団体ごとにサブドメイン:`okinawa-sports.ashibi.jp`、`okiseikan.ashibi.jp`
  - ashibi は団体ごとに別のコンテナ・DB で動くので、Cookie は**ホスト単位(Domain 属性なし)**にして、団体間でも共有しない。
- 本契約後のオプション:団体のドメインで提供(例:`yoyaku.<団体のドメイン>` を CNAME で向ける)。公共施設の利用者は団体のドメインの方が安心するため、提案材料になる。
- 画面の表記は「ashibi ー ○○協会 施設予約」+ フッターに「提供:株式会社リュウズシステム」。会社の信用は表記で示し、ドメインでは分ける。

### 理由
1. **セキュリティ**:ある製品の脆弱性・設定ミスが、他製品や会社のメールに波及しない(Cookie・サブドメイン乗っ取り・証明書の範囲を分離)。
2. **メールの到達率**:製品ごとに送信ドメインを分ければ、ある製品の送信が迷惑メール扱いされても、会社のメールや他製品に影響しない。
3. **ブランド**:製品名がそのまま URL になり、覚えてもらいやすい。将来、製品を譲渡・分社しても切り離しやすい。

## メール配信(Resend)
- **会社のドメイン(ryussystem.co.jp)から直接送らない**。Exchange Online と SPF・評判が混ざるため。
- 送信用のサブドメインを使う:例 `no-reply@mail.ashibi.jp`(Resend でドメイン認証:SPF・DKIM を DNS に追加、DMARC も設定)。
- Resend の送信リージョンは東京(ap-northeast-1)を選べる。
- 利用者のメールアドレスを外部サービスに渡すことになるため、**プライバシーポリシーに「メール配信を外部に委託」と明記**する。
- 料金:無料プランは 1 日 100 通・月 3,000 通まで(お試しは足りる見込み。本契約後は利用量に応じて有料プランを検討)。※料金は変わることがあるので契約時に確認。

## サーバー(KAGOYA VPS)
- 宿泊税 SaaS と同じ構成(KAGOYA VPS + 前段に Cloudflare)にそろえると、手順・監視・バックアップを使い回せる。
- 製品ごとに VPS を分けるか同居させるかは、費用と影響範囲で判断。お試し段階は ashibi 用に 1 台(2団体を同居)で十分。

## 決めること
- [ ] 上の方針で進めるか
- [ ] ashibi の製品ドメイン名(候補を挙げて空き確認)
- [ ] 宿泊税 SaaS・SecuBase の本番ドメイン(まだ決まっていなければ同じ方針で)

---

## 追加検討:ashibi・宿泊税 SaaS・SecuBase を ryus-apps.jp にまとめる案(2026-11-20)

**結論:可能。ただし ryus-apps のログイン共有の作りを先に変えることが条件。**

### 今のままでは不可の理由
- ryus-apps のセッション Cookie が `Domain=.ryus-apps.jp`(親ドメイン)。`*.ryus-apps.jp` 配下のすべてのアプリにログイン Cookie が送られる。

### まとめるための条件
1. **ryus-apps のログイン共有を「親ドメイン Cookie」から「中央ログイン + アプリごとの Cookie」に変える**
   - accounts.ryus-apps.jp でログイン → 使い捨てのコードを付けて各アプリへ戻す → 各アプリが自分専用の Cookie(`__Host-` 接頭辞・Domain 属性なし)を発行(OIDC と同じ考え方)。
   - こうすれば、どのサブドメインにもほかのアプリのログイン Cookie は届かない。製品をまたいだ1つのアカウント(シングルサインオン)にも広げられる。
   - **ryus-apps はまだ公開前なので、変えるなら今が一番安い**。
2. **全製品で Cookie に `__Host-` 接頭辞を使う**(親ドメインへの Cookie の書き込み=「Cookie の投げ込み」によるセッション固定を防ぐ)。
3. **CSRF 対策を「SameSite」だけに頼らない**:同じ ryus-apps.jp 配下は「同じサイト」扱いになり、SameSite=Lax では防げない。Origin ヘッダを**完全一致**で確認する(または CSRF トークン)。
4. **DNS の管理を厳しくする**:使わなくなったサブドメインのレコードを残さない(サブドメイン乗っ取り対策)。ワイルドカード証明書は製品ごと(`*.ashibi.ryus-apps.jp`)に分け、親ドメイン全体のワイルドカードは使わない。
5. **メールは製品ごとの送信サブドメイン**:`mail.ashibi.ryus-apps.jp` など。DMARC の方針は ryus-apps.jp で共通になるため、送信設定を最初から正しくそろえる。

### URL の例
| 製品 | URL |
|---|---|
| シリーズのトップ | ryus-apps.jp |
| 共通ログイン | accounts.ryus-apps.jp |
| 勤怠 | kintai.ryus-apps.jp |
| ashibi | okinawa-sports.ashibi.ryus-apps.jp / okiseikan.ashibi.ryus-apps.jp(または ashibi.ryus-apps.jp/団体名) |
| 宿泊税 SaaS | stay.ryus-apps.jp(仮) |
| SecuBase | secubase.ryus-apps.jp |

### 比較
| | 製品ごとのドメイン | ryus-apps.jp にまとめる |
|---|---|---|
| ブランド | 製品名が前面 | **RYU'S Apps シリーズとして統一**、会社の製品群に見える |
| セキュリティ | 最初から分離(作り替え不要) | 条件1〜5を満たせば十分安全。ただし「同じサイト」扱いは残る |
| 作業 | ドメイン取得のみ | ryus-apps のログイン方式の変更(数日〜1週間程度の見込み)+ 各製品の Cookie・CSRF の点検 |
| 将来 | 製品の譲渡・分社がしやすい | 製品をまたいだ1アカウント・まとめ請求がしやすい |
| 費用 | 製品ごとにドメイン代 | 1つで済む |

### 注意(一般の利用者向けの製品)
- ashibi の利用者は「県民」、宿泊税 SaaS の利用者は「宿泊事業者」で、RYU'S Apps の利用者(企業の社員)とは層が違う。シリーズでまとめても、**画面・規約は製品ごとに分ける**のがよい。
- 公共施設の予約は、団体のドメインで提供してほしいと言われる可能性がある(本契約時のオプションとして残す)。

## 進捗(2026-11-24 確認)
| 製品 | 条件(Cookie・CSRF)の対応 | 状態 |
|---|---|---|
| ryus-apps(勤怠) | 中央ログイン+アプリ専用 `__Host-` Cookie | 済(ryus-apps#32、11/20) |
| ashibi | 同居のための Cookie・CSRF 対策 | 済(ashibi#10、11/20) |
| 宿泊税 SaaS(OSM) | CSRF は Origin 完全一致(ただし Origin が無い要求は通す)。Cookie `osm_rt`(path=/api/auth)は `__Host-` でない | 未対応(小さな修正) |
| SecuBase | CSRF は Origin 完全一致+Sec-Fetch-Site で厳格。Cookie `sb_session` は `__Host-` でない | 未対応(小さな修正) |
| blue-shield | 対象外(振興基金向けの受託システム。自社製品ではない) | — |
- 未決定:ashibi のサブドメインの形、宿泊税 SaaS の名前(stay.ryus-apps.jp は仮)、DNS の登録
