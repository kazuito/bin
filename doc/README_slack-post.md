# `slack-post`
シェル上からSlackにIncoming Webhooksを利用してテキストを投稿するスクリプト

## 前準備
### Incoming Webhooks URL の設定
本スクリプトはIncoming WebhooksのURLを使います．Custom IntegrationsにてURLを取得してください．URLは次のうちどれかに記述してください．

* スクリプト内の変数 `WEBHOOKURL`
* `$PWD/slack-post_webhook.txt`
* `$PWD/etc/slack-post_webhook.txt`
* `$PWD/misc/slack-post_webhook.txt`
* `$HOME/etc/slack-post_webhook.txt`
* `$HOME/misc/slack-post_webhook.txt`
* `$HOME/slack-post_webhook.txt`

なおこの設定は，変数 `WEBHOOKURL_DIR` および `WEBHOOKURL_BASE` にて変更できます．

### デフォルトチャンネル/ユーザ/アイコンの設定
本スクリプトの使用の前に，デフォルト設定を変更しておくことをおすすめします．

本スクリプトでは，コマンドラインオプションによって以下の設定が行なえます．

* 投稿するチャンネル(またはユーザ名)
* 投稿にあたってのユーザ名
* 投稿にあたってのアイコン(絵文字)

オプションを指定しない場合は，次のデフォルト設定が使われます．

* チャンネル: `@takaion`
* ユーザ名: `slack-post` (`basename` で取得します)
* アイコン: `:computer:` (💻)

しかしながら，デフォルトチャンネルが `@takaion` (作者のSlackでのユーザ名です)なので，ほとんどのワークスペースではデフォルトチャンネルは機能しません (takaionというユーザがいない限りは)．したがって，以下の変数を変更しておくことをおすすめします．

* デフォルトチャンネル: `DEFAULT_CHANNEL`
* ユーザ名: `DEFAULT_USER`
* アイコン: `DEFAULT_ICON`

## 使い方
スクリプトの基本的な使い方は `-h` または `--help` オプションを使うことで確認できます．

ここでは，その補足や使用例を紹介します．

### チャンネルの指定方法
`-c` または `--channel` オプションで指定できるチャンネル名には `#` または `@` (DMの場合) が必要です．

### 別のコマンドの出力をSlackに投げたいとき
`another-command | slack-post`

### テキストを引数として指定する
`slack-post "Test message"`
