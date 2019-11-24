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
  - [check]上記5つに関しては、管理者とエンドユーザーで分けることで解消しそうです。
- ユーザーの退会確認画面のパスがない
- ユーザーの退会完了画面のパスがない

## cds
- indexは別でadminのパスがない
- showは別でadminのパスがない
  - [check]上記2つに関しては、管理者とエンドユーザーで分けることで解消しそうです。
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
  - [check]上記2つに関しては、管理者とエンドユーザーで分けることで解消しそうです。
- [add]URLが重複している部分があります。
  
## order_details
- いらない
  - [check]いらない理由も付記しておきましょう。

## admins
- showがトップページとおもっていいですか？
- editはワイヤーフレームがない
  - [check]指摘はOKです。ちなみに、show,editでURLが重複しています。
