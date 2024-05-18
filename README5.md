- [DB周りの環境構築編　プロジェクトにDockerfileなどを配置](#anchor5)
- [DB周りの環境構築編　docker-compose.yml内の表記変更](#anchor6)
- [DB周りの環境構築編　sql/001-create-table-and-load-data.sql内の表記変更](#anchor7)
- [DB周りの環境構築編　Dockerによるコンテナ起動、データベースの中身の確認](#anchor8)
- [DB周りの環境構築編　githubにbranchとpush実施](#anchor9)

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

データベースに追加でデータを入れたい時、下記の画像例のように入れます。

後で、時、先にデータベースにデータに追加する場合、ログインとデータベースに接続
```
docker compose exec db mysql -uroot -p
passworｄ　　//passworｄ名を入力
use name_database;
show tables;
```
データを追加する
```
insert into names (name) values ("lisa");
```
データベ入力後、データベースを確認する
```
select * from names;
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

