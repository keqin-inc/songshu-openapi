# 订单查询

根据时间范围等信息，查询订单

{% hint style="success" %}
您需要实现此接口
{% endhint %}

{% api-method method="get" host="" path="/:appid/orders?page=:page&begin=:begin&end=:end&time=:time" %}
{% api-method-summary %}
查询订单
{% endapi-method-summary %}

{% api-method-description %}
例如：https://api.example.com/v1/wx570bc396a51b8ff8/orders?page=1&begin=2019-12-01%2000%3A00%3A00&2019-12-01%2023%3A59%3A59&time=1575883879
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="appid" type="string" required=true %}
公众号的开发者AppId
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="openid" type="string" required=false %}
指定用户的 openid，留空时查询所有用户订单。
{% endapi-method-parameter %}

{% api-method-parameter name="pay\_status" type="integer" required=false %}
-1/0/1，-1 为全部（默认值）；0 待支付；1 已支付
{% endapi-method-parameter %}

{% api-method-parameter name="begin" type="string" required=true %}
订单创建时间，开始范围
{% endapi-method-parameter %}

{% api-method-parameter name="end" type="string" required=true %}
订单创建时间，格式为 Y-m-d H:i:s
{% endapi-method-parameter %}

{% api-method-parameter name="time" type="integer" required=true %}
当前的 Unix 时间戳
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="integer" required=false %}
当前的页数
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "page": 1,
    "total": 10490,
    "page_size": 100,
    "orders": [
        {
            "amount": 80.00,
            "order_id":"4200000429201912071609677638",
            "create_time": "2019-12-07 23:59:41",
            "pay_time": "2019-12-07 23:59:46",
            "pay_status": 1,
            "openid":"oBHx1s775pANd1HWQ-aS-ou49kNA",
            "book":"他与星辰皆璀璨"
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

* page 当前页数
* total 当前条件下的订单总数
* page\_size 每页订单数
* orders 订单列表数组

orders 字段结构

| 字段 | 含义 | 类型 | 示例值 |
| :--- | :--- | :--- | :--- |
| order\_id | 平台唯一订单号 | string | "4200000429201912071609677638" |
| amount | 订单金额 | float | 80.00 |
| create\_time | 订单创建时间 | string | "2019-12-07 23:59:41" |
| pay\_time | 订单支付时间 | string | "2019-12-07 23:59:46" |
| pay\_status | 支付状态，0：未支付，1：已支付 | int | 1 |
| openid | 用户的OpenId | string | "oBHx1s775pANd1HWQ-aS-ou49kNA" |
| book | 订单关联的图书，无时留空 | string | "他与星辰皆璀璨" |

{% hint style="danger" %}
一部分平台以支付成功时才有订单号，这种情况下的未支付订单的订单号可留空。
{% endhint %}

