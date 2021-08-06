# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


## users テーブル
| Column | Type | Options |
| ------------------ | ------ | ----------------------  |
| nickname           | string | null: false             |
| email              | string | null: false unique true |
| encrypted_password | string | null: false             |

### Association
- has_many :items
- has_many :purchase_histories

## items テーブル
| Column | Type | Options |
| ---------------------- | ---------- | ------------------------------ |
| name                   | string     | null: false                    |
| info                   | text       | null: false                    |
| price                  | integer    | null: false                    |
| category_id            | integer    | null: false                    |Active hash
| user                   | references | null: false, foreign_key: true |
image < active storage
### Association
- has_one :purchase_history
- belongs_to :user

## purchase_histories テーブル
| Column | Type | Options |
| ---------------- | ---------- | ------------------------------ |
| postal_code      | string     | null: false                    |
| prefecture_id    | integer    | null: false                    |
| city             | string     | null: false                    |
| addresses        | string     | null: false                    |
| building         | string     |                                |
| phone_number     | string     | null: false                    |
| order            | references | null: false, foreign_key: true |
### Association
- belongs_to :order

## orders テーブル
| Column | Type | Options |
| ------------- | ---------- | ------------------------------ |
| user          | references | null: false, foreign_key: true |
| item          | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :item
- has_one :purchase_history