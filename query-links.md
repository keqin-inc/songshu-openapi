# 推广链接查询

批量查询推广链接及其统计数据。需求场景：用于定时更新链接的统计数据。

{% hint style="success" %}
您**需要实现此接口**
{% endhint %}

{% api-method method="get" host="/" path=":appid/links?page=:page&link\_id=:link\_id1,:link\_id2&begin=:begin&end=:end&time=:time" %}
{% api-method-summary %}
Query Links
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="appid" type="string" required=true %}
公众号的AppId
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="page" type="integer" required=false %}
当前页码，默认为1
{% endapi-method-parameter %}

{% api-method-parameter name="link\_id" type="string" required=false %}
指定查询的链接ID，半角逗号分隔。省略时不指定LinkID
{% endapi-method-parameter %}

{% api-method-parameter name="begin" type="string" required=false %}
链接创建开始时间，格式 Y-m-d H:i:s。省略时为全部
{% endapi-method-parameter %}

{% api-method-parameter name="end" type="string" required=false %}
链接创建的结束时间
{% endapi-method-parameter %}

{% api-method-parameter name="time" type="string" required=true %}
当前的 unix 时间戳
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    "page": 1,
    "total": 21,
    "page_size": 100,
    "links": [{
        "link_id": "112845",
        "url": "https:\/\/100336.jiangdia.com\/channel\/read\/1\/98582\/32037240\/112845\/0",
        "title": "12.11客服中",
        "create_time": "2019-12-11 01:09:15",
        "book": "拥抱太阳的月亮",
        "begin_section": "第1章",
        "end_section": "第9章",
        "is_subscribe_required": 1,
        "pv": 170,
        "uv": 141,
        "increased_user": 5,
        "charged_price": 434,
        "charged_count": 21,
        "remark": "",
        "is_deleted": 0
    }]
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
一般只指定 link\_id 或 begin/end。创建时间范围用于更新当日创建的链接，link\_id 用于批量更新指定的链接统计数据。
{% endhint %}

* **page** 当前页数
* **total** 当前条件下的链接总数
* **page\_size** 每页链接数
* **links** 推广链接列表数组

响应的 Link 数据结构

<table>
  <thead>
    <tr>
      <th style="text-align:right">&#x5B57;&#x6BB5;</th>
      <th style="text-align:left">&#x542B;&#x4E49;</th>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x793A;&#x4F8B;&#x503C;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:right"><b>link_id</b>
      </td>
      <td style="text-align:left">&#x5728;&#x8D35;&#x5E73;&#x53F0;&#x5185;&#x7684;&#x94FE;&#x63A5;ID(&#x6709;&#x7684;&#x5E73;&#x53F0;&#x4EA6;&#x79F0;&#x6E20;&#x9053;ID)</td>
      <td
      style="text-align:left">string</td>
        <td style="text-align:left">&quot;112845&quot;</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>url</b>
      </td>
      <td style="text-align:left">&#x63A8;&#x5E7F;URL</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p>&quot;https:\/\/100336.jiangdia.com\/channel\</p>
        <p>/read\/1\/98582\/32037240\/112845\/0&quot;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:right"><b>title</b>
      </td>
      <td style="text-align:left">&#x6807;&#x9898;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&quot;12.11&#x5BA2;&#x670D;&#x4E2D;&quot;</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>create_time</b>
      </td>
      <td style="text-align:left">&#x521B;&#x5EFA;&#x65F6;&#x95F4;</td>
      <td style="text-align:left">srting</td>
      <td style="text-align:left">&quot;2019-12-11 01:09:15&quot;</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>book</b>
      </td>
      <td style="text-align:left">&#x4E66;&#x540D;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&quot;&#x62E5;&#x62B1;&#x592A;&#x9633;&#x7684;&#x6708;&#x4EAE;&quot;</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>begin_section</b>
      </td>
      <td style="text-align:left">&#x8D77;&#x59CB;&#x7AE0;&#x8282;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&quot;&#x7B2C;1&#x7AE0;&quot;</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>end_section</b>
      </td>
      <td style="text-align:left">&#x5F3A;&#x5236;&#x5173;&#x6CE8;&#x7AE0;&#x8282;&#xFF0C;&#x5982;&#x679C;&#x4E0D;&#x9700;&#x8981;&#x5F3A;&#x5236;&#x5173;&#x6CE8;&#x5219;&#x7559;&#x7A7A;</td>
      <td
      style="text-align:left">string</td>
        <td style="text-align:left">&quot;&#x7B2C;9&#x7AE0;&quot;</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>is_subscribe_required</b>
      </td>
      <td style="text-align:left">&#x662F;&#x5426;&#x5F3A;&#x5236;&#x5173;&#x6CE8;&#xFF0C;0 &#x4E3A;&#x5426;&#xFF0C;1&#x4E3A;&#x662F;</td>
      <td
      style="text-align:left">int</td>
        <td style="text-align:left">1</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>pv</b>
      </td>
      <td style="text-align:left">&#x94FE;&#x63A5;&#x70B9;&#x51FB;&#x6570;</td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">170</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>uv</b>
      </td>
      <td style="text-align:left">&#x70B9;&#x51FB;&#x7684;&#x4EBA;&#x6570;&#xFF0C;&#x4EA6;&#x79F0;&#x5F15;&#x5BFC;&#x4EBA;&#x6570;</td>
      <td
      style="text-align:left">int</td>
        <td style="text-align:left">141</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>increased_user</b>
      </td>
      <td style="text-align:left">&#x65B0;&#x589E;&#x5173;&#x6CE8;&#x6570;</td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">5</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>charged_price</b>
      </td>
      <td style="text-align:left">&#x94FE;&#x63A5;&#x5E26;&#x6765;&#x7684;<b>&#x5145;&#x503C;&#x603B;&#x91D1;&#x989D;</b>
      </td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">434.00</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>charged_count</b>
      </td>
      <td style="text-align:left">&#x5145;&#x503C;&#x6B21;&#x6570;</td>
      <td style="text-align:left">int</td>
      <td style="text-align:left">21</td>
    </tr>
    <tr>
      <td style="text-align:right"><b>remark</b>
      </td>
      <td style="text-align:left">&#x5907;&#x6CE8;&#xFF0C;&#x65E0;&#x65F6;&#x7559;&#x7A7A;</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:right"><b>is_deleted</b>
      </td>
      <td style="text-align:left">&#x662F;&#x5426;&#x5DF2;&#x5220;&#x9664;&#xFF0C;&#x5373;&#x662F;&#x5426;&#x5DF2;&#x7ECF;&#x8FDB;&#x5165;&#x267B;&#xFE0F;&#x56DE;&#x6536;&#x7AD9;&#x3002;</td>
      <td
      style="text-align:left">int</td>
        <td style="text-align:left">0</td>
    </tr>
  </tbody>
</table>{% hint style="danger" %}
请确保 link\_id 在单个公众号范围内是唯一的。
{% endhint %}

