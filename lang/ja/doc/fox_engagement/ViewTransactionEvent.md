# Track Transaction（商品購入イベント）実装方法

Track Transaction（商品購入）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例


![Language](http://img.shields.io/badge/language-Objective–C-blue.svg?style=flat)
```objective-c
NSDictionary* eventInfo = {
  @"transaction_id": @"ABC",
  @"product":@[
    {@"id":@"1234",@"price":@100,@"quantity":@1, @"currency": @"JPY", @"category": @"display"},
    {@"id":@"1235",@"price":@200,@"quantity":@2, @"currency": @"THB", @"category": @"av"},
    {@"id":@"1236",@"price":@300,@"quantity":@3, @"currency": @"USD", @"category": @"car"}
  ],
  @"din":@"2016-01-02",
  @"dout":@"2016-01-05",
  @"origin":@"XXXXX",
  @"destination":@"XXXXX",
  @"criteo_partner_id":@"XXXXX"
};

CYZFoxEvent* event = [[CYZFoxEvent alloc] initWithEventName:@"_purchase"];
event.eventInfo = eventInfo;
event.currency = @"JPY";
event.price = 2750;
event.quantity = 1;
event.sku = @"ABC789";
event.orderId = @"ABCDFE";
[CYZFox trackEvent:event];
```

![Language](https://img.shields.io/badge/language-Swift-orange.svg?style=flat)
```Swift
let eventInfo: Dictionary = [
  "transaction_id": "ABC",
  "din": "2018-05-01",
  "dout": "2018-05-30",
  "origin": "XXXX",
  "destination": "XXXX",
  "criteo_partner_id": "XXXXX",
  "product":[
    ["id":"1234", "price": 100, "quantity": 1, "currency": "JPY", "category":"display"],
    ["id":"1235", "price": 200, "quantity": 2, "currency": "THB", "category":"av"],
    ["id":"1236", "price": 300, "quantity": 3, "currency": "USD", "category":"car"]
  ]
]
let event:CYZFoxEvent = CYZFoxEvent.init(eventName:"_purchase")
event.eventInfo = eventInfo
event.currency = "JPY"
event.price = 2750
event.quantity = 1
event.sku = "ABC789"
event.orderId = "ABCDFE"
CYZFox.trackEvent(event)
```

### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventName|NSString|任意の名前を指定してください。特に指定がない場は、"_purchase" を指定してください。|
|<span style="color:grey">action|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">label|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|orderID|NSString|（任意）注⽂番号等を指定します。|
|sku|NSString|（任意）商品コード等を指定します。|
|<span style="color:grey">itemName|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|price|double|商品総額を指定します。<br><span style="color:red">※必ず price * quantity の値が商品総額となるよう指定ください|
|quantity|NSUInteger|1を指定してください。|
|currency|NSUInteger|通貨コードを指定します。<br>nilの場合は”JPY”が指定されます。|
|eventInfo|NSDictionary|イベント情報詳細 (以下参照)|

#### イベント情報詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventInfo (transaction_id)|NSDictionary|注文番号、問い合わせ番号などのトランザクションID|
|eventInfo (product)|JSONArray|Product をキーとして商品IDを配列で設定します。
|&nbsp;&nbsp;eventInfo (product[].id)|NSDictionary|商品IDデータフィードと同じ商品IDを使用してください。|
|&nbsp;&nbsp;eventInfo (product[].price)|NSDictionary|該当商品の価格を設定します。|
|&nbsp;&nbsp;eventInfo (product[].quantity)|NSDictionary|該当商品を買った個数を設定します。|
|&nbsp;&nbsp;eventInfo (product[].currency)|NSDictionary|通貨コードを設定します。|
|&nbsp;&nbsp;eventInfo (product[].category)|NSDictionary|カテゴリIDを設定します。|
|eventInfo (din/dout)|NSDictionary|⽇付の指定がある場合は⼊⼒してください。（任意）|
|eventInfo (origin/destination)|NSDictionary|出発地点／行先の指定がある場合は入力（旅行アプリなど）（任意）|
|eventInfo (criteo_partner_id)|NSDictionary|Criteo アカウントID が同⼀アプリで異なる場合は⼊⼒(任意)<br>


---
[戻る](/lang/ja/doc/fox_engagement/README.md)
