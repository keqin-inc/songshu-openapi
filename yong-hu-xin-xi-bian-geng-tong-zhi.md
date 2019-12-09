# 用户信息变更通知

当用户以下信息在当天发生变化时，次日凌晨需要把此类用户推送至此接口，**推送的内容和用户查询返回的结构完全一致。**

1. 用户的书币
2. 用户的书券
3. 用户最后阅读时间
4. 用户最后阅读的图书名称

{% hint style="success" %}
您需要定时主动调用此接口，建议至少保证每日一次。
{% endhint %}

{% api-method method="post" host="https://" path="mp-notify-api.sdpku.com/v1/:appid/user" %}
{% api-method-summary %}
用户信息变更批量推送接口
{% endapi-method-summary %}

{% api-method-description %}
示例 https://mp-notify-api.sdpku.com/v1/wx570bc396a51b8ff8/user
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="appid" type="string" required=true %}
公众号AppId
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="test" type="boolean" required=false %}
是否测试订单，1或0，默认情况下不要添加此参数
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "errcode": 0
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

推送正文为 JSON 数组结构，数组的每一项为一个用户，建议单次用户数量控制在 1000 以内，分多次发送

```text
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

{% hint style="info" %}
释义参考[《用户查询》](query-users.md)一节，含义一致。
{% endhint %}

