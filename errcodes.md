# 参考错误代码

{% hint style="danger" %}
通知推送接口幂等，出现非 4 开头的错误代码时，建议延时后重试。
{% endhint %}

正确时直接返回结果数据结构。如果无结果，则返回 `{"errcode": 0}`

失败时返回如下结构的 json 数据：

* errcode 为 int 类型错误代码，失败时必须不等于 0
* msg 为错误的具体解释

```javascript
{
    "errcode": 401000,
    "msg": "签名错误"
}
```

错误代码示例

* 40100 签名错误
* 41000 时间戳过期 
* 40000 缺少参数







