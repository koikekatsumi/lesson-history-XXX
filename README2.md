# 課題8の作成時の操作説明

ここでは、操作方法での解説説明を、後で復習して見返せるように画像と文章を通じて載せています。

## 目次<a id="anchor99"></a>
- [Spring Initializrでの登録操作とプロジェクトの起動操作、プロジェクトの初期設定](#anchor1)
- [依存関係の追加に伴うライブラリーのダウンロードの操作](#anchor2)
- [.DS_Storeのコード表記追加](#anchor3)
- [DB周りの環境構築編　プロジェクトにDockerfileなどを配置](#anchor4)
- [DB周りの環境構築編　docker-compose.yml内の表記変更](#anchor5)
- [DB周りの環境構築編　sql/001-create-table-and-load-data.sql内の表記変更](#anchor6)
- [DB周りの環境構築編　Dockerによるコンテナ起動、データベースの中身の確認](#anchor7)
- [DB周りの環境構築編　githubにbranchとpush実施](#anchor8)
- []
- []
- []
- []
- []
- []
- []
- []

<a id="anchor1"></a>
### Spring Initializrでの登録操作とプロジェクトの起動操作、プロジェクトの初期設定
#### Spring Initializrでの登録操作
まず依存関係の追加が必要です。 今回、InitializrからREST APIのプロジェクトを作る場合は
Spring Webに加えてMySQL DriverとMyBatis Frameworkが必要になります。

![スクリーンショット 2024-04-29 17 37 20](https://github.com/koikekatsumi/nameservice4-/assets/163390515/ddd90c27-57cf-406b-aa6f-e77eecac130c)

#### プロジェクトの起動操作
その後、ダウンロードファイルを解凍後、
メインメニュー＞＞FILE＞＞OPEN＞＞解凍したフォルダーを選び、OPENします。

#### プロジェクトの初期設定
ターミナルにて、下記のコマンドを入力
コマンドの各々の命令の意味あい

- リポジトリーの初期化
- ファイルの作成
- README.mdの表示の確認
- nameservice4（プロジェクト内にて）　表示を確認
- ステージングされたファイルの一覧を表示　ステージングしていないと、赤く表示されます。
- ステージング
- コミット

```
git init
echo "# nameservice4" >>README.md
ls
cat README.md
git status
git add .
git commit -m "プロジェクトの初期設定"
```
その後、github上で、リポジトリを作成
リポジトリーのpushコードをコピーして、ターミナルにて、コマンド実行します。
※ここでは、一番最初の初期化設定のため、branchをしません。

<a id="anchor2"></a>
### 依存関係の追加に伴うライブラリーのダウンロードの操作
インテリジェイ起動時、たとえばGradleを利用する場合、build.gradleには下記の画像の赤線のようにコードが追加されます。
依存関係を追加する際は記述を追加するだけでなく追加したライブラリをダウンロードする必要があります。

<img width="1180" alt="スクリーンショット 2024-05-04 9 00 51" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/dfd1070f-61fe-439d-98ec-58202c36ce12">

![2024-04-29_20 50 04のコピー](https://github.com/koikekatsumi/nameservice4-/assets/163390515/9b2f9760-cae0-4f7c-8f93-d222958937d7)

<a id="anchor3"></a>
### .DS_Storeのコード表記追加
.DS_Storeファイルとは、Macでのみ使われる隠しファイルです。
Macに隠しファイル（不可視ファイル）があるのは重要なデータをユーザーが変更したりアクセスしてプログラムの大切なデータを誤って削除や変更してしまうことがないように、隠しファイルとしてユーザーが不用意に手を加えることなく、利用するために、デフォルトで隠しファイル/フォルダに設定されます。
インテリジェイには、デフォルトではないので追加します。

.gitigone にて.DS_Storeのコードを追加
<img width="807" alt="スクリーンショット 2024-05-02 20 22 44" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/bbc47e5c-6e33-46a6-bfd5-0031d979a0b5">

<a id="anchor4"></a>
### DB周りの環境構築編　プロジェクトにDockerfileなどを配置

<img width="527" alt="スクリーンショット 2024-05-01 10 57 27" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/90077847-be25-4252-9fed-7226b514fb80">

<a id="anchor5"></a>
### DB周りの環境構築編　docker-compose.yml内の表記変更
MYSQL_DATABASE は自分が扱いたいものに合わせたデータベース名にしましょう。
ここでは名前情報を扱うため name_database という名前にしています。

<img width="768" alt="スクリーンショット 2024-05-01 10 57 46" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/3974e308-3093-456d-8e9f-bddfaa652e5e">

<a id="anchor6"></a>
### DB周りの環境構築編　sql/001-create-table-and-load-data.sql内の表記変更
もし、TODOアプリを作りたいなどのアイデアがある場合は自分で考えたテーブルを作成してください。

<img width="532" alt="スクリーンショット 2024-05-01 10 57 35" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/3d03c3d0-f07b-4f8b-87e9-496581f11262">

<a id="anchor7"></a>
### DB周りの環境構築編　Dockerによるコンテナ起動とデータベースの中身の確認、Docker内のデータを確認
#### Dockerによるコンテナ起動とデータベースの中身の確認
ターミナルにて、下記の画像のコマンド入力

<img width="1338" alt="スクリーンショット 2024-05-02 20 49 44" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/178f3bd4-00ec-4b57-95c2-f860f1e159f2">

<img width="1348" alt="スクリーンショット 2024-05-02 21 18 06" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/cb8dc368-cefd-4f75-b413-fe5b37b52040">

<img width="1004" alt="スクリーンショット 2024-05-02 21 53 48のコピー" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/82a926e0-2c9a-4a4d-a258-d938636c401b">

<img width="1127" alt="スクリーンショット 2024-05-02 21 22 16" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/c8790e8e-5c5a-47b4-9e32-c2df24f3e626">

#### Docker内のデータを確認




<img width="1412" alt="スクリーンショット 2024-05-01 11 13 46" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/7b6ae2c3-d3b9-459f-a1c2-b1648cd101a9">

<a id="anchor8"></a>
### DB周りの環境構築編　githubにbranchとpush実施
ターミナルにて、下記のコマンドを入力
コマンドの各々の命令の意味あい

- ブランチの作成
- ステージング
- コミット
- push
  
```
git checkout -b setup-db-container
git add .
git commit -m "DB周りの環境構築"
git push origin head -u
```
<img width="1129" alt="スクリーンショット 2024-05-02 21 30 57" src="https://github.com/koikekatsumi/nameservice4/assets/163390515/4bb7d6fc-d58c-44be-a650-0dadba149d03">




[目次に戻る](#anchor99)
