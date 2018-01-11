## 用户(user)

+ [响应状态码](#响应状态码表)
+ 方法列表
	+ [登录](#登录)
	+ [登出(TODO)](#TODO登出)
	+ [静默注册](#静默注册)
	+ [详情](#详情)


### 响应状态码表

|  code  |       说明       |
| ------ | ---------------- |
| 333001 | 用户不存在       |
| 333002 | 用户校验失败     |
| 333003 | 图片验证码错误   |
| 333004 | 手机号格式错误   |
| 333005 | 忘记设置性别啦～ |
| 333006 | 注册失败         |
| 333007 | token添加失败    |
| 333008 | 手机验证码错误   |
| 333009 | 防打扰时间非法   |
| 333010 | 设置失败         |



### 登录

uri: app1/user/login

params:

|   变量   |  名称  | 必填 |  类型  | 描述 |
| -------- | ------ | ---- | ------ | ---- |
| username | 用户名 | 是   | string |      |
| key      | 密码   | 是   | string |      |

请求示例：

1.正式环境: 待定

2.测试环境:
http://47.52.101.29/app1/user/login?username=liu&key=123

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxfQ.-QqHe1NOuVz8hpMDRm5CZfWT6SWh1R38mwNkjCOj34o",
        "user": {
            "id": 1,
            "name": "刘先森",
            "signture": "302af1b2e2a1d120ae91197b4eb23cc4",
            "status": 0,
            "sex": 0,
            "avatar": "/static/images/user/cd678b5f206c51658d7d5dffd82e6980.png",
            "phone": 18888888888,
            "ctime": 0,
            "utime": 0
        },
        "user_setting": {
            "id": 1,
            "user_id": 1,
            "notify_free_begin": "22:00",
            "notify_free_end": "08:00"
        }
    }
}
```

response 说明：

|                 字段                |   名称   |                  说明                  |
| ----------------------------------- | -------- | -------------------------------------- |
| code                                | 状态码   | 0:正常,333002:token校验失败            |
| msg                                 | 消息     | 请求正常为"ok",否则为详细错误信息      |
| data.token                          | token    | 该用户的token，线上接口无该条目        |
| data.user.id                        | 用户ID   |                                        |
| data.user.openid                    | OPENID   | 测试属性，后期移除                     |
| data.user.name                      | 用户名   |                                        |
| data.user.ctime                     | 创建时间 | 创建时间，unixtimestamp，bigint(13)    |
| data.user.utime                     | 更新时间 | 更新时间，unixtimestamp，bigint(13)    |
| data.user.signture                  | 令牌     |                                        |
| data.user.status                    | 账号状态 | 0:正常                                 |
| data.user_setting.id                |          |                                        |
| data.user_setting.user_id           |          |                                        |
| data.user_setting.notify_free_begin | 账号状态 | 免打扰开始时间，24小时制  格式： hh:mm |
| data.user_setting.notify_free_end   | 账号状态 | 免打扰结束时间，24小时制  格式：hh:mm  |



### TODO：登出

uri: app1/user/logout

params: 空

请求示例：http://47.52.101.29/app1/user/logout

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": []
}
```

response 说明：

| 字段 |  名称  |                说明               |
|------|--------|-----------------------------------|
| code | 状态码 | 0:正常                            |
| msg  | 消息   | 请求正常为"ok",否则为详细错误信息 |

### 详情

uri: app1/user/profile

params: 无


请求示例：http://47.52.101.29/app1/user/profile

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "id": 1,
        "openid": "openid1",
        "name": "刘先森",
        "ctime": 0,
        "utime": 0,
        "signture": "cd678b5f206c51658d7d5dffd82e6980",
        "status": 0,
        "sex": 0,
        "avatar": "/static/images/user/cd678b5f206c51658d7d5dffd82e6980.png"
    }
}
```

response 说明:

|      字段     |   名称   |                 说明                |
|---------------|----------|-------------------------------------|
| code          | 状态码   | 0:正常                              |
| msg           | 消息     | 请求正常为"ok",否则为详细的错误信息 |
| data.id       | ID       |                                     |
| data.name     | 昵称     |                                     |
| data.ctime    | 创建时间 | 类型为unixtimestamp                 |
| data.utime    | 更新时间 | 类型为unixtimestamp                 |
| data.signture | 签名     |                                     |
| data.status   | 状态     | 0:正常                              |
| data.sex      | 性别     | 0:外星人,1:男,2:女                  |
| data.avatar   | 头像     |                                     |


### 静默注册

uri: app1/user/ssign_up

params: 无


请求示例：http://47.52.101.29/app1/user/ssign_up

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "token": "52b29deb878f15e1a22be9e0c5cfee80",
        "user": {
            "phone": 0,
            "name": "x_079407",
            "ctime": 1514272407,
            "utime": 1514272407,
            "sex": 0,
            "status": 0,
            "signture": "52b29deb878f15e1a22be9e0c5cfee80",
            "id": 8
        }
    }
}
```

response 说明:

|        字段        |   名称   |                 说明                |
|--------------------|----------|-------------------------------------|
| code               | 状态码   | 0:正常                              |
| msg                | 消息     | 请求正常为"ok",否则为详细的错误信息 |
| data.token         | token    | 该用户的token，线上接口无该条目     |
| data.user.id       | ID       |                                     |
| data.user.name     | 昵称     |                                     |
| data.user.ctime    | 创建时间 | 类型为unixtimestamp                 |
| data.user.utime    | 更新时间 | 类型为unixtimestamp                 |
| data.user.signture | 签名     | 方便测试，临时token==signture       |
| data.user.status   | 状态     | 0:正常                              |
| data.user.sex      | 性别     | 0:外星人,1:男,2:女                  |
| data.user.avatar   | 头像     |                                     |
