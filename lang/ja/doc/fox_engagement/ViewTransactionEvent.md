# Track Transaction（商品購入イベント）実装方法

Track Transaction（商品購入）イベントが発生する箇所に、下記に従ってアクセス解析のイベント計測機能を実装ください。

### 実装例

```java
JSONObject eventInfo = new JSONObject("{" +
                                      "'transaction_id':'ABCDFE'," +
                                      "'product':[" +
                                                "{'id':'1234','price':550,'quantity':1}," +
                                                "{'id':'1235','price':550,'quantity':2}," +
                                                "{'id':'1236','price':550,'quantity':2}" +
                                                "]," +
                                      "'din':'2016-01-02'," +
                                      "'dout':'2016-01-05'," +
                                      "'origin':'XXXXX'," +
                                      "'destination':'XXXXX'," +
                                      "'criteo_partner_id':'XXXXX'" +
                                      "}");
AnalyticsManager.sendEvent(this, "_purchase", null, null, null, null, null, 2750, 1, "JPY", eventInfo);
```

### 引数詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|context|Context|呼び出し元のActivityのContext|
|eventName|String|任意の名前を指定してください。特に指定がない場は、"_purchase" を指定してください。|
|<span style="color:grey">action|<span style="color:grey">String|<span style="color:grey">使用しません。|
|<span style="color:grey">label|<span style="color:grey">String|<span style="color:grey">使用しません。|
|orderID|String|（任意）注⽂番号等を指定します。|
|sku|String|（任意）商品コード等を指定します。|
|<span style="color:grey">itemName|<span style="color:grey">String|<span style="color:grey">使用しません。|
|price|double|商品総額を指定します。<br><span style="color:red">※必ず price * quantity の値が商品総額となるよう指定ください|
|quantity|int|1を指定してください。|
|currency|int|通貨コードを指定します。<br>nullの場合は”JPY”が指定されます。|
|eventInfo|JSONObject|イベント情報詳細 (以下参照)|

#### イベント情報詳細

| 引数 | 型 | 概要 |
|:----------|:-----------:|:------------|
|eventInfo (transaction_id)|JSONObject|注文番号、問い合わせ番号などのトランザクションID|
|eventInfo (product)|JSONArray|Product をキーとして商品IDを配列で設定します。
|&nbsp;&nbsp;eventInfo (product[].id)|JSONObject|商品IDデータフィードと同じ商品IDを使用してください。|
|&nbsp;&nbsp;eventInfo (product[].price)|JSONObject|該当商品の価格を設定します。|
|&nbsp;&nbsp;eventInfo (product[].quantity)|JSONObject|該当商品を買った個数を設定します。|
|eventInfo (din/dout)|JSONObject|⽇付の指定がある場合は⼊⼒してください。（任意）|
|eventInfo (origin/destination)|JSONObject|出発地点／行先の指定がある場合は入力（旅行アプリなど）</br>（任意）|
|eventInfo (criteo_partner_id)|JSONObject|Criteo アカウントID が同⼀アプリで異なる場合は⼊⼒(任意)<br>以下、このアクションによってデータフィードが変動する場合に設定します。|


> ※ 商品購⼊イベントの price に⼊⼒する⾦額は必ず、Json データに指定した商品の総額 (price * quantity)となるよう指定してください。指定されていない場合、集計が正しく⾏われません。


---
[戻る](/lang/ja//doc/fox_engagement/README.md)

[トップ](/lang/ja/README.md)
