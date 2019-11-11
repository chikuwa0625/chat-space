
# chat-space DB設計
## userテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false, password.match(/[a-z\d]{8,}/i)|
|nickname|string|null: false, index: true|
### Association
- has_many :messages
- has_many :groups, throug: :user_group

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, foreign_key: true|
|user_group_id|integer|null: false|
### Association
- has_many :users, throug: :user_group
- has_many :messages

## messageテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|string|null: false|r
|user_id|integer|null: false|
### Association
- belongs_to :user
- belongs_to :group

## user_groupテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

