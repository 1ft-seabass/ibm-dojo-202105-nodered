# Node-REDを動かしてみよう

## Node-RED とは

![image](https://i.gyazo.com/07c703e8af39a7a5aaf5e660f663b576.png)

[Node\-RED日本ユーザ会](https://nodered.jp/)

Node-RED は Node.js で動く仕組みです。Node-RED はサーバーとフロントエンドの両方を作れる仕組みです。GUI（ビジュアルで見えるUI）によって、APIを取得する仕組みであったり、dashboard のように表示も作れます。

[フロー検索](https://flows.nodered.org/)で他の人の作った仕組みやノード再利用でき、プロトタイプするうえでも小さく素早く進める側面を備えています。

## IBM Cloud での Node-RED の準備

![image](https://i.gyazo.com/9fb96662265fab7324e6326edf507f07.png)

IBM Cloud でセットアップされた Node-RED ではじめていきます。

![image](https://i.gyazo.com/4952e648ed52462f44f4577c555528a5.png)

IBM Champion である [柿本さん](https://twitter.com/Kakimoty_Field)の書かれた[IBM Cloud で Node\-RED セットアップ \(2020年９月\) \- Qiita](https://qiita.com/Kakimoty_Field/items/ed30531445cafcb30a63) で Node-RED を使える環境をの作り方が参考になります。

## 動かしてみよう

[はじめてのフロー : Node\-RED日本ユーザ会](https://nodered.jp/docs/tutorials/first-flow)

こちら元に進めます。

ウォームアップしてみましょう。

![image](https://i.gyazo.com/b94d2d8a7a58febf76226db658c7d5dc.png)

このようなシンプル仕組みをつくります。

## ノードについて

![image](https://i.gyazo.com/4209abfa226dca0d1a4c1d3421768bbe.png)

まず ノード（Node）はNode-REDを構成する基本的な構成要素です。処理をする機能のかたまりです。

![image](https://i.gyazo.com/ac72b467278872701170501f629731ef.png)

ノードはフロー中の前方のノードからメッセージを受け取るか、外部イベントを受け取ることで動き出します。ノードはメッセージまたはイベントを処理し、 フロー中の次のノードにメッセージを送ります。右から左に処理されていきます。

![image](https://i.gyazo.com/b2e38a11e61da1ad55ff387493b71891.png)

メッセージはJSONデータで構成され、`msg` という一番上のオブジェクトにぶら下がっている `payload` というオブジェクトの中で、各ノードで処理された内容がバケツリレーのようにやり取りされていきます。

![image](https://i.gyazo.com/7a554e64647323ace99a930de52bfe67.png)

こんな感じです。

![image](https://i.gyazo.com/20007903edfd97e9aabddeedd5d6d8d5.png)

今回は inject というノードでボタンクリックをきっかけにメッセージを送り、 debug ノードという送られてきたメッセージをサイドバーのデバッグタブに表示するノードに送ります。

## 画面紹介

![image](https://i.gyazo.com/4e4f325615d23c2a56929fc767ce4327.png)

パレットはインストール済みで利用可能なすべてのノードが含まれます。ノードが置かれているエリアです。

![image](https://i.gyazo.com/47f080539655f431df2bc6afbf2eb845.png)

ワークスペースはパレットからノードを配置してフロー（データの流れ）を作るエリアです。

![image](https://i.gyazo.com/2b44b8d4535ed54a2ce46629fec8f96f.png)

サイドバーは、エディタ内に多くの便利なツールを提供するエリアです。

* ノードについてのさらなる情報
* ヘルプを確認するパネル
* デバッグメッセージを確認するパネル
* フローの設定ノードを確認するパネル

などがあります。

## inject ノードと debug ノードをつなげていく

![image](https://i.gyazo.com/69d9424ea7db4779794c1d39e1d0a44f.png)

inject ノードをワークスペースにドラックアンドドロップします。

![image](https://i.gyazo.com/4ab5cd15ee540f8b2181cafc29cf9377.png)

inject ノードの横にdebugノードをドラックアンドドロップします。

![image](https://i.gyazo.com/b8eb34fb3296018ddae614e01bd47a50.png)

inject ノードと debug ノードをつなぎます。つなぐものはワイヤーといいます。

![image](https://i.gyazo.com/58de57346d51b7620c32562f9c8690bf.png)

デプロイボタンをクリックすると今作ったものが反映されます。

![image](https://i.gyazo.com/6d69e6990487e06533edba753d67904e.png)

## 動かしてみる

![image](https://i.gyazo.com/486f98add3229d4cc880359bf1b3b643.png)

debugノードでデータがきてるか確認します。

![image](https://i.gyazo.com/6efbc1b0671669a3e5201e23e7298216.png)

debugノードのデータはサイドバーのデバッグタブをクリックすると見れます。

![image](https://i.gyazo.com/f99e3989db06dd84900022d8be76cb75.png)

injectノードの横のボタンを押すとdebugノードにデータが送られます。今回はinjectノードは日付（タイムスタンプ）を送っています。さきほどのデバッグタブでdebugノードが受け付けたデータを確認できます。

## injectノードで送るデータを変更

injectノードをダブルクリックしてデータを変更しましょう。

![image](https://i.gyazo.com/05dc870ae85c44d1be74d97b1a474b41.png)

ノードはダブルクリックすると細かな設定ができます。

![image](https://i.gyazo.com/6416484adf11e2410f0e5e1042da7f53.png)

ペイロードがデータの内容です。数値に変更しましょう。

![image](https://i.gyazo.com/290cce9c52a9736289eb3317a8f18f36.png)

50に設定して完了をクリックします。

![image](https://i.gyazo.com/6d69e6990487e06533edba753d67904e.png)

デプロイボタンをクリックすると今作ったものが反映されます。

![image](https://i.gyazo.com/5ce3b9ec73285db932270eabfab4ac63.png)

動かして、inject ノードから送られるデータが 50 の数値になっているか確認します。

## この章のまとめ

![image](https://i.gyazo.com/9d560ea43e326e7f26b905d1771e60a2.png)

inject ノードと debug ノードのフローづくりを通じて Node-RED のファーストステップをお伝えしました。

## 次の章へ

* [猫画像 API からデータを取得してみよう](02_api_request.md)