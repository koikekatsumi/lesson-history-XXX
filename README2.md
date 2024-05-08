# 講義8動画まとめの操作説明

ここでは、操作方法での解説説明を、後で復習して見返せるように画像と文章を通じて載せています。

## 目次<a id="anchor99"></a>
- [Spring Initializrでの登録操作とプロジェクトの起動操作](#anchor1)
- [.DS_Storeのコード表記追加](#anchor2)
- [プロジェクトの初期設定](#anchor3)
- [依存関係の追加に伴うライブラリーのダウンロードの操作](#anchor4)
- [DB周りの環境構築編　プロジェクトにDockerfileなどを配置](#anchor5)
- [DB周りの環境構築編　docker-compose.yml内の表記変更](#anchor6)
- [DB周りの環境構築編　sql/001-create-table-and-load-data.sql内の表記変更](#anchor7)
- [DB周りの環境構築編　Dockerによるコンテナ起動、データベースの中身の確認](#anchor8)
- [DB周りの環境構築編　githubにbranchとpush実施](#anchor9)
- [Spring BootからMySQLに接続するための設定とSpring BootからMySQLに接続確認、postmanにて通信接続確認](#anchor10)
- [Controller作成とpostmanでの動作確認](#anchor11)
- []
- []
- []
- []
- []
- []

<a id="anchor1"></a>
### Spring Initializrでの登録操作とプロジェクトの起動操作
#### Spring Initializrでの登録操作
まず依存関係の追加が必要です。 今回、InitializrからREST APIのプロジェクトを作る場合は
Spring Webに加えてMySQL DriverとMyBatis Frameworkが必要になります。

![スクリーンショット 2024-04-29 17 37 20](https://github.com/koikekatsumi/nameservice4-/assets/163390515/ddd90c27-57cf-406b-aa6f-e77eecac130c)

#### プロジェクトの起動操作
その後、ダウンロードファイルを解凍後、
メインメニュー＞＞FILE＞＞OPEN＞＞解凍したフォルダーを選び、OPENします。

<a id="anchor2"></a>
### .DS_Storeのコード表記追加
.DS_Storeファイルとは、Macでのみ使われる隠しファイルです。
Macに隠しファイル（不可視ファイル）があるのは重要なデータをユーザーが変更したりアクセスしてプログラムの大切なデータを誤って削除や変更してしまうことがないように、隠しファイルとしてユーザーが不用意に手を加えることなく、利用するために、MacBook内のデフォルトで隠しファイル/フォルダに設定されます。
尚、インテリジェイには、デフォルト設定されてない為、追加します。

.gitigone にて.DS_Storeのコードを追加
<img width="807" alt="スクリーンショット 2024-05-02 20 22 44" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/bbc47e5c-6e33-46a6-bfd5-0031d979a0b5">

<a id="anchor3"></a>
### プロジェクトの初期設定
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
```

ここで、ターミナル上で、README.mdにプロジェクトの詳細を記載します。

＜記載例＞

＄　# このプロジェクトについて

このプロジェクトでは Spring Boot と MySQL を用いた簡単 Read 処理をする API を実装します。

```
git status
git add .
git commit -m "プロジェクトの初期設定"
```
その後、github上で、リポジトリを作成
下記のように、リポジトリーのpushコードをコピーして、ターミナルにて、コマンド実行します。

![スクリーンショット 2024-05-06 15 45 58](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/88f95cee-8c94-448d-becb-6bbf4628fb37)

<a id="anchor4"></a>
### 依存関係の追加に伴うライブラリーのダウンロードの操作
インテリジェイ起動時、たとえばGradleを利用する場合、build.gradleには下記の画像の赤線のようにコードが追加されます。
依存関係を追加する際は記述を追加するだけでなく追加したライブラリをダウンロードする必要があります。

<img width="1180" alt="スクリーンショット 2024-05-04 9 00 51" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/dfd1070f-61fe-439d-98ec-58202c36ce12">

![2024-04-29_20 50 04のコピー](https://github.com/koikekatsumi/nameservice4-/assets/163390515/9b2f9760-cae0-4f7c-8f93-d222958937d7)


<a id="anchor5"></a>
### DB周りの環境構築編　プロジェクトにDockerfileなどを配置

<img width="527" alt="スクリーンショット 2024-05-01 10 57 27" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/90077847-be25-4252-9fed-7226b514fb80">

### [目次に戻る](#anchor99)
<a id="anchor6"></a>
### DB周りの環境構築編　docker-compose.yml内の表記変更
MYSQL_DATABASE は自分が扱いたいものに合わせたデータベース名にしましょう。
ここでは名前情報を扱うため name_database という名前にしています。

<img width="768" alt="スクリーンショット 2024-05-01 10 57 46" src="https://github.com/koikekatsumi/nameservice4-/assets/163390515/3974e308-3093-456d-8e9f-bddfaa652e5e">

<a id="anchor7"></a>
### DB周りの環境構築編　sql/001-create-table-and-load-data.sql内の表記変更
もし、TODOアプリを作りたいなどのアイデアがある場合は自分で考えたテーブルを作成してください。

<img width="532" alt="スクリーンショット 2024-05-01 10 57 35" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/3d03c3d0-f07b-4f8b-87e9-496581f11262">

<a id="anchor8"></a>
### DB周りの環境構築編　Dockerによるコンテナ起動とデータベースの中身の確認、Docker内のデータを確認
#### Dockerによるコンテナ起動とデータベースの中身の確認
ターミナルにて、下記の画像のコマンド入力
```
docker compose up -d
docker compose exec db mysql -uroot -p
```
passwordの入力　文字は、表示されない

<img width="1338" alt="スクリーンショット 2024-05-02 20 49 44" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/178f3bd4-00ec-4b57-95c2-f860f1e159f2">

<img width="1348" alt="スクリーンショット 2024-05-02 21 18 06" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/cb8dc368-cefd-4f75-b413-fe5b37b52040">

<img width="1004" alt="スクリーンショット 2024-05-02 21 53 48のコピー" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/82a926e0-2c9a-4a4d-a258-d938636c401b">

<img width="1127" alt="スクリーンショット 2024-05-02 21 22 16" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/c8790e8e-5c5a-47b4-9e32-c2df24f3e626">

データベースに追加でデータを入れたい時、下記の画像のように入れます。
例
```
insert into names (name) values ("lisa");
insert into names (name) values ("sofia");
```

<img width="827" alt="スクリーンショット 2024-05-06 17 27 15" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/849be546-f474-4d87-8a40-cd0bfee6099d">

#### Docker内のデータを確認

<img width="1253" alt="スクリーンショット 2024-05-06 14 34 46" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/96176068-d7b1-4066-a126-01f2a07cbb49">

<img width="1244" alt="スクリーンショット 2024-05-06 14 34 37" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/90160f08-1cba-45ec-aeda-7d8821ceac83">

<img width="1234" alt="スクリーンショット 2024-05-06 14 34 27" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/d1cfc38b-ff23-494d-bb71-5d65dfe06abc">

<img width="1412" alt="スクリーンショット 2024-05-01 11 13 46" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/7b6ae2c3-d3b9-459f-a1c2-b1648cd101a9">



<a id="anchor9"></a>
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

DB周りの環境構築の概要、動作確認を記載後、クリエイトプルリクエストを行う（正式には、ここで上長の判断を仰ぐ）

![スクリーンショット 2024-05-06 16 56 38](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/37a53b13-2111-4a40-95c9-47a5b5bd713e)

その後、レビューがOKの時（正式には、ここで上長の判断で承認されれば）、下記のように、マージ、プルリクエストを行う

![スクリーンショット 2024-05-06 16 33 38](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/018eb09f-362e-4bca-a8fe-ec99545e2c66)

![スクリーンショット 2024-05-06 16 34 14](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/eb5a382c-5225-47d8-a39b-05c44c7e7d17)

<img width="1008" alt="スクリーンショット 2024-05-06 16 34 50" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/b17f9eb1-5c3e-443d-ae12-0cdfe71bf366">

<a id="anchor10"></a>
### Spring BootからMySQLに接続するための設定とSpring BootからMySQLに接続確認、postmanにて通信接続確認
#### Spring BootからMySQLに接続するための設定
src/main/resources ディレクトリ配下にある application.properties へ次のような記述が必要で
す。

spring.datasource.url=jdbc:mysql://localhost:{port番号}/{database名}

spring.datasource.username={ユーザー名}

spring.datasource.password={パスワード}

ソースコード記入例
```
spring.datasource.url=jdbc:mysql://localhost:{3306}/{name_database}
spring.datasource.username={user}
spring.datasource.password={password}
```

<img width="1303" alt="スクリーンショット 2024-05-07 23 08 06" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/316cb7d9-7ff0-4924-bb53-80a51d25e22b">

ｄocker compose_ymlのファイルを参照する
<img width="1361" alt="スクリーンショット 2024-05-07 23 25 25" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/0d6f8f13-4035-42ed-9889-e89df582ef68">
application.propertiesにて、赤枠にて入力
<img width="1364" alt="スクリーンショット 2024-05-07 23 34 32" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/0c7bef88-1281-4cfc-a635-a1354013a542">

#### Spring BootからMySQLに接続確認
javaのNameserviceApplicationをrun（起動）をして、正常動作することを確認する。下記のようになっていること

<img width="1211" alt="スクリーンショット 2024-05-08 16 37 24" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/59b88600-5925-471b-9c2b-780e224c72cc">

#### postmanにて通信接続確認

![スクリーンショット 2024-05-08 17 33 31](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/c06b378a-cfcc-43bc-8c86-513cb1cb8f95)

<a id="anchor11"></a>
### Controller作成とpostmanでの動作確認
#### Controller作成
<img width="1345" alt="スクリーンショット 2024-05-08 18 07 50" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/2c20523d-2c8c-444e-a83a-7d123741c8ec">

#### postmanでの動作確認
![スクリーンショット 2024-05-08 18 08 00](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/f99949af-286d-43ae-9512-c5e0dbbb5af6)




### [目次に戻る](#anchor99)
