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


## health_statuses テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| status             | string     | null: false                    |
| notes              | text       | null: false                    |
| user               | references | null: false, foreign_key: true |

## comments テーブル

| Column             | Type        | Options                        |
| ------------------ | ----------- | ------------------------------ |
| content            | text        | null: false                    |
| health_statuse     | references  | null: false, foreign_key: true |
| users              | references  | null: false, foreign_key: true |
