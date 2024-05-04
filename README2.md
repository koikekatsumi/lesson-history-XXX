# 課題8の作成時の操作説明

ここでは、操作方法での解説説明を、後で復習して見返せるように画像と文章を通じて載せています。

## 目次
- [Spring Initializrでの登録操作とプロジェクトの起動操作、プロジェクトの初期設定](#anchor1)
- [依存関係の追加に伴うライブラリーのダウンロードの操作](#anchor2)
- [.DS_Storeのコード表記追加](#anchor3)
- [プロジェクトにDockerfileなどを配置](#anchor4)
- [docker-compose.yml内の表記変更](#anchor5)
- [sql/001-create-table-and-load-data.sql内の表記変更](#anchor6)
- [DB周りの環境構築編　githubにbranchとpush実施](#anchor7)
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
メインメニュー＞＞FILE＞＞OPEN＞＞解凍したフォルダーごと選び、OPENします。

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
<img width="532" alt="スクリーンショット 2024-05-01 10 57 35" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/cc7c82af-da08-4d6a-a8be-a0f05ed08869">

<a id="anchor7"></a>
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
