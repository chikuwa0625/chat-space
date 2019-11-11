
# chat-space DB設計
## userテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false, password.match(/[a-z\d]{8,}/i)|
|nickname|string|null: false, index: true|
### Association
- has_many :messages
- has_many :groups
- has_many :user_groups, through: :user_groups

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :users
- has_many :messages
- has_many :user_groups

## messageテーブル
|Column|Type|Options|
|------|----|-------|
|text|string|
|image|string|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## user_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

