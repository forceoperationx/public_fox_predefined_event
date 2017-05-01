#	ACHIEVED_LEVEL（レベル到達）実装方法

　ACHIEVED_LEVEL（レベル到達）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例

```objective-c
[ForceAnalyticsManager sendEvent:@"_achieved_level"
                                action: nil
                                label: nil
                                value: 0
                                eventInfo:@{
                                  @"track_info":@[@{@"main_level":@"XX"}]
                                }
];
```

### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventName|NSString|"\_achieved\_level" を指定してください。|
|<span style="color:grey">action|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">label|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">value|<span style="color:grey">NSUInteger|<span style="color:grey">使用しません。|
|eventInfo|NSDictionary|イベント情報詳細 (以下参照)|

#### イベント情報詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventInfo (track_info)|NSDictionary|レベル情報を配列で入力
|&nbsp;&nbsp;eventInfo (track_info[].main_level)|NSDictionary|到達レベルを入力|

---
[戻る](/lang/ja/doc/fox_engagement/README.md)

