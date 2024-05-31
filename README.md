# テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| nickname           | string | null: false               |
| name               | string | null: false               |
| birth_date         | DATE   | null: false               |

### Association

- has_many :product
- has_many :purchase

## product テーブル

| Column       | Type       | Options         |
| ------------ | ---------- | --------------- |
| product_name | string     | null: false     |
| description  | text       | null: false     |
| category     | string     | null: false     |
| condition    | text       | null: false     |
| cost         | text       | null: false     |
| local        | string     | null: false     |
| days         | string     | null: false     |
| price        | integer    | null: false     |

### Association

- belongs_to :users
- has_many :purchase

## shipping テーブル

| Column         | Type       | Options         |
| -------------- | ---------- | --------------- |
| post_code      | string     | null: false     |
| prefectures    | string     | null: false     |
| municipalities | string     | null: false     |
| address        | string     | null: false     |
| building_name  | string     | null: true      |
| phone_number   | string     | null: false     |

### Association

- has_one :purchase

## purchase テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| total_price | integer    | null: false                    |
| token       | string     | null: false                    |
| user        | references | null: false, foreign_key: true |
| product     | references | null: false, foreign_key: true |
| shipping    | references | null: false, foreign_key: true |

### Association

- belongs_to :users
- belongs_to :product
- belongs_to :shipping
