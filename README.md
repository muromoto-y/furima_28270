# テーブル設計

## users テーブル

| Column              | Type   | Options     |
| ------------------- | ------ | ----------- |
| first_name          | string | null: false |
| last_name           | string | null: false |
| first_name_furigana | string | null: false |
| last_name_furigana  | string | null: false |
| birthday            | string | null: false |
| nick_name           | string | null: false |
| email               | string | null: false |
| password            | string | null: false |

### Association

- has_many :items
- has_many :deliveries
- has_many :purchases

## items テーブル

| Column          | Type   | Options     |
| --------------- | ------ | ----------- |
| name            | string | null: false |
| explanation     | text   | null: false |
| selling_price   | string | null: false |
| category        | string | null: false |
| Status          | string | null: false |
| shipping burden | string | null: false |
| shipping area   | string | null: false |
| shipping days   | string | null: false |

### Association

- belongs_to :user
- has_one :purchase

## deliveries テーブル

| Column        | Type   | Options     |
| ------------- | ------ | ----------- |
| post_code     | string | null: false |
| city          | string | null: false |
| address       | string | null: false |
| building_name | string |             |
| phone_number  | string | null: false |
| prefectures   | string | null: false |

### Association

- belongs_to :user
- has_one :purchase


# purchase テーブル

### Association

- belongs_to :user
- belongs_to :item
- belongs_to :delivery