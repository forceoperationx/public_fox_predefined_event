#	View Search(アプリ内検索イベント)実装方法
　View Search（検索画面）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例


![Language](http://img.shields.io/badge/language-Objective–C-blue.svg?style=flat)
```objective-c
NSDictionary* eventInfo = {
	@"search_term":@"XXXXX",
	@"product":@[@{@"id":@"111", @"item_location_id":@"XXXXX"}],
  @"din":@"2016-01-02",
  @"dout":@"2016-01-05",
  @"origin":@"XXXXX",
  @"destination":@"XXXXX",
  @"criteo_partner_id":@"XXXXX"
};

CYZFoxEvent* event = [[CYZFoxEvent alloc] initWithEventName:@"_search"];
event.eventInfo = eventInfo;
[CYZFox trackEvent:event];
```

![Language](https://img.shields.io/badge/language-Swift-orange.svg?style=flat)
```Swift
let eventInfo: Dictionary = [
  "search_term": "XXXXX",
  "din": "2018-05-01",
  "dout": "2018-05-30",
  "origin": "XXXX",
  "destination": "XXXX",
  "criteo_partner_id": "XXXXX",
  "product":[
    ["id":"1234", "item_location_id": "XXXXX"]
  ]
]
let event:CYZFoxEvent = CYZFoxEvent.init(eventName:"_search")
event.eventInfo = eventInfo
CYZFox.trackEvent(event)
```

### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventName|NSString|“\_search”を指定してください。|
|<span style="color:grey">action|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">label|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">value|<span style="color:grey">NSUInteger|<span style="color:grey">使用しません。|
|eventInfo|NSDictionary|イベント情報詳細 (以下参照)|


#### イベント情報詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventInfo (product)|NSDictionary|Product をキーとして商品IDを配列で設定します。
|&nbsp;&nbsp;eventInfo (product[].id)|NSDictionary|検索された商品IDを設定します。|
|&nbsp;&nbsp;eventInfo (product[].item_location_id)|NSDictionary|商品の広告を特定の場所や地域に訴求したい場合指定（任意）|
|eventInfo (search_term)|NSDictionary|検索キーワードを入力|
|eventInfo (din/dout)|NSDictionary|日付の指定がある場合は入力（任意）|
|eventInfo (origin/destination)|NSDictionary|出発地点／行先の指定がある場合は入力（旅行アプリなど）（任意）|
|eventInfo (criteo_partner_id)|NSDictionary|CriteoアカウントIDが同一アプリで異なる場合は入力(任意)|

---
[戻る](/lang/ja/doc/fox_engagement/README.md)
