# オリジナルアプリ

<img width="557" alt="logo" src="https://github.com/user-attachments/assets/f01be728-5b13-403c-87a3-a3c1be9dba3e">

良い体調を維持し、自ら、人生豊かにしていこう！



## 体調管理アプリを作ろうと思った経緯

どの職種についても、コミニュケーション能力が必要不可欠。

現状、コミニュケーション不足に悩んでいたり課題を感じている

→
仕事の仲間一人ひとりの事を理解できていない
長所、短所を知らない
指示する内容が適切でない

人間一人ひとりとコミニュケーション不足を解消するためにきっかけとなる
体調やメンタル面が分かる体調管理アプリを作成することになりました！



## アプリ開発考察の背景
＜コミニュケーションが不足＞

・人には毎日、それぞれやる気にムラが生じる

・相手の能力、適性などを理解せず、指示を出すことにより期待値操作が出来ない

＜体調管理アプリの影響＞

・一人ひとりの体調を把握することでコミニュケーションのきっかけを作る

・タイミングを見極め、有効的な作業の指示を出すことができる

・相手の興味のあることや仕事に対する考え方に関心を持つことが
　出来、お互いの心が開く

 

## オリジナルアプリの概要

＜テーマ＞　　個々のスキルの共有を円滑に行い風通しの良い職場へ

＜コンセプト＞　　係内の仕事力向上

＜提供価値＞　　容易に仲間とのコミニュケーションが可能

＜対象者＞　　労働者をマネジメントする管理職、チームリーダー



## 各機能
⭐️体調管理機能
・５つの体調の状態から選択し投稿
・補足情報を文章で追加
（何かきっかけがあったのか、なぜそうなったのか）　
![体調管理アプリ](https://github.com/user-attachments/assets/0cd8190d-019a-4f7a-ba67-6e345fa7cd0c)



⭐️ユーザ管理機能
・氏名、プロフィール画像、性別、自己紹介文、役職


⭐️コメント機能
・コメント、ユーザー

## トップページ（体調一覧ページ）
<img width="847" alt="スクリーンショット 2024-08-06 0 35 46" src="https://github.com/user-attachments/assets/fa7f4872-f15a-4c44-aa31-8812d8ad5133">



# テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| name               | string | null: false               |
| first_name         | string | null: false               |
| last_name          | string | null: false               |
| first_name_kana    | string | null: false               |
| last_name_kana     | string | null: false               |
| gender             | string | null: false               |
| introduction       | text   | null: false               | 
| position           | string | null: false               |

### Association

* has_many :health_statuses
* has_many :comments


## health_statuses テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| status             | string     | null: false                    |
| notes              | text       | null: false                    |
| user               | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :comments

## comments テーブル

| Column             | Type        | Options                        |
| ------------------ | ----------- | ------------------------------ |
| content            | text        | null: false                    |
| health_statuse     | references  | null: false, foreign_key: true |
| users              | references  | null: false, foreign_key: true |

### Association

- belongs_to :health_statuses
- belongs_to :user
