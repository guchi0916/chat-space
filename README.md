# ChatSpace DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false|
|password|string|null: false|

### Association
- has_many :group,  through: groups_users
- has_many messages

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|string||
|body|text|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :users
- belongs_to :groups

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|
|member|string|

### Association
- has_many :use,  through: groups_users
- has_many :messages

## users_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|users_id|integer|null: false, foreign_key: true|
|groups_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :users
- belongs_to :groups