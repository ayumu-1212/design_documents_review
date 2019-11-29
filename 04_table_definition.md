# テーブル定義書レビュー課題1
## 全体
- PKのカラム名は「id」と書きましょう
- 在庫数テーブルに関して記述しましょう
- products_id は product_id です
- buy_details_id は buy_detail_id です
- 全てのテーブルで"created_at"、"updated_at"の説明欄が同じになっていますので見直しましょう

## Admin
- テーブル名は複数形にしましょう
- テーブル名の情報はカラム名に入れなくていいです。
  - admin_email ⇒ email
  - admin_password ⇒ password
- admin_idにAUTO INCREMENTが適用しましょう
- admin_idにPKがチェックされていません
- admin_idにINDEXが適用されていません

## Users
- テーブル名の情報はカラム名に入れなくていいです。
- カラム名は省略してはいけません
  - user_l_name ⇒ last_name
  - user_f_name ⇒ first_name
  - user_l_kana ⇒ last_name_kana
  - user_f_kana ⇒ first_name_kana
  - ship_address ⇒ shipping_address
  - user_tel ⇒ telephon_number or phone_number
  - user_email ⇒ email
  - user_password ⇒ password
- 郵便番号・電話番号は先頭の0はどのように表現しますか？
- 配送先住所はここに保存されて大丈夫ですか？
- 退会ステータスはboolen型が好ましいです。
- 名・名カナがNOT NULLが外れています

## Products
- FKにindexを追加しましょう
- discとのリレーションを再度確認しましょう
- genre_idはFKです
- label_idはFKです
- artist_idはFKです
- テーブル名の情報はカラム名に入れなくていいです。
  - cd_image ⇒ image
  - cd_title ⇒ title
- 在庫数カラム、在庫ステータスカラムは不要です。テーブルを作成しましょう。
  - [check]在庫ステータスカラムも不要です。
    - [done]修正しました

## Discs
- カラム名は省略してはいけません
  - track_num ⇒ track_number
- また、track_numberの意味を考えてみると、ディスクごとの曲順を表す番号となります。
     したがって、このテーブルではなく、songsテーブルに持たせる必要があります。
  - [check]略語の指摘OKです。
     また、track_numberの意味を考えてみると、ディスクごとの曲順を表す番号となります。
     したがって、このテーブルではなく、songsテーブルに持たせる必要があります。
     - [done]修正いたしました。
- PKにINDEXが適用されていません
- products_idにINDEXが適用されていません。
- 同一商品で異なるディスクかどうかの判断ができません。ディスク名をカラムとして持たせる必要があります。
  - [add]同一商品で異なるディスクかどうかの判断ができません。ディスク名をカラムとして持たせる必要があります。
     (本来であればER図で指摘することですが、たまに見落としあるので注意が必要です。)
     - [done] 修正しました

## Songs
- PKがありません
- FKにAUTO INCREMENTは適用しません
- FKにINDEXは必要です
- テーブル名の情報はカラム名に入れなくていいです。
  - song ⇒ name

## Labels
- PKがありません
- FKにINDEXは必要です
- products_idはいりません
- テーブル名の情報はカラム名に入れなくていいです。
  - label ⇒ name

## Artists
- PKがありません
- テーブル名の情報はカラム名に入れなくていいです。
  - artist ⇒ name
- artist名カラムのデータ型は文字列です
- FKにAUTO INCREMENTは適用しません
- productsとのリレーションを確認しましょう

## Genre
- テーブル名が単数形
- PKがありません
- テーブル名の情報はカラム名に入れなくていいです。
  - genre ⇒ name
- FKにAUTO INCREMENTは適用しません
- productsとのリレーションを確認しましょう

## Cart item
- PKがありません
- テーブル名は複数形です
- テーブル名はスネークケースで書きましょう
- FKにAUTO INCREMENTは適用しません
- products_idのデータ型はintegerです
- カラムはスネークケースで書きましょう
- カラム名の省略はしません
  - buy num ⇒ buy_number
- また購入枚数を表すカラム名として"buy_number"はそもそも適切でしょうか。
    直訳すると「番号を買う」「購入番号」となる気がします。数量を表す単語として、もう少し適切なものはないか、考えてみましょう。
  - [check] 購入枚数を表すカラム名として"buy_number"はそもそも適切でしょうか。
    直訳すると「番号を買う」「購入番号」となる気がします。数量を表す単語として、もう少し適切なものはないか、考えてみましょう。
    - [done] 修正しました
- subtotalカラムは数量と価格で計算が容易なためカラムとして持たなくていいです。
  - [add]subtotalというカラムがありますが、必要ありません。必要ない理由を考え、レビュー文に追記してください。
    - [done]修正しました

# Buy details
- テーブル名はスネークケースで書きましょう
- 管理者目線で考えましょう
  - Buy detailis ⇒ Order_details
- カラムはスネークケースで書きましょう
- カラム名の省略はしません
  - buy num ⇒ buy_number
- また購入枚数を表すカラム名として"buy_number"はそもそも適切でしょうか。
    直訳すると「番号を買う」「購入番号」となる気がします。数量を表す単語として、もう少し適切なものはないか、考えてみましょう。
  - [check] 購入枚数を表すカラム名として"buy_number"はそもそも適切でしょうか(cart_itemと同じ指摘です)。
    - [done] 修正しました


## Buy
- テーブル名は複数形です
- 管理者目線で考えましょう
  - Buy ⇒ Orders
- FKにINDEXは必要です
- payカラムは名前で内容が伝わりづらいので名前を変えましょう
- カラム名の省略はしません
  - ship_address ⇒ shipping_address
  - ship_cost ⇒ shipping_cost
- 支払い合計カラムの命名が不十分です
  - stock ⇒ total_payment
- buy_atとcreated_atの違いは何ですか？
- 支払い方法はenumで管理しましょう
- buy_detailカラムを持っていますが、リレーションは大丈夫でしょうか。


-----------------------------------------------------------------------------------


# テーブル定義書レビュー課題2
## 全体
- PKのカラム名はidです
- sellテーブルとsell_detailsテーブルのリレーション関係を再度確認しましょう
- 在庫数テーブルに関して記述しましょう
- products_id ⇒ product_id
- sell_details_id ⇒ sell_detail_id

## admins
- テーブル名の情報はカラム名に入れなくていいです。
  - admin_email ⇒ email
  - admin_password ⇒ password
- admin_idにPKが○になっていませｎ
- admin_idにINDEXが適用されていません

## users
- テーブル名の情報はカラム名に入れなくていいです。
- カラム名は省略してはいけません
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
- テーブル名の情報はカラム名に入れなくていいです。
  - ship_name ⇒ name
  - ship_address ⇒ address
  - ship_tel ⇒ telephon_number or phone_number
  - ship_code ⇒ zip_code

## products
- FKにindexがありません
- テーブル名の情報はカラム名に入れなくていいです。
  - cd_image ⇒ image_id
  - cd_title ⇒ title or name
- 在庫数カラム、在庫ステータスカラムは不要です。テーブルを作成しましょう。

## discs
- カラム名は省略してはいけません
  - disc_num ⇒ disc_number
- PKにINDEXが適用されていません
- FKにINDEXが適用されていません

## songs
- テーブル名の情報はカラム名に入れなくていいです。
  - song ⇒ name
- カラム名は省略してはいけません
  - track_num ⇒ track_number

## labels
- テーブル名の情報はカラム名に入れなくていいです。
  - label ⇒ name

## artists
- テーブル名の情報はカラム名に入れなくていいです。
  - artist ⇒ name

## genres
- テーブル名の情報はカラム名に入れなくていいです。
  - genre ⇒ name

## cart items
- テーブル名はスネークケースで書きましょう
- products_idのデータ型はintegerです
- カラムはスネークケースで書きましょう
- カラム名は省略してはいけません
  - buy num ⇒ buy_number

# sell_details
- カラム名は省略してはいけません
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
