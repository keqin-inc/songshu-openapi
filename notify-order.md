# 订单创建/支付通知

{% hint style="success" %}
您需要在出现新订单、订单完成支付时主动调用此接口，建议近实时调用。
{% endhint %}

{% api-method method="post" host="https://" path="mp-notify-api.sdpku.com/v1/:appid/order/:orderId" %}
{% api-method-summary %}
订单创建/支付通知推送
{% endapi-method-summary %}

{% api-method-description %}
示例 https://mp-notify-api.sdpku.com/v1/wx570bc396a51b8ff8/order/4200000429201912071609677638
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="orderId" type="string" required=true %}
订单号
{% endapi-method-parameter %}

{% api-method-parameter name="appid" type="string" required=true %}
公众号AppId
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="test" type="boolean" required=false %}
是否测试订单，1或0，默认情况下不要添加此参数
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="book" type="string" required=false %}
订单关联的图书名称，例如 "他与星辰皆璀璨"
{% endapi-method-parameter %}

{% api-method-parameter name="openid" type="string" required=true %}
用户的Openid
{% endapi-method-parameter %}

{% api-method-parameter name="pay\_status" type="string" required=true %}
支付状态，1为已支付，0为未支付
{% endapi-method-parameter %}

{% api-method-parameter name="pay\_time" type="string" required=true %}
支付时间，格式 "2019-12-07 23:59:46"
{% endapi-method-parameter %}

{% api-method-parameter name="create\_time" type="string" required=true %}
订单创建时间，"2019-12-07 23:59:41"
{% endapi-method-parameter %}

{% api-method-parameter name="order\_id" type="string" required=false %}
不重复的订单号
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="number" required=true %}
订单金额，整型或者数字
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "errcode": 0
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### 推送正文示例

Post 请求 Body 正文为 json 格式字符串，例如

```javascript
{
    "amount": 80.00,
    "order_id":"4200000429201912071609677638",
    "create_time": "2019-12-07 23:59:41",
    "pay_time": "2019-12-07 23:59:46",
    "pay_status": 1,
    "openid": "oBHx1s775pANd1HWQ-aS-ou49kNA",
    "book": "他与星辰皆璀璨"
}
```

{% hint style="danger" %}
通知推送不需要完全实时，例如每五分钟推送一次亦可。
{% endhint %}

