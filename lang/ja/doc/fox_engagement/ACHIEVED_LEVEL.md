#	ACHIEVED_LEVEL（レベル到達）実装方法

　ACHIEVED_LEVEL（レベル到達）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例

![Language](http://img.shields.io/badge/language-Objective–C-blue.svg?style=flat)
```objective-c
NSDictionary* eventInfo = @{
  @"track_info":@[@{@"main_level":@"XX"}]
};
CYZFoxEvent* event = [[CYZFoxEvent alloc] initWithEventName:@"_achieved_level"];
event.eventInfo = eventInfo;
[CYZFox trackEvent:event];
```

![Language](https://img.shields.io/badge/language-Swift-orange.svg?style=flat)
```Swift
let eventInfo: Dictionary = [
  "track_info":[["main_level":"XX"]]
]
let event:CYZFoxEvent = CYZFoxEvent.init(eventName:"_achieved_level")
event.eventInfo = eventInfo
CYZFox.trackEvent(event)
```

### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventName|NSString|"\_achieved\_level" を指定してください。|
|eventInfo|NSDictionary|イベント情報詳細 (以下参照)|

#### イベント情報詳細

| 引数 | 型 | 概要 | 必須 |
|:----------|:-----------:|:------------|:------------|
|eventInfo (track_info)|NSDictionary|レベル情報を配列で入力| ○ |
|&nbsp;&nbsp;eventInfo (track_info[].main_level)|NSDictionary|到達レベルを入力| ○ |

---
[戻る](/lang/ja/doc/fox_engagement/README.md)
