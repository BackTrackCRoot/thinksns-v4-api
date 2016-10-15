# ThinkSNS v4 开源版 API 收集

## 账户验证与注册

### 登录验证

**请求地址** `http://<ThinkSNS站点域名>/index.php?app=public&mod=Passport&act=doLogin`

**请求参数列表**

请求类型 | 参数名 | 参数值
-------- | ------ | -------
HTTP 请求头 | Cookie | TS4_TSV4_ACTIVE_TIME=<10位Unix时间轴>;
HTTP 请求头 | Referer | http://<ThinkSNS站点域名>/index.php
POST 数据 | login_email | 用户 E-Mail
POST 数据 | login_password | 用户密码
POST 数据 | login_remember | 记住用户名 ( 0 / 1 )

**注意** 其中 ```TS4_TSV4_ACTIVE_TIME``` 的值必须大于当前时间，不得小于当前时间！

**cURL请求示范**

```bash
curl "http://demo.acgdraw.com/index.php?app=public&mod=Passport&act=doLogin" -H "Cookie: TS4_TSV4_ACTIVE_TIME=1476527241;" -H "Referer: http://demo.acgdraw.com/" --data "login_email=test"%"40example.com&login_password=12345678&login_remember=1" --compressed
```

**请求成功返回**

```json
{
    "status": 1,
    "info": "登录成功，努力加载中。。",
    "data": "http://demo.acgdraw.com/index.php?app=public&mod=Index&act=index"
}
```

**请求失败返回**

```json
{
    "status": 0,
    "info": "帐号不存在",
    "data": 0
}
```
