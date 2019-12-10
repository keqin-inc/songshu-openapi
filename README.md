# 松鼠数据平台互通 OpenAPI

松鼠数据平台用于第三方小说平台数据互通，用于公众号内的用户精准运维。小说平台的 API URL 前缀可自行决定，例如 `https://api.example.com/v1/`，剩余部分请尽量按指定格式提供。

### 需要实现以下接口

{% page-ref page="query-users.md" %}

{% page-ref page="query-orders.md" %}

{% page-ref page="query-links.md" %}



### 需要接入以下接口

{% page-ref page="notify-order.md" %}

{% page-ref page="notify-order.md" %}

### 更新变动历史

| 日期 | 更新项目 |
| :--- | :--- |
| 2019-12-11 | 添加[推广链接查询](query-links.md)接口 |
| 2019-12-10 | 第一版 |

