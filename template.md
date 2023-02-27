# テンプレート

## アプリケーション立ち上げのテンプレート

### Steps

#### Action
testool-api 側の src/main/resources/application.yml 内にある active の値を local に変更
#### Result
active の値が local になっている

#### Action
ローカルで testool-api を実行する

#### Result
testool-api が実行され、「Started TestLinkApplication in xxxx seconds」が出力される

#### Action
ローカルで testool-clinet を実行する
#### Result
testool-clinet が実行され、http://localhost:9000 と表示される

#### Action
ブラウザで http://localhost:9000 にアクセスし、TesTool にログインする
#### Result
TesTool のトップページが表示される

## インポートのテンプレート

### Steps

#### Action
ホーム画面にある「テストプロジェクト管理」ボタンをクリックする
#### Result
「テストプロジェクト管理画面」が表示される

#### Action
テーブルを確認して、「Project Name」という名前のプロジェクトが存在していれば削除する
#### Result
テーブルに「Project Name」という名前のプロジェクトが存在しない

#### Action
「テストプロジェクトをインポートする」ボタンをクリックする
#### Result
「テストプロジェクト選択」ダイアログが表示される

#### Action
入力欄に https://github.com/url を入力し、エンターキーを押す
#### Result
「ブランチを選択してください。選択しないと正常にインポートされません。」というアラートが表示される

#### Action
表示されたアラート内の「OK」ボタンをクリックする
#### Result
入力欄の下部にブランチ選択メニューやプレフィックス入力欄が表示される

#### Action
ブランチ選択のプルダウンより、「main」を選択して、ユニークなプレフィックスを入力した後、「インポート」ボタンをクリックする
#### Result
「インポートに成功しました。」というアラートが表示される

#### Action
表示されたアラート内の「OK」ボタンをクリックする
#### Result
「選択中のプロジェクト」直下に表示されるものが「Project Name」になっており、  
入力したプレフィックスが全て大文字で表示されている。  
リポジトリURLと作成日時、更新日時の列に正しい値が入っている。

#### Action
ヘッダーを確認する
#### Result
選択中のプロジェクトが「Project Name」になっている

## 同期のテンプレート

### Steps

#### Action
ホーム画面にある「テストプロジェクト管理」ボタンをクリックする
#### Result
「テストプロジェクト管理画面」が表示される

#### Action
プロジェクト「Project Name」の右にある「同期」ボタンをクリック
#### Result
ブランチやタグを選択するダイアログが表示される

#### Action
ブランチ「ターゲットブランチ」を選択する
#### Result
「Pullに成功しました」というアラートが出る

#### Action
「テスト仕様管理」画面を確認する
#### Result
テストスイート「B」とテストケース「B01」「B02」「B03」が追加される

## コミット取り消しのテンプレート

### Steps

#### Action
gitコマンドと使って、ローカルの任意な場所に https://github.com/url をクローンする
#### Result
リポジトリのクローンが完了する

#### Action
ターミナルでリポジトリに移動する（またはGitツールでリポジトリを開く）
#### Result
リポジトリの情報を確認できる

#### Action
「ターゲットブランチ」ブランチに切り替える
#### Result
現在のブランチが「ターゲットブランチ」になっている

#### Action
コミットを確認する
#### Result
最新のコミットのメッセージが「Update test case id」となっている

#### Action
最新のコミットが「Update test case id」となっていれば、`git reset --hard HEAD^`で先頭のコミットを消す。  
先頭のコミットが「Update test case id」じゃなければ、何もしない。
#### Result
「Update test case id」のコミットが消える

#### Action
コミットを消したら、`git push origin ターゲットブランチ --force`でリモートブランチを更新する。  
コミットを取り消していなかったら、何もしない。
#### Result
https://github.com/url にアクセスして、「ターゲットブランチ」ブランチの最新コミットが「Update test case id」ではなくなる
