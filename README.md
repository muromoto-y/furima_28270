# テーブル設計

## users テーブル

| Column     | Type   | Options     |
| ---------- | ------ | ----------- |
| first_name | string | null: false |
| last_name  | string | null: false |
| nick_name  | string | null: false |
| email      | string | null: false |
| password   | string | null: false |

### Association

- has_many :items
- has_many :deliveries
- has_many :purchase

## items テーブル

| Column           | Type   | Options     |
| ---------------- | ------ | ----------- |
| item_name        | string | null: false |
| item_explanation | text   | null: false |
| selling_price    | string | null: false |

### Association

- has_many :deliveries, through: item_deliveries
- belongs_to :user
- has_one :purchase

## item_deliveries テーブル

| Column     | Type       | Options                        |
| ---------- | ---------- | ------------------------------ |
| item       | references | null: false, foreign_key: true |
| delivery   | references | null: false, foreign_key: true |

### Association

- belongs_to :item
- belongs_to :delivery

## deliveries テーブル

| Column        | Type   | Options     |
| ------------- | ------ | ----------- |
| post_code     | string | null: false |
| city          | string | null: false |
| address       | string | null: false |
| building_name | string |             |
| phone_number  | string | null: false |

### Association

- belongs_to :user
- has_many :items, through: item_deliveries

# purchase テーブル

| Column      | Type   | Options     |
| ----------- | ------ | ----------- |
| deadline    | string | null: false |
| card_number | string | null: false |
| security    | string | null: false |

### Association

- belongs_to :user
- has_one :item