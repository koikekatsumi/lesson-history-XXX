- [Read処理実装編　Spring BootからMySQLに接続するための設定とSpring BootからMySQLに接続確認、postmanにて通信接続確認](#anchor10)
- [Read処理実装編　　Controller作成とpostmanでの動作確認](#anchor11)
- [Read処理実装編　　MyBatisを使ったファイルを作成](#anchor12)
- [Read処理実装編　　Entity作成](#anchor13)
- [Read処理実装編　postmanのCurlにて実行確認](#anchor14)
- [Read処理実装編　クエリ文字列を指定して検索するAPIを実装](#anchor15)


<a id="anchor10"></a>
### Read処理実装編　Spring BootからMySQLに接続するための設定とSpring BootからMySQLに接続確認、postmanにて通信接続確認
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

<img width="1274" alt="スクリーンショット 2024-05-11 20 25 39" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/8f6a7883-1dc9-458f-99d9-ee87c094840f">

#### Spring BootからMySQLに接続確認
javaのNameserviceApplicationをrun（起動）をして、正常動作することを確認する。下記のようになっていること

<img width="1211" alt="スクリーンショット 2024-05-08 16 37 24" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/59b88600-5925-471b-9c2b-780e224c72cc">

#### postmanにて通信接続確認

![スクリーンショット 2024-05-08 17 33 31](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/c06b378a-cfcc-43bc-8c86-513cb1cb8f95)


<a id="anchor11"></a>
### Read処理実装編　Controller作成（例　List返すコードを作成）とpostmanでの動作確認
#### Controller作成　（例　List返すコードを作成）
<img width="1345" alt="スクリーンショット 2024-05-08 18 07 50" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/2c20523d-2c8c-444e-a83a-7d123741c8ec">

#### postmanでの動作確認
![スクリーンショット 2024-05-08 18 08 00](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/f99949af-286d-43ae-9512-c5e0dbbb5af6)

下記のJSON形式の記述例のように、上記↑になっていない

![スクリーンショット 2024-05-12 2 55 11](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/c3c2772a-dc2c-4137-9cf2-eb8f5cb017e7)

<a id="anchor12"></a>
### Read処理実装編　MyBatisを使ったファイルを作成
MyBatisではMapperと名付けますが、データベースとやり取りするためのモジュール
は Repository という呼び方をすることが多いです。

#### 下記の画像のように、Interfaceを作成 
※キャメルソースでファイル名を作成　　　例NameMapper
<img width="1281" alt="スクリーンショット 2024-05-08 20 17 53" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/dff73481-7cb4-4209-a5c9-d99bded1e7dd">

#### 次に下記のように、コードを記入
```
@Mapper // MyBatisのMapperである⽬印として@Mapperアノテーションを付与する
public interface NameMapper { // classではなくinterfaceで定義する
 @Select("SELECT * FROM names")
 List<Name> findAll();
}
```

<img width="1362" alt="スクリーンショット 2024-05-12 2 38 32" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/bc299c40-503d-4047-9729-9c7a835ae3a8">

<a id="anchor13"></a>

### Read処理実装編　Entity作成
上の画像③の手順↑のことから、、、

NameMapperのメソッドの返り値として定義しているNameはデータベースのレコードに対応しています。
言い換えると、データベースのテーブル構造を表したオブジェクトだと考えてください。
アプリケーション全体の設計によりますが、ここではEntity（エンティティ）とよびます。
Entity（エンティティ）は文脈により違うものを表すことがありますが、ここではデータベースのレコードに対応
するものとして定義します。
データベースの1行を1インスタンスと対応させるためのクラスが「 Entityクラス 」となります。

<img width="1353" alt="スクリーンショット 2024-05-12 10 19 59" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/3e7648f2-4b02-42e3-83d0-11992deb103d">

<img width="1370" alt="スクリーンショット 2024-05-12 2 41 02" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/226584cb-a9c3-4f49-b6e8-3c5b98af2cb6">

#### postmanにて、確認する

![スクリーンショット 2024-05-11 20 26 58](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/fda2882c-6637-41fd-9a47-d05927bfb87d)
![スクリーンショット 2024-05-12 12 48 17](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/2d9e78eb-a2d9-49fd-912c-c7568fc3cc8b)

データベースにデータを追加した時は、下記のようになっていることを確認とJSON形式の記述になっていることを確認する
![スクリーンショット 2024-05-12 17 24 01](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/106ea379-0cab-4b15-a122-75f60af430ab)

<a id="anchor14"></a>
### postmanのCurlにて実行確認
postmanにて、クリックする

![スクリーンショット 2024-05-12 17 38 46](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/8e58824e-818e-492d-b52a-2051ebd438de)

Curlをコピーする

![スクリーンショット 2024-05-12 17 38 59](https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/aa8d47cd-1596-4d5f-82d7-aafe0279c634)

#### ターミナルにて、Curlを貼り付けして確認
<img width="1221" alt="スクリーンショット 2024-05-12 17 41 40" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/1ef81795-aec2-47d6-82bc-a1ae4ef4b832">

さらに、Curｌ　のコピーペーストしたもの後に、＋　-i で詳細な動作も確認できる
<img width="1281" alt="スクリーンショット 2024-05-12 17 42 09" src="https://github.com/koikekatsumi/lesson-history-XXX/assets/163390515/9b09f575-db5d-4046-a0c0-e705f9d671b7">

<a id="anchor15"></a>
### Read処理実装編　クエリ文字列を指定して検索するAPIを実装
#### クエリ文字列を指定して検索するAPIを実装のためのコード作成
Mapperを作成します。
findByNameStartingWithというメソッドを作成します。
前方一致で検索するために、SQLのLIKE句を使います。

@Select("SELECT * FROM names")
 List<Name> findAll();
 
上記のコードだと、全てのデータをRead処理してしまう為、削除
下記のように、クエリ文字列を指定して検索するAPIを実装しますには、コードを加えてます。
```
@Select("SELECT * FROM names WHERE name LIKE CONCAT(#{prefix}, '%')")
List<Name> findByNameStartingWith(String prefix);
```







#### 基本的な使い方の解説例

SELECT [表示要素] FROM [テーブル名] WHERE [要素名] LIKE [曖昧検索の条件];

基本的に「WHERE句」の後ろに、条件の一つとして記述することになります。

少し実践的な内容で見てみましょうか。例えばユーザーの情報が入った、userテーブルがあったとして…名前に「山」がつくユーザーを探すなら、以下のようになるでしょう。

```
SELECT name FROM user WHERE name LIKE "%山%";
```

これだけで、名前に「山」がつくユーザーを一覧表示できます。

便利ですね!

しかし”%山%”部分の%となんでしょうか?

実はこれが今回重要となる、ワイルドカード文字です。

ワイルドカード文字とは
ワイルドカード文字とは、曖昧検索を指示する記号のことです。

このワイルドカード文字には二種類の文字があります。それが「% 」と「 _ 」で、それぞれ以下の効果をもちます。

% ・・・ 0文字以上の任意の文字列
_ ・・・ 任意の1文字
つまり先ほどの”%山%”部分は「どこかに山がついている文字列かどうか」を指定していたわけですね!

逆に「”_山%”」としていたら、任意の1文字が頭に必要になるので…たとえば山田はNG、竹山はOKといった指示となるわけです。

※ただし環境によっては、これ以外にもワイルドカード文字があるケースもあります。














#### postmanにて検索結果表示
メソッド：GET

パス
{param}の部分に、アルファベットの最初の文字を入力　例　a

```
/names?startsWith={param}
```
説明：startsWithで指定した文字列で始まる名前を取得する

レスポンスのステータスコードは200、レスポンスボディは下記のようなものとします。
```
[
 {
 "id": 1,
 "name": "john"
 }
]
````
検索結果がない場合は、空の配列を返却します。
[]



