#	TUTORIAL_COMP（チュートリアル突破）実装方法

　TUTORIAL_COMP（チュートリアル突破）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例

![Language](http://img.shields.io/badge/language-Objective–C-blue.svg?style=flat)
```objective-c
NSDictionary* eventInfo = @{
  @"product":@[@{@"id":@"XXXX"}]
};
CYZFoxEvent* event = [[CYZFoxEvent alloc] initWithEventName:@"_tutorial_comp"];
event.eventInfo = eventInfo;
[CYZFox trackEvent:event];
```

![Language](https://img.shields.io/badge/language-Swift-orange.svg?style=flat)
```Swift
let eventInfo: Dictionary = [
  "product":[["id":"XXXX"]]
]
let event:CYZFoxEvent = CYZFoxEvent.init(eventName:"_tutorial_comp")
event.eventInfo = eventInfo
CYZFox.trackEvent(event)
```

### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventName|NSString|"\_tutorial\_comp" を指定してください。|
|<span style="color:grey">action|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">label|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">value|<span style="color:grey">NSUInteger|<span style="color:grey">使用しません。|
|eventInfo|NSDictionary|イベント情報詳細 (以下参照)|

#### イベント情報詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventInfo (product)|NSDictionary|Product をキーとして商品IDを配列で設定します。
|&nbsp;&nbsp;eventInfo (product[].id)|NSDictionary|閲覧した商品IDを設定します。|

---
[戻る](/lang/ja/doc/fox_engagement/README.md)
