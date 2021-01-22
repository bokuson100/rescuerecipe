# アプリ名
　"レスキューレシピ"

# 概要（このアプリでできること）
　疲れて帰宅してから短時間で夕食を作る際に手間別、材料数、工程数、料理カテゴリーでレシピをサクっと検索でき、作れる料理がすぐに決められる。

# 制作背景（意図）
　私自身もそうであるように食事の準備を担っている女性によって仕事後の夕食の準備は献立検索、決定、買い出し、調理、ととても負担が重い。そんな時は作らずに外食やデリバリーで良いのではという意見もありそうだが、コスト的にも栄養管理的にも自炊しなければという使命感もある。そんな働く女性にとって余裕の無い平日（土日出勤の方は土日）夜の時間が少しでもゆとりある生活になるよう、夕食作りに関わる献立検索、決定、調理の手間を軽くするためにこのアプリを開発する。

# DEMO
# 実装予定の内容
　・レシピ登録機能
　・レシピ検索機能
　・ユーザー登録機能
　・お気に入り登録機能

# DB設計
## recipe テーブル

| Column             | Type       | Options     |
| ------------------ | ---------- | ----------- |
| web_page_url       | string     | null: false |
| recipe_name        | string     | null: false |
| effort_id          | integer    | null: false |
| material_id        | integer    | null: false |
| process_id         | integer    | null: false |
| category_id        | integer    | null: false |

### Association
- has_many : favorite


## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |
| first_name_kanji   | string | null: false |
| last_name_kanji    | string | null: false |
| first_name_kana    | string | null: false |
| last_name_kana     | string | null: false |

- has_many : favorite

## favorite テーブル
| Column | Type       | Options                      |
| ------ | ---------- | ----------------------------- |
| recipe | references | null: false, foreign_key:true |
| user   | references | null: false, foreign_key:true |

### Association

- belongs_to :recipe
- belongs_to :user

