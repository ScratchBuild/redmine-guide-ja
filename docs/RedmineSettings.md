アプリケーションの設定
======================

!!! note ""
    最終更新: 2018/01/08 [[原文](http://www.redmine.org/projects/redmine/wiki/RedmineSettings/71)]

「管理」→「設定」画面では、システム管理者はさまざまなグローバルレベルのアプリケーションの設定が行えます。

[TOC]

全般
----

### アプリケーションのタイトル

Redmineの画面の上部に表示されるタイトルです。

### ウェルカムメッセージ

アプリケーションの「ホーム」ページに表示されるテキストです。

### ページ毎の表示件数

チケットなどのオブジェクトを1ページに何件表示するのか、ユーザーが選択可能な固定値を定義します。

*デフォルト: 25, 50, 100*

### ページごとの検索結果表示件数

検索結果を1ページあたり何件表示するのか指定します。

*デフォルト: 20*

### プロジェクトの活動ページに表示される日数

[活動画面](RedmineProjectActivity)で1画面に何日分の情報を表示するのか指定します。

### ホスト名とパス

Redmineサーバにアクセスするためのホスト名とパスです。ユーザーに送信されるメール内のURLを生成するのに使われます。

Redmineはこの設定の適切そうな値を推測して入力欄の下に「例」として表示します。この値はほとんどの場合そのまま利用できます。

### プロトコル

メール通知でリンクを生成する際に使用されます。Redmineサーバにアクセスする際に実際に使用しているもの（http または https）を選択してください。 *デフォルト: http*

### テキスト書式

チケット、ニュース、文書などのテキストを修飾するために使用するテキスト書式を設定します。

**Textile** *(デフォルト)* または **Markdown** を選択できます。

### テキスト書式の変換結果をキャッシュ

TextileやMarkdownなどのテキスト書式からHTMLへの変換はブラウザにページを送信するたびに行われます(例: チケットの説明、Wikiページなど)。この処理は大きなテキストだと時間がかかることがあります。

この設定を有効にすると、変換済みのHTMLがキャッシュされるようになります。

キャッシュされたデータが保存されるストレージはキャッシュストアの設定によって変わります。デフォルトのキャッシュストアは[FileStore](https://railsguides.jp/caching_with_rails.html#activesupport-cache-filestore) で、データは `tmp/cache` ディレクトリ内のファイルとして保存されます。

[MemoryStore](https://railsguides.jp/caching_with_rails.html#activesupport-cache-memorystore)や[MemCacheStore](https://railsguides.jp/caching_with_rails.html#activesupport-cache-memcachestore)など別のキャッシュストアを使用するよう設定することもできます。例えば、MemoryStoreを使用するには以下のように `config/environments/production.rb` 内で `config.cache_store = :memory_store` のように設定します。

``` ruby
Rails.application.configure do
  # Settings specified here will take precedence over those in config/application.rb

  config.cache_store = :memory_store

  ...
```

キャッシュストアのより詳しい解説はRails Guidesの [キャッシュストア](https://railsguides.jp/caching_with_rails.html#%E3%82%AD%E3%83%A3%E3%83%83%E3%82%B7%E3%83%A5%E3%82%B9%E3%83%88%E3%82%A2) をご覧ください。

### Wiki履歴を圧縮する

wiki履歴の圧縮を有効にします（データベース領域を節約します） *デフォルト: なし*

### Atomフィードの最大出力件数

Atomフィードで出力するエントリ数の上限です *デフォルト: 15*

表示
----

### テーマ

カスタムテーマを選択することができます。
Redmineには、 [デフォルトのテーマ](http://www.redmine.org/projects/redmine/wiki/ThemeDefault) のほかに2個のテーマが同梱されています。

-   [alternate](http://www.redmine.org/projects/redmine/wiki/ThemeAlternate) : チケットの一覧を優先度に応じて色分け表示します
-   [classic](http://www.redmine.org/projects/redmine/wiki/ThemeClassic) : Redmine 0.5.1で使われていた旧形式のテーマです

alternateテーマの画面:

![](RedmineSettings/alternate_theme.png)

テーマは `public/themes/` に格納されています。テーマについての詳細は [テーマ](HowTo_create_a_custom_Redmine_theme.md) を参照してください。

### デフォルトの言語 {:#Default-language }

利用者のブラウザの言語をアプリケーションが識別できないときに利用されます。また、複数の利用者（異なる言語が混在）へメールを送信する際にも使われます。

*デフォルト: 英語*

### 匿名ユーザーにデフォルトの言語を強制

ログインしていないユーザーがアクセスしてきたとき、ブラウザの言語設定を無視して常に「[デフォルトの言語](#Default-language)」で設定された言語でユーザーインターフェイスを表示します。

### ログインユーザーにデフォルトの言語を強制

ユーザーの 個人設定 で設定されている言語を無視して常に「[デフォルトの言語](#Default-language)」で設定された言語でユーザーインターフェイスを表示します。

### 週の開始曜日

カレンダーを表示する際に何曜日を開始とするか選択します。デフォルトは「ユーザーの言語の設定に従う」で、例えばユーザーが「[個人設定](RedmineAccounts/#My-account)」で「日本語」を選択している場合は日曜日始まりになります。

### 日付の形式

日付をどのような形式で表示するか選択できます:

* **ユーザーの言語の設定に従う**: ユーザーが設定している言語に従った形式で表示されます。
* **他の形式**: 常に指定された形式で表示されます。

*デフォルト: ユーザーの言語の設定に従う*

### 時刻の形式

日付をどのような形式で表示するか選択できます:

* **ユーザーの言語の設定に従う**: ユーザーが設定している言語に従った形式で表示されます。
* **他の形式**: 常に指定された形式で表示されます。

*デフォルト: ユーザーの言語の設定に従う*

### 時間の形式

時間（予定工数、作業時間など）をどのような形式で表示するか選択できます:

* **0.75** _(デフォルト)_ : 小数で表示します。
* **0:45 h** : "HH:MM" 形式で表示します。

### ユーザー名の表示形式

氏名をどのような形式で表示するのか指定します。以下の組み合わせが選択できます。

-   名
-   名 姓
-   姓 名
-   姓, 名
-   ユーザー名

### Gravatarのアイコンを使用する

有効にすると、ユーザーの[Gravatar](https://ja.gravatar.com/) (globally recognized avatar) が様々な箇所で表示されるようになります。

### デフォルトのGravatarアイコン

Gravatarアイコンが未設定のユーザーに対して表示するアイコンを設定します。

### 添付ファイルのサムネイル画像を表示 {: #Display-attachment-thumbnails }

有効にすると、添付画像のサムネイルが添付ファイルの一覧の下に表示されます。

### サムネイル画像の大きさ

[添付ファイルのサムネイル画像を表示](#Display-attachment-thumbnails) がONのとき、サムネイル画像のサイズをピクセル単位で指定します。

*デフォルト: 100*

### 新規オブジェクト作成タブ

* **なし** : 「＋」メニューも「新しいチケット」タブも表示しません
* **"新しいチケット" タブを表示** : 「＋」メニューを表示せずに、Redmine 3.2までで使われていた「新しいチケット」タブを表示します。
* **"+" ドロップダウンを表示** _(デフォルト)_ : プロジェクトメニュー左端にチケットやWikiページなど各種オブジェクトを作成できる「＋」メニューをプロジェクトメニューの右端に表示します。


認証
----

### 認証が必要

このオプションが有効な場合、未認証のユーザーはどのページにもアクセスできません。Redmineにアクセスするためには必ずログインする必要があります。 *デフォルト: 無効*

### 自動ログイン

ユーザーが自動ログインを利用できるようになります。 *デフォルト: 無効*

### ユーザーによるアカウント登録 {: #Self-registration }

新規ユーザーが自分自身でユーザー登録を行う機能の有効／無効を切り替えます。

-   **無効**: 登録は行えません
-   **メールでアカウントを有効化**: 新規ユーザーにはアカウントを有効にするためのリンクが記載されたメールが届きます (ユーザーは正しいメールアドレスを入力する必要がある)。
-   **手動でアカウントを有効化** (デフォルト): 新規ユーザーのアカウントは作成されますが、システム管理者の承認が必要です。管理者には承認待ちのアカウントがある旨のメールが届きます。
-   **自動でアカウントを有効化**: 新規ユーザーは登録が完了すると直ちにログインすることができます。

ユーザーによるアカウント登録の詳細については [登録](RedmineRegister.md) をご覧ください。

### アカウント登録画面でカスタムフィールドを表示

(WIP)

### ユーザーによるアカウント削除を許可

有効にすると[個人設定](RedmineAccounts#My-account)画面のサイドバーに「自分のアカウントを削除」リンクが表示され、ユーザーは自分自身の操作で自分のアカウントを削除できるようになります。

*デフォルト: 有効*

### パスワードの最低必要文字数 {: #Minimum-password-length }

パスワードの最低文字数を設定できます。

*デフォルト: 8*

### パスワードの有効期限

有効にすると、パスワードの定期変更をユーザーに強制させることができます。定期変更の間隔は7日から365日の間の6段階で選択できます。

デフォルト: *無効*

### 追加メールアドレス数の上限

(WIP)

### パスワードの再発行 {: #Lost-password }

[パスワード再発行機能](RedmineAccounts#Password-lost)が有効になります。 *デフォルト: 有効*

### OpenIDによるログインと登録 {: #Allow-OpenID-login-and-registration }

OpenIDによるログインと登録の有効・無効を切り替えます。この機能は、必要なライブラリ（ruby-openid gem）がインストールされていない場合は常に無効になっています。

### セッション有効期間

* **有効期間の最大値**: セッションの有効期間が設定できます。
* **無操作タイムアウト**: 一定期間操作がなかったときにセッションをタイムアウトささせるよう設定できます。

!!! warning
    1. これらの設定を変更すると現在のセッションが失効する場合があります（自分自身のものを含む）。
    2. Redmineはセッション管理にRailsのcookiestoreを使用しています。「有効期間の最大値」を設定することを強く推奨します。もし設定しなかった場合、攻撃者にセッション情報のcookieを盗まれたときにそれを使い続けることが理論的には可能です。

API
---

### RESTによるWebサービスを有効にする

REST APIを有効にします。REST APIにより、外部のアプリケーションからRedmineのプロジェクトおよびチケットの作成・読み取り・更新・削除が行えるようになります。

REST API経由でRedmineと連係するアプリケーションを使用したり開発したりする場合はこの項目を有効にしてください。

### JSONPを有効にする

REST APIをJSONで利用しているとき、クロスドメインでの通信を実現するためのJSONPを有効にします。

JSONPでのレスポンスを得るには以下のようにパラメータ callback でコールバック関数名を指定してください。

```
GET /issues.json?callback=foo
=> foo({"issues":...})
```

プロジェクト
------------

### デフォルトで新しいプロジェクトは公開にする

新しくプロジェクトを作成したときの「公開」チェックボックスのデフォルトの状態を指定します。この設定が無効の場合でも、プロジェクト作成中または作成後にいつでも非公開に変更できます。

### 新規プロジェクトにおいてデフォルトで有効になるモジュール

新しくプロジェクトを作成したとき、ここで指定にしたモジュールのみがデフォルトで有効になります。

### 新規プロジェクトにおいてデフォルトで有効になるトラッカー

新しくプロジェクトを作成したとき、ここで指定にしたトラッカーのみがデフォルトで有効になります。

### プロジェクト識別子を連番で生成する

プロジェクトを作成するとき、連番によるデフォルトのプロジェクト識別子が生成されます。プロジェクト作成中のみ、手作業でほかの識別子に変更することもできます。

### システム管理者以外のユーザーが作成したプロジェクトに設定するロール

システム管理者でないユーザーがプロジェクトを作成したとき、そのユーザーをどのロールでプロジェクトのメンバーに加えるのか指定します（権限の設定でシステム管理者以外のユーザーがプロジェクトを作成できるように設定しているときのみ適用されます）。

チケットトラッキング
--------------------

### 異なるプロジェクトのチケット間で関係の設定を許可

有効にすると、異なるプロジェクトのチケット間で関係の設定ができるようになります。 *Default: 無効*

### チケットをコピーしたときに関連を設定

あるチケットをコピーして新しいチケットをコピーしたとき、それらのチケットに相互に「コピー元」「コピー先」という関連が設定します。

*デフォルト: 有効*

### 異なるプロジェクトのチケット間の親子関係を許可

プロジェクトをまたいでチケットの親子関係を設定する際の制約を指定します。それぞれの設定の意味はバージョンの共有の設定と同じです。詳しくは [バージョン](RedmineProjectSettings/#Versions) に記載されています。 *デフォルト: プロジェクトツリー単位*

* **無効** : 同一プロジェクトのチケットのみを子チケットにできます。
* **全プロジェクト** : 任意のプロジェクトのチケットを子チケットにできます。
* **プロジェクトツリー単位** : 最上位の親プロジェクトとすべての子孫プロジェクト間のチケットを子チケットにできます。
* **プロジェクト階層単位** : 直系の先祖・子孫プロジェクトのチケットを子チケットにできます。
* **サブプロジェクト単位** : サブプロジェクトのチケットを子チケットにできます。

### 重複しているチケットを連動して終了

(WIP)

### グループへのチケット割り当てを許可

(WIP)

### 現在の日付を新しいチケットの開始日とする

新しいチケットを作成する際、現在の日付をチケットの開始日のデフォルト値にします。

*デフォルト: 有効*

### サブプロジェクトのチケットをメインプロジェクトに表示する

有効にすると、チケット一覧、カレンダー、ガントチャートにサブプロジェクトのチケットも表示されるようになります。 *Default: 有効*

### 進捗率の算出方法 {: #Calculate-the-issue-done-ratio }

チケットの 進捗% の設定方法です。

-   チケットのフィールドを使用する (デフォルト): Users can manually set % done.
-   チケットのステータスを使用する: 各々のステータスにあらかじめ割り当てられた進捗率をチケットの進捗率とすることができます。

### 休業日

(WIP)

### エクスポートするチケット数の上限

チケットをCSV、PDF形式でエクスポートする際の最大数。 *デフォルト: 500*

### ガントチャートの最大表示件数

ガントチャートに表示するチケットやバージョンなどの最大件数

### チケットの一覧で表示する項目

この設定により、チケット一覧でどの項目を表示させるのか指定できます。この画面では「全プロジェクト向け」と設定されているカスタムフィールドのみが選択できます。

時間管理
--------

### 作業時間の必須入力フィールド

(WIP)

### 1日・1人あたりの作業時間の上限

(WIP)

### 作業時間に0時間の入力を許可

(WIP)

ファイル
--------

### 添付ファイルサイズの上限

アップロードできるファイルの最大サイズです(KB)。 *デフォルト: 5120 (5MB)*

### 許可する拡張子

(WIP)

### 禁止する拡張子

(WIP)

### 画面表示するテキストファイルサイズの上限

テキストファイルをインライン表示する際のファイルサイズの上限を指定します。

### 差分の表示行数の上限

diffの結果を画面表示する際の最大行数を指定します。

### 添付ファイルとリポジトリのエンコーディング

リポジトリに格納されたファイルにどのようなエンコーディングを適用するのか指定します。(コンマで区切ることにより複数の値を指定できます)。これらのエンコーディングはファイルの内容や差分をブラウザで表示する際に文字化けが発生しないよう、UTF-8に変換する際に使用されます。
複数の値を設定した場合、ファイルの内容に対して有効な最初のエンコーディングが使用されます。

フランス語の場合の設定例:

``` text
UTF-8, ISO 8859-15, CP1252
```

日本語の場合:

``` text
UTF-8, CP932, EUC-JP
```

メール通知
----------

### 送信元メールアドレス

ユーザーにメールを送信する際に使用されるFromアドレスです。

### ブラインドカーボンコピーで受信(bcc)

メール通知がBccで送信されるようになります。 *Default: 有効*

### プレインテキストのみ(HTMLなし)

メールがHTMLではなくプレインテキストのみで送信されるようになります。

### デフォルトのメール通知オプション

(WIP)

### メールのヘッダ

(WIP)

### メールのフッタ

Redmineから送信されるメールの末尾に付加するテキストを指定できます。

受信メール
----------

メールでチケットを作成するための設定手順については [メールによるチケット登録](RedmineReceivingEmails) を参照してください。

## メール本文から一致する行以降を切り取る

メールから署名を取り除くのに利用できます。

## 除外する添付ファイル名

(WIP)

## 受信メール用のwebサービスを有効にする

Redmineはチケット作成やコメントをメール経由で行えるよう設定できます。この機能を利用するためには、受信メール用のAPIを有効にする必要があります。

*デフォルト: オフ*

## APIキー

メールによるチケット登録の設定内で使用するためのAPIキーを指定します。

リポジトリ
----------

### 使用するバージョン管理システム

各プロジェクトで使用するバージョン管理システムを指定します。この設定は、利用できるのが特定のバージョン管理システムのみの場合に便利です（例: GitとSubversionのみがシステムで利用できる）

### コミットを自動取得する

このオプションが有効である場合、ユーザーが「リポジトリ」を参照した際に自動的に新しいリビジョンを取得します。

*デフォルト: 有効*

このオプションを無効にし、 `Repository#fetch_changesets` の呼び出しを自動化することにより、全リポジトリの全リビジョンをバックグラウンドで取得させることができます。

例:

``` sh
bin/rails runner "Repository.fetch_changesets" -e production
```

この処理をpost-commitまたはpost-receiveフックを利用してリポジトリから呼び出すこともできます。これにより新しいリビジョンがコミットごとに自動取得されるようになります。

gitによるpost-commit/post-receiveフックの設定例: <http://web.archive.org/web/20160523024839/http:///remine-git-post-receive.html>

### リポジトリ管理用のWeb Serviceを有効にする

このオプションは、SVNリポジトリの作成を自動化するスクリプトをインストールしている時のみ有効にします。 *デフォルト: 無効*

### ファイルのリビジョン表示数の上限

リポジトリ内の特定のパスの更新履歴を表示するときの、取得するリビジョン数の上限を指定します。

### コミットメッセージにテキスト書式を適用

(WIP)

### コミットメッセージ内でチケットの参照/修正 {: #Referencing-issues-in-commit-messages}

コミットメッセージがリポジトリから取得されると、参照する、もしくは修正されたチケットのIDが検索されます。
このオプションは、コミットメッセージから参照先あるいは修正されたチケットを自動的に検出するためのキーワードをを定義できます。また、修正されたチケットについてRedmineのステータスをどのように変更するのか設定できます。

デフォルトのキーワード:

-   参照するチケット: refs, references, IssueID
-   修正されたチケット: fixes, closes

修正されたチケットで、ステータスのデフォルト値は設定されていません。コミットと同時にチケットをクローズさせるためには、ステータスを設定してください。
もしキーワードを使わずにチケットを参照させたい場合、単にアスタリスク: \* を **参照用キーワード** に入力してください。メッセージ中に検出されたチケットIDはすべてチェンジセットに関連づけられます。

デフォルトのキーワードを使ったコミットの例:

``` text
This commit refs #1, #2 and fixes #3
```

このメッセージはチケット1および2を参照し、チケット3のステータスを自動的に変更します。
キーワードの後のチケットIDは、スペース、コンマもしくはアンパサンド(&)で区切ることができます。

The keywords are caseinsensitive and at least one blankspace or colon is needed between the keyword and the first hash to produce
a match. More examples that will produce the same result as the example above:

```
This commit refs:#1, #2 and fixes #3
This commit Refs  #1, #2 and fixes #3
This commit REFS: #1, #2 and fixes #3
```

### コミット時に作業時間を記録する

コミットメッセージによる作業時間の記録を許可します。プロジェクトで「作業時間」モジュールを有効にしている場合のみ効果があります。この設定を有効にすると、コミットメッセージ内に特別な記述を行うことであるチケットに対する作業時間を記録できます。

基本的な記法は `@時間` です。

以下に、チケット1234に対して費やした作業時間を記録する場合のコミットメッセージの例を示します:

```
Implement feature #1234 @2

Implement feature #1234 @2h

Implement feature #1234 @2hours

Implement feature #1234 @15m

Implement feature #1234 @15min

Implement feature #1234 @3h15

Implement feature #1234 @3h15m

Implement feature #1234 @3:15

Implement feature #1234 @3.25

Implement feature #1234 @3.25h

Implement feature #1234 @3,25

Implement feature #1234 @3,25h
```

### 作業時間の作業分類

コミットメッセージによる作業時間の記録（上記参照）を行うとき、この作業分類で作業時間を記録します。
