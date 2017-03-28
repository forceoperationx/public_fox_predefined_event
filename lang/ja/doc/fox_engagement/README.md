# F.O.X事前定義イベント
## 1. 概要
本ドキュメントでは、Force Operation X SDK(以下F.O.X)における各媒体とのアクセス解析イベントの連携を行う際に必要となる実装を説明します。

* **対応F.O.X iOS SDKバージョン** : `v2.16g`以上

### 1.1.	SDK仕様
F.O.X SDKアクセス解析機能を利用することにより媒体を横断したイベント計測連携を行います。計測は内容に応じて各種メソッドを実行することで行います。

#### イベント情報の送信

ヘッダファイル AnalyticsManager.hをインポートします。
```objective-c
 #import "AnalyticsManager.h"
```

次のsendEventメソッドを利用し、イベント情報を送信します。
```objective-c
+ (void)sendEvent:(NSString*)eventName
           action:(NSString*)action
            label:(NSString*)label
          orderID:(NSString*)orderID
              sku:(NSString*)sku
         itemName:(NSString*)itemName
            price:(double)price
         quantity:(NSUInteger)quantity
         currency:(NSString*)currency;
         eventInfo:(NSDictionary*)eventInfo;
```

### sendEventメソッド 引数

引数それぞれのパラメータの仕様は以下の通りです。

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventName|String|計測を行うイベント種別に応じて、指定されたイベント名を設定します。|
|<span style="color:grey">action|<span style="color:grey">String|<span style="color:grey">使用しません。|
|<span style="color:grey">label	|<span style="color:grey">String|<span style="color:grey">使用しません。|
|orderId|String|(任意)注⽂番号等を指定します。|
|sku	|String|(任意)商品コード等を指定します。|
|<span style="color:grey">itemName|<span style="color:grey">String|<span style="color:grey">使用しません。|
|<span style="color:grey">value	|<span style="color:grey">int|<span style="color:grey">使用しません。|
|price|double|	売上金額を指定します。|
|quantity|int|	数量を指定します。<br>price * quantityが売上金額として計上されます。|
|currency|String|通貨コードを指定します。nullの場合は”JPY”が指定されます。|
|eventInfo|JSONObject|下記の仕様のとおりにJsonを指定します。|

### 1.2. eventInfo仕様
eventInfo内にアクションに付随する情報をJson形式で設定することで、ダイナミックな配信連携が可能になります。
Jsonの仕様は以下の通りです。

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|product|Array|閲覧した、カートに入れた等の商品の設定領域です。|
|&nbsp;&nbsp;product[].id|String|閲覧した、カートに入れた等の商品IDを設定します。|
|&nbsp;&nbsp;product[].price|double|閲覧した、カートに入れた等の商品単価を設定します。|
|&nbsp;&nbsp;product[].quantity|int|閲覧した、カートに入れた等の商品数量を設定します。|
|&nbsp;&nbsp;product[].category|String|閲覧した、カートに入れた等の商品カテゴリを指定します。<br>複数ある場合はカンマ「,」区切り、階層がある場合は「>」で分割します。<br>例）映画、ビデオ>DVD>スポーツ、レジャー|
|din|String|開始日の指定がある場合に設定します。|
|dout|String|終了日の指定がある場合に指定します。|
|origin|String|出発地点指定がある場合に設定します。|
|destination|String|行先の指定がある場合に指定します。|
|criteo_partner_id|String|CriteoアカウントIDが同一アプリで異なる場合に設定します。|

　　　
## 2.イベント計測の実装
F.O.X SDKで対応している媒体のイベント計測は以下の6つとなっています。

* [> View Toppage イベント](./ViewToppageEvent.md)
* [> View Search イベント](./ViewSearchEvent.md)
* [> View Listing イベント](./ViewListingEvent.md)
* [> View Product イベント](./ViewProductEvent.md)
* [> View Basket イベント](./ViewBasketEvent.md)
* [> Track Transaction イベント](./ViewTransactionEvent.md)




