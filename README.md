# テーブル設計

## users テーブル

| Column             | Type    | option      |
| ------------------ | ------- | -----------
| email              | string  | null: false, unique: true|
| encrypted_password | string  | null: false |
| name               | string  | null: false |
| profile            | text    | null: false |
| occupation         | text    | null: false |
| position           | text    | null: false |

### Association

- has_many :prototype_users
- has_many :prototypes, through: :prototype_users
- has_many :comments

## prototypes テーブル

| Column     | Type      | option      |
| ---------- | --------- | ----------- |
| title      | string    | null: false |
| catch_copy | text      | null: false |
| concept    | text      | null: false |
| user       | reference | null: false, foreign_key: true |

### Association

- has_many :prototype_users
- has_many :prototypes, through: :prototype_users
- has_many :comments

## prototype_users テーブル

| Column    | Type      | option
| --------- | --------- | ------------------------------ |
| user      | reference | null: false, foreign_key: true |
| prototype | reference | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :prototype

## comments テーブル

| Column    | Type      | option      |
| --------- | --------- | ----------- |
| content   | text      | null: false |
| prototype | reference | null: false, foreign_key: true |
| user      | reference | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :prototype