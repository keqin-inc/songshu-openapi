# 签名校验

### Secret 

需要同步一份 32 位字符串作为 Secret。算法为 X-Hub-Signature，即：`hash_hmac("sha1", "数据", $secret);`Node.Js 可参考 [x-hub-signature](https://github.com/compwright/x-hub-signature) 库，Java 可参考 [xhub4j](https://github.com/McFoggy/xhub4j) 库

### 查询接口：查询参数中的 time 参数

我们会在请求接口时附带 time 参数，为当前服务器 Unix 时间戳。如果超过一定时间，接口需要返回错误信息。

### 查询接口：Header 中的签名

这不是标准的 X-Hub-Signature，签名的数据为 URL 中的路径、查询参数部分，即 PHP 中的 `$_SERVER['REQUEST_URI']` 变量，内容示例：`/v1/wx570bc396a51b8ff8/users?time=1575883879&openid=oP7TW1X--NjWFwpApzzsS75vVHuI,oP7TW1Q2eC0T-p3TI5j5cQakwbcs`

**为以下您需要实现的校验，代码供参考**

```php
<?php
function isLegalRequest($uri, $signature, $secret)
{
    return 'sha1='.hash_hmac('sha1', $uri, $secret) === $signature;
}

function isExpired($time)
{
    return ($time + 300) < time();
}

$secret = '394d5e7337578e17a7fc5e6bd5cfb2640950d054';
$uri = $_SERVER['REQUEST_URI'];
$signature = $_SERVER['HTTP_X_HUB_SIGNATURE'];
$time = filter_input(INPUT_GET, 'time');
if (isLegalRequest($uri, $signature, $secret)) {
    // 签名错误
}
if (isExpired($time)) {
    // 请求已过期
}

```

### 通知接口

由于是 POST 请求，签名方法遵循 X-Hub-Signature 签名法，即对 Post 的字符串 Body 进行签名，并把结果附加在 Http 请求的 Header 中，格式： `X-Hub-Signature: sha1=${sign}`

**推送数据的 PHP 示例**

```php
<?php
$secret = "394d5e7337578e17a7fc5e6bd5cfb2640950d054";
$appid = 'wx570bc396a51b8ff8';
$notifyUrl = "https://mp-notify-api.sdpku.com/v1/${appid}/users";

$body = json_encode([
    [
        "openid" => "oP7TW1X--NjWFwpApzzsS75vVHuI",
        "balance" => 1.23, // 书币余额
        "ticket" => 23.3, // 书券余额
        "charged" => 300.00, // 充值过的总金额
        "reg_time" => "2019-08-01 12:43:23", //注册时间
        "last_read_book" => "都市极品医神",
        "last_read_time" => "2019-11-01 12:43:23"
    ]
], JSON_UNESCAPED_UNICODE);

$algo = "sha1";
$signature = hash_hmac($algo, $body, $secret);
$ch = curl_init();
$headers = [
    'Content-Type: application/json',
    'Accept: application/json',
    "X-Hub-Signature: ${algo}=${signature}"
];
curl_setopt_array($ch, [
  CURLOPT_URL => $notifyUrl,
  CURLOPT_POST => true,
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => 'gzip,deflate',
  CURLOPT_HTTPHEADER => $headers,
  CURLOPT_POSTFIELDS => $body
]);

$content = curl_exec($ch);
var_dump(json_decode($content));
```



