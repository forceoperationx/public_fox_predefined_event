# Tutorial Comp（チュートリアル突破イベント）実装方法

　Tutorial Comp（チュートリアル突破）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例

```java
JSONObject eventInfo = new JSONObject("{" +
                                 "'product':[{'id': 'XXXXX'}]" +
                                 "}");
AnalyticsManager.sendEvent(this, "_tutorial_comp", null, null, 0, eventInfo);
```

### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|context|Context|呼び出し元のActivityのContext|
|eventName|String|"\_tutorial\_comp" を指定してください。|
|<span style="color:grey">action|<span style="color:grey">String|<span style="color:grey">使用しません。|
|<span style="color:grey">label|<span style="color:grey">String|<span style="color:grey">使用しません。|
|<span style="color:grey">value|<span style="color:grey">int|<span style="color:grey">使用しません。|
|eventInfo|JSONObject|イベント情報詳細 (以下参照)|

#### イベント情報詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventInfo (product)|JSONArray|Product をキーとして商品IDを配列で設定します。|
|&nbsp;&nbsp;eventInfo (product[].id)|JSONObject|閲覧した商品IDを設定します。|
　　

---
[戻る](/lang/ja//doc/fox_engagement/README.md)

[トップ](/lang/ja/README.md)