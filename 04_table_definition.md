# テーブル定義書レビュー課題1
## 全体
- PKのカラム名はidです
- buyテーブルとbuy detailsテーブルのリレーション関係が逆
- 在庫数テーブルがないです
- products_id ⇒ product_id
- buy_details_id ⇒ buy_detail_id
- [add] 全てのテーブルで"created_at"、"updated_at"が同名になっているので、名前の見直しが必要

## Admin
- テーブル名が単数形
- テーブル名の名前をカラムに入れている
  - admin_email ⇒ email
  - admin_password ⇒ password
- admin_idにAUTO INCREMENTが適用されていない
- admin_idにPKが○になっていない
- admin_idにINDEXが適用されていない

## Users
- テーブル名の名前をカラムに入れている
- カラム名を省略している
  - user_l_name ⇒ last_name
  - user_f_name ⇒ first_name
  - user_l_kana ⇒ last_name_kana
  - user_f_kana ⇒ first_name_kana
  - ship_address ⇒ shipping_address
  - user_tel ⇒ telephon_number or phone_number
  - user_email ⇒ email
  - user_password ⇒ password
- 郵便番号・電話番号はstring型です
- そもそも配送先住所はここに保存されない？
- 退会ステータスはboolen型がよい
- 名・名カナがNOT NULLが外れている

## Products
- FKにindexがない
- disc_idは不要です
- genre_idはFKです
- label_idはFKです
- artist_idはFKです
- 名前が不適切
  - cd_image ⇒ image
  - cd_title ⇒ title
- 在庫数カラムは不要です
  - [check]在庫ステータスカラムも不要です。

## Discs
- カラム名を省略している
  - track_num ⇒ track_number
  - [check]略語の指摘OKです。
     また、track_numberの意味を考えてみると、ディスクごとの曲順を表す番号となります。
     したがって、このテーブルではなく、songsテーブルに持たせる必要があります。
- PKにINDEXが適用されていません
- products_idはいりません
- [add]同一商品で異なるディスクかどうかの判断ができません。ディスク名をカラムとして持たせる必要があります。
  (本来であればER図で指摘することですが、たまに見落としあるので注意が必要です。)

## Songs
- PKがありません
- FKにAUTO INCREMENTは適用しません
- FKにINDEXは必要です
- テーブル名の名前をカラムに入れている
  - song ⇒ name

## Labels
- PKがありません
- FKにINDEXは必要です
- products_idはいりません
- テーブル名の名前をカラムに入れている
  - label ⇒ name

## Artists
- PKがありません
- テーブル名の名前をカラムに入れている
  - artist ⇒ name
- artist名カラムのデータ型は文字列です
- FKにAUTO INCREMENTは適用しません
- products_idはいりません

## Genre
- テーブル名が単数形
- PKがありません
- テーブル名の名前をカラムに入れている
  - genre ⇒ name
- FKにAUTO INCREMENTは適用しません
- products_idはいりません

## Cart item
- PKがありません
- テーブル名が単数形
- テーブル名はスネークで書きましょう
- FKにAUTO INCREMENTは適用しません
- products_idのデータ型はintegerです
- カラムはスネークで書きましょう
- カラム名の省略はしません
  - buy num ⇒ buy_number
  - [check] 購入枚数を表すカラム名として"buy_number"はそもそも適切でしょうか。
    直訳すると「番号を買う」「購入番号」となる気がします。数量を表す単語として、もう少し適切なものはないか、考えてみましょう。
- [add]subtotalというカラムがありますが、必要ありません。必要ない理由を考え、レビュー文に追記してください。

# Buy details
- テーブル名はスネークで書きましょう
- 管理者目線で考えましょう
  - Buy detailis ⇒ Order_details
- カラムはスネークで書きましょう
- カラム名の省略はしません
  - buy num ⇒ buy_number
  - [check] 購入枚数を表すカラム名として"buy_number"はそもそも適切でしょうか(cart_itemと同じ指摘です)。


## Buy
- テーブル名が単数形
- 管理者目線で考えましょう
  - Buy ⇒ Orders
- FKにINDEXは必要です
- payカラムは名前で内容が伝わらない
- カラム名の省略はしません
  - ship_address ⇒ shipping_address
  - ship_cost ⇒ shipping_cost
- 支払い合計カラムの命名が不十分です
  - stock ⇒ total_payment
- buy_atとcreated_atの違いは何ですか？
- 支払い方法はenumで管理しましょう


-----------------------------------------------------------------------------------


# テーブル定義書レビュー課題2
## 全体
- PKのカラム名はidです
- sellテーブルとsell_detailsテーブルのリレーション関係が逆
- 在庫数テーブルがないです
- products_id ⇒ product_id
- sell_details_id ⇒ sell_detail_id

## admins
- テーブル名の名前をカラムに入れている
  - admin_email ⇒ email
  - admin_password ⇒ password
- admin_idにPKが○になっていない
- admin_idにINDEXが適用されていない

## users
- テーブル名の名前をカラムに入れている
- カラム名を省略している
  - user_l_name ⇒ last_name
  - user_f_name ⇒ first_name
  - user_l_kana ⇒ last_name_kana
  - user_f_kana ⇒ first_name_kana
  - ship_address ⇒ shipping_address
  - user_tel ⇒ telephon_number or phone_number
  - user_email ⇒ email
  - user_password ⇒ password

## ships
- PKにINDEXが適用されていません
- FKにINDEXが適用されていません
- テーブル名の名前をカラムに入れている
  - ship_name ⇒ name
  - ship_address ⇒ address
  - ship_tel ⇒ telephon_number or phone_number
  - ship_code ⇒ zip_code

## products
- FKにindexがない
- 名前が不適切
  - cd_image ⇒ image_id
  - cd_title ⇒ title or name
- 在庫数カラムは不要です

## discs
- カラム名を省略している
  - disc_num ⇒ disc_number
- PKにINDEXが適用されていません
- FKにINDEXが適用されていません

## songs
- テーブル名の名前をカラムに入れている
  - song ⇒ name
- カラム名の省略はしません
  - track_num ⇒ track_number

## labels
- テーブル名の名前をカラムに入れている
  - label ⇒ name

## artists
- テーブル名の名前をカラムに入れている
  - artist ⇒ name

## genres
- テーブル名の名前をカラムに入れている
  - genre ⇒ name

## cart items
- テーブル名はスネークケースで書きましょう
- products_idのデータ型はintegerです
- カラムはスネークケースで書きましょう
- カラム名の省略はしません
  - buy num ⇒ buy_number

# sell_details
- カラム名の省略はしません
  - buy num ⇒ buy_number
- 商品IDのFK覧に○がない
- FKにINDEXは必要です

## sells
- PKにINDEXは必要です
- FKにINDEXは必要です
- payカラムは名前で内容が伝わらない
- カラム名の省略はしません
  - ship_address ⇒ shipping_address
  - ship_tel ⇒ shipping_phone_number
  - ship_code ⇒ shipping_zip_code
  - ship_name ⇒ shipping_name
  - ship_cost ⇒ shipping_cost
