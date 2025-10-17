---
title: やさしい図解で学ぶ　ER図　表記法一覧
tags: ER図 Rails DB
author: ramuneru
slide: false
---
# ER図とは?
ER図もしくはERDとは 
 "Entity Relationship Diagram"のこと

DB設計において
「**テーブルとテーブルを線でつなぎ、中身の種類と関係性見やすくしたもの**」
と思っていただければ大丈夫です。 

プログラミング学習者の方であればどこかで<font color="blue";>”鳥の足”</font>みたいな先端で図表が結ばれたものを見たことがあるかもしれません。

それが<font color="red";>ERD<font color="black";>もしくは<font color="red";>ER図。

簡素なものですがたとえば下のような図です。

<img width="545" alt="スクリーンショット 2019-12-16 11.24.29.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/e1b3c21e-da70-a7a1-db80-f0de05a37f8b.png">



## ER図のリレーション表記法一覧

![無題の図形描画 (1)のコピー.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/bda5fa65-da55-1552-0801-9fad3a3da152.png)


これだけだと少しわかりにくいかもしれないので簡単な例をいくつかみてみましょう。

## `` 例1: `` １ 対 多
ユーザーログイン機能とツイートが出来る簡単なアプリケーションがあるとします。

データベースにはusersテーブルとtweetsテーブルの２つのテーブルが下図のようにあります。

このテーブル間の関係性としては**<font color= "red";>1<font color= "black";>対<font color= "blue";>多<font color= "black";>**となります。


<img width="716" alt="スクリーンショット 2019-12-12 23.30.35.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/db0614bc-e008-59e3-fefd-906472128b7e.png">


###<font color="red";>user<font color="black";>→→<font color="blue";>tweet
1人のuserに対してtweetの数は0か多
(※単なる"多"ではなく、"0か多(0以上)"として考えるのは一つもtweetをしないことも可能だからです)

![無題の図形描画 (1)のコピー2.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/6d7dcd3e-ca3c-fefe-2862-fa3a657baff6.png)

###<font color="blue";>tweet<font color="black";>→→<font color="red";>user
1つのtweetは必ず誰かuser1人が作成したもの。つまり、あるユーザーに属しているので下記の表記になります。
![無題の図形描画 (1)のコピー8.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/b90ff24e-e196-d5a5-91ff-69b0fc49fa37.png)

## ``例2`` 1 対 1
例１にprofilesテーブルとimagesテーブルをプラスしたもの
<img width="546" alt="スクリーンショット 2019-12-12 23.33.20.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/475fb891-559f-3506-1b32-eeab992d8135.png">



### <font color="red";>user<font color="black";>→→<font color="purple";>profile

### <font color="purple";>profile<font color="black";>→→<font color="red";>user

userから見ると
user1人に対してprofileは１つなので<font color="red";>1<font color="black";>対<font color="purple";>1<font color="black";>の関係となる。

逆も同じでprofile側から見ると
必ずuser１人に所属していると考えるので
![無題の図形描画 (1)のコピー8.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/35cf95b9-7815-43e1-a554-03e205d86434.png)


### <font color="blue";>tweet<font color="black";>→→<font color="green";>image
tweetから見たimageは
1tweetに対して最大1枚imageを持てるとし、
imageのないtweetもあるとするとリレーションは"０か1"となる
![無題の図形描画 (1)のコピー9.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/a10ff035-782a-699d-4f23-5106b133a333.png)

### <font color="green";>image<font color="black";>→→<font color="blue";>tweet
imageから見たtweet。
一方でimageは1tweetに必ず所属していると考えるので図のような関係性になります。
![68747470733a2f2f71696974612d696d6167652d73746f72652e73332e61702d6e6f727468656173742d312e616d617a6f6e6177732e636f6d2f302f3531333532342f62646135666136352d646135352d313535322d303830312d3966616433613364613135322e706e67.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/98c937af-2641-9523-b371-e043b94d5315.png)




## 1対多 ~制約がある場合~
tweetに対してimageの最低枚数に制約がある場合
<img width="756" alt="スクリーンショット 2019-12-13 0.03.50.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/22c79ee1-e5d4-6afb-044b-7c3e738d9f94.png">


### "1か多"とは <font color="Crimson">１対１<font color="black";>もしくは<font color="Crimson">1対複数のとき
例えば
オークションやフリーマーケットサイトでは１つの商品に対して画像が最低１枚は必要なのでこちら。１対１でも１対多でもOKな場合です。
![無題の図形描画 (1)のコピー11.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/2c882ac8-8720-abbb-da53-c70d1a85b045.png)


### 単なる　"多"　とは  <font color="MediumBlue">必ず1対複数、<font color="black";>つまり<font color="MediumBlue">２つ以上は必要
例えば
メッセージアプリなどでグループをつくるとなったらグループ内にメンバーが２人以上は必要ですよね。そんなときはこの表記になります。
![無題の図形描画 (1)のコピー12.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/40eda078-f5fe-582b-b2f6-bd9bdbaeadc6.png)


one and only oneなど厳密な制約を持たせる関係性もありますが、今回は大まかによく使われる基本的なもののみを取り上げました。気づいたところがあれば、随時更新いたします。


---
title: やさしい図解で学ぶ　ER図　表記法一覧
tags: ER図 Rails DB
author: ramuneru
slide: false
---
# ER図とは?
ER図もしくはERDとは 
 "Entity Relationship Diagram"のこと

DB設計において
「**テーブルとテーブルを線でつなぎ、中身の種類と関係性見やすくしたもの**」
と思っていただければ大丈夫です。 

プログラミング学習者の方であればどこかで<font color="blue";>”鳥の足”</font>みたいな先端で図表が結ばれたものを見たことがあるかもしれません。

それが<font color="red";>ERD<font color="black";>もしくは<font color="red";>ER図。

簡素なものですがたとえば下のような図です。

<img width="545" alt="スクリーンショット 2019-12-16 11.24.29.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/e1b3c21e-da70-a7a1-db80-f0de05a37f8b.png">



## ER図のリレーション表記法一覧

![無題の図形描画 (1)のコピー.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/bda5fa65-da55-1552-0801-9fad3a3da152.png)


これだけだと少しわかりにくいかもしれないので簡単な例をいくつかみてみましょう。

## `` 例1: `` １ 対 多
ユーザーログイン機能とツイートが出来る簡単なアプリケーションがあるとします。

データベースにはusersテーブルとtweetsテーブルの２つのテーブルが下図のようにあります。

このテーブル間の関係性としては**<font color= "red";>1<font color= "black";>対<font color= "blue";>多<font color= "black";>**となります。


<img width="716" alt="スクリーンショット 2019-12-12 23.30.35.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/db0614bc-e008-59e3-fefd-906472128b7e.png">


###<font color="red";>user<font color="black";>→→<font color="blue";>tweet
1人のuserに対してtweetの数は0か多
(※単なる"多"ではなく、"0か多(0以上)"として考えるのは一つもtweetをしないことも可能だからです)

![無題の図形描画 (1)のコピー2.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/6d7dcd3e-ca3c-fefe-2862-fa3a657baff6.png)

###<font color="blue";>tweet<font color="black";>→→<font color="red";>user
1つのtweetは必ず誰かuser1人が作成したもの。つまり、あるユーザーに属しているので下記の表記になります。
![無題の図形描画 (1)のコピー8.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/b90ff24e-e196-d5a5-91ff-69b0fc49fa37.png)

## ``例2`` 1 対 1
例１にprofilesテーブルとimagesテーブルをプラスしたもの
<img width="546" alt="スクリーンショット 2019-12-12 23.33.20.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/475fb891-559f-3506-1b32-eeab992d8135.png">



### <font color="red";>user<font color="black";>→→<font color="purple";>profile

### <font color="purple";>profile<font color="black";>→→<font color="red";>user

userから見ると
user1人に対してprofileは１つなので<font color="red";>1<font color="black";>対<font color="purple";>1<font color="black";>の関係となる。

逆も同じでprofile側から見ると
必ずuser１人に所属していると考えるので
![無題の図形描画 (1)のコピー8.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/35cf95b9-7815-43e1-a554-03e205d86434.png)


### <font color="blue";>tweet<font color="black";>→→<font color="green";>image
tweetから見たimageは
1tweetに対して最大1枚imageを持てるとし、
imageのないtweetもあるとするとリレーションは"０か1"となる
![無題の図形描画 (1)のコピー9.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/a10ff035-782a-699d-4f23-5106b133a333.png)

### <font color="green";>image<font color="black";>→→<font color="blue";>tweet
imageから見たtweet。
一方でimageは1tweetに必ず所属していると考えるので図のような関係性になります。
![68747470733a2f2f71696974612d696d6167652d73746f72652e73332e61702d6e6f727468656173742d312e616d617a6f6e6177732e636f6d2f302f3531333532342f62646135666136352d646135352d313535322d303830312d3966616433613364613135322e706e67.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/98c937af-2641-9523-b371-e043b94d5315.png)




## 1対多 ~制約がある場合~
tweetに対してimageの最低枚数に制約がある場合
<img width="756" alt="スクリーンショット 2019-12-13 0.03.50.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/22c79ee1-e5d4-6afb-044b-7c3e738d9f94.png">


### "1か多"とは <font color="Crimson">１対１<font color="black";>もしくは<font color="Crimson">1対複数のとき
例えば
オークションやフリーマーケットサイトでは１つの商品に対して画像が最低１枚は必要なのでこちら。１対１でも１対多でもOKな場合です。
![無題の図形描画 (1)のコピー11.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/2c882ac8-8720-abbb-da53-c70d1a85b045.png)


### 単なる　"多"　とは  <font color="MediumBlue">必ず1対複数、<font color="black";>つまり<font color="MediumBlue">２つ以上は必要
例えば
メッセージアプリなどでグループをつくるとなったらグループ内にメンバーが２人以上は必要ですよね。そんなときはこの表記になります。
![無題の図形描画 (1)のコピー12.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/513524/40eda078-f5fe-582b-b2f6-bd9bdbaeadc6.png)


one and only oneなど厳密な制約を持たせる関係性もありますが、今回は大まかによく使われる基本的なもののみを取り上げました。気づいたところがあれば、随時更新いたします。


