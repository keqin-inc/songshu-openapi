# 用户查询

根据用户的 openid，批量查询信息

{% hint style="success" %}
**您需要实现此接口**
{% endhint %}

{% api-method method="get" host="" path="/:appid/users?openid=:openid,:openid&time=:time" %}
{% api-method-summary %}
 Query Users
{% endapi-method-summary %}

{% api-method-description %}
示例  
https://api.example.com/v1/wx570bc396a51b8ff8/users?openid=oP7TW1X--NjWFwpApzzsS75vVHuI,oP7TW1Q2eC0T-p3TI5j5cQakwbcs&time=1575883879
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
用户的 OpenId，多个用户时，使用半角逗号分隔
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
JSON 格式的用户数组，每个用户为一项。
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

{% hint style="danger" %}
如果 openid 不存在，不需要返回该用户信息。
{% endhint %}

### 字段含义

| 字段 | 含义 | 类型 | 示例值 |
| ---: | :--- | :--- | :--- |
| **openid** | 用户 OpenId | string | "oP7TW1X--NjWFwpApzzsS75vVHuI" |
| **balance** | 书币余额 | 浮点 | 21.00 |
| **ticket** | 书券余额 | 浮点 | 400 |
| **charged** | 充值过的总金额 | 浮点 | 400 |
| **reg\_time** | 注册时间 | string | "2019-08-01 12:43:23" |
| **last\_read\_book** | 最后阅读记录书名 | string | "都市极品医神" |
| **last\_read\_time** | 最后阅读时间 | string | "2019-11-01 12:43:23" |

#### 注：

1. 时间的格式为 `Y-m-d H:i:s`
2. 金额一般都是整型，无需刻意转换成浮点





