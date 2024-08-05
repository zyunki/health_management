# オリジナルアプリ

<img width="557" alt="logo" src="https://github.com/user-attachments/assets/f01be728-5b13-403c-87a3-a3c1be9dba3e">

良い体調を維持し、自ら、人生豊かにしていこう！

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
