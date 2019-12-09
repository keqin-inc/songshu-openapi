# 用户查询

{% api-method method="get" host="" path="/:appid/users?openid=:openid,:openid&time=:time" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
 用户查询接口
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="appid" type="string" required=true %}
 公众号的微信开发者 AppId
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="time" type="integer" required=true %}
当前的 Unix 时间戳
{% endapi-method-parameter %}

{% api-method-parameter name="openid" type="string" required=true %}
用户的 OpenId
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
  {
    "openid": "oP7TW1X--NjWFwpApzzsS75vVHuI",
    "balance": 1.23, // 书币余额
    "ticket": 23, // 书券余额
    "charged": 2300, // 充值过的总金额
    "reg_time": "2019-08-01 12:43:23", //注册时间
    "last_read_book": "都市极品医神",
    "last_read_time": "2019-11-01 12:43:23"
}, 
{
    "openid": "oP7TW1Q2eC0T-p3TI5j5cQakwbcs",
    "balance": 32,
    "ticket": 23,
    "charged": 2300,
    "reg_time": "2019-08-01 12:43:23",
    "last_read_book": "都市极品医神",
    "last_read_time": "2019-11-01 12:43:23"
 }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
test
{% endhint %}

