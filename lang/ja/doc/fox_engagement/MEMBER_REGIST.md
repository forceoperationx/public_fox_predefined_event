#	MEMBER_REGIST（会員登録イベント）実装方法

　MEMBER_REGIST（会員登録イベント）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例

```objective-c
[ForceAnalyticsManager sendEvent:@"_member_regist"
                                action: nil
                                label: nil
                                value: 0
                                eventInfo:@{
                                  @"registration_method":@"XXXXX"
                                }
];
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

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventInfo (registration_method)|NSDictionary|Facebook,Twitter,EmailなどをJSONに設定する|

---
[戻る](/lang/ja/doc/fox_engagement/README.md)

