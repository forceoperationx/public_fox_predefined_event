#	View Toppage(アプリトップ訪問イベント)実装方法
　View Toppage（ホーム画面）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例


![Language](http://img.shields.io/badge/language-Objective–C-blue.svg?style=flat)
```objective-c
NSDictionary* eventInfo = {
  @"din":@"2016-01-02",
  @"dout":@"2016-01-05",
  @"origin":@"XXXXX",
  @"destination":@"XXXXX",
  @"criteo_partner_id":@"XXXXX"
};

CYZFoxEvent* event = [[CYZFoxEvent alloc] initWithEventName:@"_view_toppage"];
event.eventInfo = eventInfo;
[CYZFox trackEvent:event];
```

![Language](https://img.shields.io/badge/language-Swift-orange.svg?style=flat)
```Swift
let eventInfo: Dictionary = [
  "din": "2018-05-01",
  "dout": "2018-05-30",
  "origin": "XXXX",
  "destination": "XXXX",
  "criteo_partner_id": "XXXXX"
]
let event:CYZFoxEvent = CYZFoxEvent.init(eventName:"_view_toppage")
event.eventInfo = eventInfo
CYZFox.trackEvent(event)
```


### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventName|NSString|“\_view\_toppage”を指定してください。|
|<span style="color:grey">action|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">label|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">value|<span style="color:grey">NSUInteger|<span style="color:grey">使用しません。|
|eventInfo|NSDictionary|イベント情報詳細 (以下参照)|


#### イベント情報詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventInfo (din/dout)|NSDictionary|日付の指定がある場合は入力（任意）|
|eventInfo (origin/destination)|NSDictionary|出発地点／行先の指定がある場合は入力（旅行アプリなど）（任意）|
|eventInfo (criteo_partner_id)|NSDictionary|CriteoアカウントIDが同一アプリで異なる場合は入力(任意)|

---
[戻る](/lang/ja/doc/fox_engagement/README.md)
