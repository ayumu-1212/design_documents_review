# アプリケーション詳細設計レビュー研修課題

# route

## 全体
- rootがない
- 管理者とエンドユーザーで分けていない
- deviseで生成されるパスに関する記述がない
- 支払い方法選択画面があるのでpaymentsコントローラなどが必要なのでは

## users
- indexはadminのみと明記しましょう
- showは別で別でadminのワイヤーフレームとパスがない
- editは別でadminのワイヤーフレームとパスがない
- updateは別でadminのパスがない
- destroyは別でadminのパスがない
- ユーザーの退会確認画面のパスがない
- ユーザーの退会完了画面のパスがない

## cds
- indexは別でadminのパスがない
- showは別でadminのパスがない
- editのパスはあるがワイヤーフレームがない

## addresses
- newがいらない
- editは別でadminのワイヤーフレームとパスがない
- updateは別でadminのパスがない
- destroyは別でadminのパスがない

## cart_items
- editはいらないのでは
- 目的覧でカートといっているが、カートアイテムに関してです

## orders
- indexは別でenduserのパスがない
- showはenduserのワイヤーフレームとadminのパスとワイヤーフレームがない

## order_details
- いらない

## admins
- showがトップページとおもっていいですか？
- editはワイヤーフレームがない

