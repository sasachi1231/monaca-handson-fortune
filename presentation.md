title: Monaca × ニフクラ mobile backendでクラウド連携アプリ開発ハンズオン！
title_row1: Monaca × ニフクラ mobile backendで
title_row2: クラウド連携アプリ開発ハンズオン！
company_ja: 富士通クラウドテクノロジーズ株式会社
company_en: FUJITSU CLOUD TECHNOLOGIES LIMITED
thisyear: 2019
class: animation-fade
layout: true

<!-- This slide will serve as the base layout for all your slides -->
.bottom-bar[
  .small[
  .center[Copyright 2017 - {{thisyear}} FUJITSU CLOUD TECHNOLOGIES LIMITED]
  ]
]

---

class: impact

# {{title_row1}}
# {{title_row2}}

.footer[
    {{company_ja}}
]

---

class: impact

## はじめに

---

# 前段

## 本日の資料

本日の資料(この資料)はここにあります。  
※ソースコードをコピペする際などに利用します  
.big[**bit.ly/monaca_x_ncmb**]

## 事前準備

以下のものを事前に用意しておいてください。
- Google Chrome最新版
- Monacaアカウント
- ニフクラ mobile backendアカウント

---

# 自己紹介

.col-6[
  ## 佐々木 大樹
  ### 所属
  富士通クラウドテクノロジーズ株式会社
  ### 業務
  ニフクラ mobile backend 企画／営業
]

.col-6[
  <img src="img/sasaki.jpg" style="width:400px">
]

---

# ニフクラ mobile backendとは

<img src="img/about_mbaas.jpg" style="width:100%">

---

# ニフクラ mobile backend × Monaca

.center[<img src="img/monaca_x_mbaas.jpg" style=width:90%>]

---

# Monacaユーザーに最も支持されるクラウド

ニフクラ mobile backendは、プッシュ通知、mBaaSの2部門で、Monacaユーザーに最も利用されるクラウドです！

.center[
  .col-6[
    <img src="img/push-survey.png" style="width:90%">
  ]
  .col-6[
    <img src="img/mbaas-survey.png" style="width:90%">
  ]
]

.col-6[※出典：https://press.monaca.io/ryo/2001]

---

class: impact

## 準備

---

# ニフクラ mobile backendの準備

## アプリの作成

mobile backendにログインして、以下の手順でアプリを作成します。

.center[
  .col-6[
    <img src="img/ncmb-create-app1.png" style="width:55%">
  ]
  .col-6[
    <img src="img/ncmb-create-app2.png" style="width:100%">
  ]
]

---

# ニフクラ mobile backendの準備

この画面が表示されます。  
これでmobile backendの準備は完了です。タブはこのままにしておき、新しいタブを開いて次のステップへ進みます。

.center[<img src="img/ncmb-create-app3.png" style="width:40%">]

---

# Monacaの準備

## プロジェクトの作成

Monacaダッシュボード(要ログイン)から、以下の手順でプロジェクトを作成します。

.col-4[
  <img src="img/monaca_create_project1.png" style="width:100%">
]
.col-4[
  <img src="img/monaca_create_project2.png" style="width:100%">
]
.col-4[
  <img src="img/monaca_create_project3.png" style="width:100%">
]

作成されたら、作成したプロジェクトをクリックして「クラウドIDEで開く」を押してください。

---

#  Monacaの準備

この画面が表示されます。  
これで準備は完了です。開いたタブはそのままにしておきましょう。

.center[<img src="img/monaca-ide.png" style="width:70%">]

---

class: impact

## Monaca × ニフクラ mobile backendの連携

---

# Monacaとmobile backendの連携

## SDKの導入①

以下手順でmobile backendのJavaScript SDKの導入します。

.center[
  .col-6[
    <img src="img/import-js-sdk1.png" style="width:70%">
  ]
  .col-6[
    <img src="img/import-js-sdk2.png" style="width:70%">
  ]
]

---

# Monacaとmobile backendの連携

## SDKの導入②

以下手順でmobile backendのJavaScript SDKの導入します。

.center[
  .col-6[
    <img src="img/import-js-sdk3.png" style="width:70%">
  ]
  .col-6[
    <img src="img/import-js-sdk4.png" style="width:70%">
  ]
]

---

# Monacaとmobile backendの連携

## APIキーの入力①

Monaca上のindex.htmlの10, 11行目にある以下部分を書き換えてmobile backend上のアプリへつなぎ込みを行います。


```html
<script>
</script>
```

以下のように書き換えましょう。

```html
<script>
  var APPLICATION_KEY = 'アプリケーションキー'; // アプリケーションキーの設定
  var CLIENT_KEY = 'クライアントキー'; // クライアントキーの設定
  var ncmb = new NCMB(APPLICATION_KEY, CLIENT_KEY); // SDKの初期化処理
</script>
```

上記コードの'アプリケーションキー'、'クライアントキー'の部分に、mobile backend上の一つ一つのアプリ固有のキーを入力することにより、mobile backend上のどのアプリと連携するのかが決まります。

---

# Monacaとmobile backendの連携

.col-6[

  ## APIキーの入力②

  mobile backendのタブに戻り、画面に表示されている「アプリケーションキー」「クライアントキー」をそれぞれコード上の'アプリケーションキー'、'クライアントキー'の部分に置き換える形で入力します。

  コピペミスを防ぐため、キーの右側にある「コピーボタン」を押すと確実です。

  また、すでに「OK」を押して画面を閉じてしまった場合は、画面右上の「アプリ設定」をクリックすると、中段にある「APIキー」の欄で同様の情報をご確認いただけます。

  なお、APIキーは重要な情報なので、第三者に知られることのないようにしましょう。

]

.center[<img src="img/ncmb-create-app3.png" style="width:40%">]

---

class: impact

## mobile backendへのデータの登録

---

# mobile backendへのデータの登録

## データストアを使う①

mobile bacnekdに画面で、データストア(データベース)機能を使いましょう。  
左側メニューの「データストア」をクリックし、新しいクラス(データストアの単位)を作成します。

.center[
  .col-6[
    <img src="img/create-datastore-class1.png" style="width:70%">
  ]
  .col-6[
    <img src="img/create-datastore-class2.png" style="width:100%">
  ]
]

---

# mobile backendへのデータの登録

## データストアを使う②

クラスが作成され、この画面が表示されます。

.center[
  <img src="img/create-datastore-class3.png" style="width:50%">
]

---

# mobile backendへのデータの登録

## データストアを使う③

「＋新しいフィールド」をクリックし、おみくじの結果を格納するフィールド(列)「result」を追加します。

.center[
  .col-6[
    <img src="img/create-datastore-field1.png" style="width:60%">
  ]
  .col-6[
    <img src="img/create-datastore-field2.png" style="width:80%">
  ]
]

---

# mobile backendへのデータの登録

## データストアを使う④

次に、「＋新しいレコード」をクリックし、実際にデータ(おみくじの結果)を作っていきます。  
大吉が作成できたら、同じように「中吉」「小吉」「吉」「凶」「大凶」などなど入れてみましょう。

.center[
  .col-6[
    <img src="img/create-datastore-record1.png" style="width:70%">
  ]
  .col-6[
    <img src="img/create-datastore-record2.png" style="width:100%">
    <img src="img/create-datastore-record3.png" style="width:100%">
  ]
]

---

class: impact

## mobile backendからデータを取得する

---

# mobile backendからデータを取得する

## 画面を作る

Monacaのタブを開き、index.htmlの16行目から始まるbodyタグの中身を以下記述に置き換えます。

```html
<body>
	<br />
    This is a template for Monaca app.
</body>
```

こちらを以下に置き換えます。

```html
<body>
  <button onclick="omikuji();">おみくじを引く</button>
  結果：<span id="result"></span>
</body>
```

ボタンが押されると、Omikuji()という関数が呼ばれます。  
まだ処理を実装していないので、現時点ではクリックしても何も起こりません。

---

# mobile backendからデータを取得する

## 取得処理の実装

では、先程配置したボタンが押されたときにおみくじを引く処理を実装していきます。  
10行目からのscriptタグの中に、以下を追記します。

```js
function omikuji() { // おみくじボタン押下時の処理
  var Omikuji = ncmb.DataStore("Omikuji"); // 取得元クラスの生成
  // 取得処理
  Omikuji.fetchAll()
          .then(function(objects){
            var random = Math.floor(Math.random()*objects.length); // データ数内で乱数を作成
            var object = objects[random]; // 乱数番目のデータ
            var result= object.get("result"); // 「result」フィールドの値を取得
            document.getElementById("result").innerText = result; // 画面に結果を表示
        })
        .catch(function(error){
            /* 取得失敗時の処理 */
            alert("Error: " + error.code);
        });
}
```

---

# mobile backendからデータを取得する

scriptタグ全体としては、以下のようになります。

```html
<script>
  var APPLICATION_KEY = 'アプリケーションキー'; // アプリケーションキーの設定
  var CLIENT_KEY = 'クライアントキー'; // クライアントキーの設定
  var ncmb = new NCMB(APPLICATION_KEY, CLIENT_KEY); // SDKの初期化処理

  function omikuji() { // おみくじボタン押下時の処理
    var Omikuji = ncmb.DataStore("Omikuji"); // 取得元クラスの生成
    // 取得処理
    Omikuji.fetchAll()
      .then(function(objects){
        var random = Math.floor(Math.random()*objects.length); // データ数内で乱数を作成
        var object = objects[random]; // 乱数番目のデータ
        var result= object.get("result"); // 「result」フィールドの値を取得
        document.getElementById("result").innerText = result; // 画面に結果を表示
      })
      .catch(function(error){
        /* 取得失敗時の処理 */
        alert("Error: " + error.code);
      });
  }
</script>
```

---

# まとめ

--

## hoge

--

## fuga

--

.center[
  .big[ありがとうございました！]
]

---

class: impact

## 以下、一時保存用

---

# mobile backendからデータを取得する

## 取得処理の実装①

では、先程配置したボタンが押されたときにおみくじを引く処理を実装していきます。  
10行目からのscriptタグの中に、以下を追記します。

```js
function omikuji() { // おみくじボタン押下時の処理
  var result = "テストです"; // 現時点では、仮で「テストです」と入れる
  document.getElementById("result").innerText = result; // 画面に結果を表示
}
```

---

# mobile backendからデータを取得する

## 取得処理の実装②

scriptタグ全体としては、以下のようになります。

```html
    <script>
      var APPLICATION_KEY = 'アプリケーションキー'; // アプリケーションキーの設定
      var CLIENT_KEY = 'クライアントキー'; // クライアントキーの設定
      var ncmb = new NCMB(APPLICATION_KEY, CLIENT_KEY); // SDKの初期化処理

      function omikuji() { // おみくじボタン押下時の処理
        var result = "テストです"; // 現時点では、仮で「テストです」と入れる
        document.getElementById("result").innerText = result; // 画面に結果を表示
      }
    </script>
```

---

# mobile backendからデータを取得する

## 現時点の状況

いま時点でどのように動作するのか、Monacaのプレビュー画面にて試してみましょう。

.center[
  .col-6[
    <img src="img/test-preview1.png" style="width:60%">
  ]
  .col-6[
    <img src="img/test-preview2.png" style="width:60%">
  ]
]