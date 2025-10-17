---
title: やさしい図解で学ぶ　ER図　表記法一覧
tags: ER図 Rails DB
author: ramuneru
slide: false
---

# ER図とは?

- ER図もしくはERDとは
  - "Entity Relationship Diagram"のこと
- DB設計において
  - 「``テーブルとテーブルを線でつなぎ、中身の種類と関係性見やすくしたもの``」
と思っていただければ大丈夫です。 
- プログラミング学習者の方であればどこかで`鳥の足`みたいな先端で図表が結ばれたものを見たことがあるかもしれません。
- それが `ERD` もしくは `ER図`。
- 簡素なものですがたとえば下のような図です。

<img width="400" alt="ss1.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/e1b3c21e-da70-a7a1-db80-f0de05a37f8b.png">

## ER図のリレーション表記法一覧

<img width="400" alt="1.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/bda5fa65-da55-1552-0801-9fad3a3da152.png">

## 例1: 1対多

- ユーザーログイン機能とツイートが出来る簡単なアプリケーションがあるとします。
- データベースにはusersテーブルとtweetsテーブルの２つのテーブルが下図のようにあります。
- このテーブル間の関係性としては``1対多``となります。

<img width="400" alt="ss2.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/db0614bc-e008-59e3-fefd-906472128b7e.png">

### user →→ tweet

- 1人のuserに対してtweetの数は0か多
- (※単なる"多"ではなく、"0か多(0以上)"として考えるのは一つもtweetをしないことも可能だからです)

<img width="200" alt="2.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/6d7dcd3e-ca3c-fefe-2862-fa3a657baff6.png">

### tweet →→ user

- 1つのtweetは必ず誰かuser1人が作成したもの。つまり、あるユーザーに属しているので下記の表記になります。

<img width="200" alt="3" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/b90ff24e-e196-d5a5-91ff-69b0fc49fa37.png">

## 例2: 1対1

- 例1 に profiles テーブルと images テーブルをプラスしたもの

<img width="400" alt="ss3.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/475fb891-559f-3506-1b32-eeab992d8135.png">

### user →→ profile

### profile →→ user

- userから見ると user 1人に対してprofileは１つなので1 対 1 の関係となる。
- 逆も同じでprofile側から見ると必ずuser１人に所属していると考えるので

<img width="200" alt="4" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/35cf95b9-7815-43e1-a554-03e205d86434.png">

### tweet →→ image

- tweetから見たimageは 1tweetに対して最大1枚imageを持てるとし、imageのないtweetもあるとするとリレーションは"０か1"となる

<img width="200" alt="5" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/a10ff035-782a-699d-4f23-5106b133a333.png">

### image →→ tweet

- imageから見たtweet。
- 一方でimageは1tweetに必ず所属していると考えるので図のような関係性になります。

<img width="200" alt="6" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/98c937af-2641-9523-b371-e043b94d5315.png">

## 1対多: 制約がある場合

- tweetに対してimageの最低枚数に制約がある場合

<img width="400" alt="ss4.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/22c79ee1-e5d4-6afb-044b-7c3e738d9f94.png">

### 1か多とは 1対1 もしくは 1対複数のとき

- 例えばオークションやフリーマーケットサイトでは１つの商品に対して画像が最低１枚は必要なのでこちら。１対１でも１対多でもOKな場合です。

<img width="200" alt="7" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/2c882ac8-8720-abbb-da53-c70d1a85b045.png">

### 単なる多とは 必ず1対複数、つまり 2つ以上は必要

- 例えばメッセージアプリなどでグループをつくるとなったらグループ内にメンバーが２人以上は必要ですよね。そんなときはこの表記になります。

<img width="200" alt="8" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/40eda078-f5fe-582b-b2f6-bd9bdbaeadc6.png">


