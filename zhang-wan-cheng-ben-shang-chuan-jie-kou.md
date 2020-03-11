# 【掌玩】成本上传接口

批量上传公众号的广告消耗数据。

签名方式：[通知接口](signature.md#tong-zhi-jie-kou)

{% api-method method="post" host="https://mp-notify-api.sdpku.com" path="/v1/costs" %}
{% api-method-summary %}
Push Ad Costs
{% endapi-method-summary %}

{% api-method-description %}
上传指定公众号的广告消耗数据
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
成功
{% endapi-method-response-example-description %}

```javascript
{ errcode: 0 }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

往该地址 POST 一个数组，例如：公众号 wxb0589c805785c6ad 在 3月11日消耗 1290元，wx570bc396a51b8ff8 在 11日消耗 2430 元，需要传入以下格式的数组：

```javascript
[
    { appid: 'wxb0589c805785c6ad', date: '2020-03-11', cost: 129000},
    { appid: 'wx570bc396a51b8ff8', date: '2020-03-11', cost: 243000},
]
```

{% hint style="danger" %}
注意：数组项的上限数量为 3000
{% endhint %}

#### 响应数据：

成功时： { errcode: 0 }

失败时： { errcode: 1, msg: '错误提示信息' }

