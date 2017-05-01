#	Update User Info（ユーザーデータ更新）実装方法

　Update User Info（ユーザーデータ更新）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例

```objective-c
NSDictionary *ext = @{@"XXXXX":@"XXXXX", @"XXX":@XXX};
NSDictionary *userInfo = @{@"guid":@"XXXXX", @"ext":ext};
[ForceAnalyticsManager setUserInfo:userInfo];

[ForceAnalyticsManager sendEvent:@"_update_userinfo"
                                action:nil
                                label:nil
                                value:0
                                eventInfo:nil
];
```

### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventName|NSString|"\_update\_userinfo" を指定してください。|
|<span style="color:grey">action|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">label|<span style="color:grey">NSString|<span style="color:grey">使用しません。|
|<span style="color:grey">value|<span style="color:grey">NSUInteger|<span style="color:grey">使用しません。|
|eventInfo|NSDictionary|使用しません|
|UserInfo|NSDictionary|イベント情報詳細 (以下参照)|

#### イベント情報詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventInfo (guid)|NSString|ゲームユーザID（任意）|
|eventInfo (ext)|NSDictionary|ユーザーデータ、事前にDyanlyst社と相談の上パラメータを決めてください。|

---
[戻る](/lang/ja/doc/fox_engagement/README.md)
