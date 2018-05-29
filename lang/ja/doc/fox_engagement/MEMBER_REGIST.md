#	MEMBER_REGIST（会員登録イベント）実装方法

　MEMBER_REGIST（会員登録イベント）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例

![Language](http://img.shields.io/badge/language-Objective–C-blue.svg?style=flat)
```objective-c
NSDictionary* eventInfo = @{
  @"registration_method":@"XXXXX"
};
CYZFoxEvent* event = [[CYZFoxEvent alloc] initWithEventName:@"_member_regist"];
event.eventInfo = eventInfo;
[CYZFox trackEvent:event];
```

![Language](https://img.shields.io/badge/language-Swift-orange.svg?style=flat)
```Swift
let eventInfo: Dictionary = [
  "registration_method":"XXXXX"
]
let event:CYZFoxEvent = CYZFoxEvent.init(eventName:"_member_regist")
event.eventInfo = eventInfo
CYZFox.trackEvent(event)
```

### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventName|NSString|"\_member\_regist" を指定してください。|
|<span style="color:grey">action|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">label|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">value|<span style="color:grey">NSUInteger|<span style="color:grey">使用しません。|
|eventInfo|NSDictionary|イベント情報詳細 (以下参照)|

#### イベント情報詳細

| 引数 | 型 | 概要 | 必須 |
|:----------|:-----------:|:------------|
|eventInfo (registration_method)|NSDictionary|Facebook,Twitter,EmailなどをJSONに設定する| × |

---
[戻る](/lang/ja/doc/fox_engagement/README.md)
