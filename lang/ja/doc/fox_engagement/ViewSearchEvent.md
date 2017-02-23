#	View Home(アプリトップ訪問イベント)実装方法
　View Home（ホーム画面）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例

```java
JSONObject eventInfo = new JSONObject("{" +
                                 "'din':'2016-01-02'," +
                                 "'dout':'2016-01-05'," +
                                 "'search_term':'XXXXX'" +
                                 "'origin':'XXXXX'," +
                                 "'destination':'XXXXX'," +
                                 "'criteo_partner_id':'XXXXX'" +
                                 "'product':[" +
                                        "{'id': '111'," +
                                        "'item_location_id':'XXXXX'}," +
                                        "{'id': '112'," +
                                         "'item_location_id':'XXXXX'}," +
                                        "{'id': '113'," +
                                         "'item_location_id':'XXXXX'}" +
                                 	"]," +
                                "}");
AnalyticsManager.sendEvent(this, "_search", null, null, 0, eventInfo);
```

### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|context|Context|呼び出し元のActivityのContext|
|eventName|String|“\_search”を指定してください。|
|<span style="color:grey">action|<span style="color:grey">String|<span style="color:grey">使用しません。|
|<span style="color:grey">label|<span style="color:grey">String|<span style="color:grey">使用しません。|
|<span style="color:grey">value|<span style="color:grey">int|<span style="color:grey">使用しません。|
|eventInfo|JSONObject|イベント情報詳細 (以下参照)|


#### イベント情報詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventInfo (product)|JSONArray|Product をキーとして商品IDを配列で設定します。
|&nbsp;&nbsp;eventInfo (product[].id)|JSONObject|商品IDを設定します。<br>データフィードと同じ商品IDを使⽤してください。|
|&nbsp;&nbsp;eventInfo (product[].item_location_id)|JSONObject|商品の広告を特定の場所や地域に訴求したい場合指定（任意）|
|eventInfo (search_term)|JSONObject|検索キーワードを入力|
|eventInfo (din/dout)|JSONObject|日付の指定がある場合は入力（任意）|
|eventInfo (origin/destination)|JSONObject|出発地点／行先の指定がある場合は入力（旅行アプリなど）</br>（任意）|
|eventInfo (criteo_partner_id)|JSONObject|CriteoアカウントIDが同一アプリで異なる場合は入力(任意)|

---
[戻る](/lang/ja//doc/fox_engagement/README.md)

[トップ](/lang/ja/README.md)
