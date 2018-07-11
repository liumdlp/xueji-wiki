## 用户(user)

+ [响应状态码](#响应状态码表)
+ 方法列表
	+ [登录](#登录)
	+ [登出(TODO)](#todo登出)
	+ [注册](#注册)
	+ [详情](#详情)
    + [设置](#设置)
    + [获取短信验证码](#获取短信验证码)
    + [编辑详情](#编辑详情)
    + [重置密码](#重置密码)


### 响应状态码表

|  code  |                 说明                 |
| ------ | ------------------------------------ |
| 333001 | 用户不存在                           |
| 333002 | 用户校验失败                         |
| 333003 | 图片验证码错误                       |
| 333004 | 手机号格式错误                       |
| 333006 | 注册失败                             |
| 333007 | token添加失败                        |
| 333008 | 手机验证码错误                       |
| 333009 | 防打扰时间非法                       |
| 333010 | 设置失败                             |
| 333011 | 短信发送失败                         |
| 333012 | 编辑详情失败                         |
| 333013 | 手机号已经注册，如忘记密码可重置密码 |
| 333014 | 重置密码失败                         |


### 登录

uri: app1/user/login

params:

|   变量   |    名称    | 必填 |  类型  |            描述           |
| -------- | ---------- | ---- | ------ | ------------------------- |
| phone    | 手机号     | 是   | string |                           |
| key      | 密码       | 是   | string |                           |
| platform | 平台       | 是   | string | IOS  ANDROID OTHER etc... |
| version  | 版本       | 是   | string | 0.1.0                     |
| uuid     | 设备标识ID | 是   | string |                           |


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
            "status": 0,
            "sex": 0,
            "avatar": "http://47.52.101.29/static/avatar_def.jpeg",
            "phone": 18640933943,
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

|                 字段                |      名称      |                 说明                |
| ----------------------------------- | -------------- | ----------------------------------- |
| code                                | 状态码         | 0:正常,333002:token校验失败         |
| msg                                 | 消息           | 请求正常为"ok",否则为详细错误信息   |
| data.token                          | token          | 该用户的token，线上接口无该条目     |
| data.user.id                        | 用户ID         |                                     |
| data.user.name                      | 用户名(昵称)   |                                     |
| data.user.status                    | 账号状态       | 0:正常                              |
| data.user.avatar                    | 头像地址       |                                     |
| data.user.sex                       | 性别           | 0:外星人,1:男,2:女                  |
| data.user.phone                     | 手机号         |                                     |
| data.user.utime                     | 更新时间       | 更新时间，unixtimestamp，bigint(13) |
| data.user_setting.id                |                |                                     |
| data.user_setting.user_id           |                |                                     |
| data.user_setting.notify_free_begin | 免打扰开始时间 | 24小时制  格式： hh:mm              |
| data.user_setting.notify_free_end   | 免打扰结束时间 | 24小时制  格式：hh:mm               |

#### 接口权限控制：
***登陆后所有接口均需要token,platform,version,uuid四个参数同时存在***



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


### 注册

uri: app1/user/sign_up

params:


|   变量   |    名称    | 必填 |  类型  |           描述           |
| -------- | ---------- | ---- | ------ | ------------------------ |
| phone    | 手机号     | 是   | string |                          |
| sms_code | 短信验证码 | 是   | string | 4个数字                  |
| name     | 用户昵称   | 否   | string |                          |
| sex      | 性别       | 否   | int    | 0(默认):外星人,1:男,2:女 |
| key      | 密码       | 是   | string |                          |


response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "phone": 18510542239,
        "name": "学神_002887",
        "ctime": 1531302887,
        "utime": 1531302887,
        "avatar": "http://47.52.101.29/static/avatar_def.jpeg",
        "sex": 0,
        "id": 12
    }
}
```

response 说明:

|       字段       |   名称   |                 说明                |
| ---------------- | -------- | ----------------------------------- |
| code             | 状态码   | 0:正常                              |
| msg              | 消息     | 请求正常为"ok",否则为详细的错误信息 |
| data.phone       | 手机号   | 手机号                              |
| data.id          | ID       |                                     |
| data.name        | 昵称     |                                     |
| data.ctime       | 创建时间 | 类型为unixtimestamp                 |
| data.utime       | 更新时间 | 类型为unixtimestamp                 |
| data.sex         | 性别     | 0:外星人,1:男,2:女                  |
| data.user.avatar | 头像     |                                     |


### 设置

uri: app1/user/setting

params:

|  变量 |   名称   | 必填 |  类型  |         描述        |
| ----- | -------- | ---- | ------ | ------------------- |
| nfbeg | 开始时间 | 是   | string | 防打扰开始时间23:00 |
| nfend | 结束时间 | 是   | string | 防打扰结束时间08:00 |

请求示例：http://47.52.101.29/app1/user/setting?nfbeg=23%3a00&nfend=07%3a00

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": []
}
```

response 说明:

| 字段 |  名称  |                 说明                |
| ---- | ------ | ----------------------------------- |
| code | 状态码 | 0:正常                              |
| msg  | 消息   | 请求正常为"ok",否则为详细的错误信息 |



### 获取短信验证码

uri: app1/user/get_sms_code

params:

|  变量 |   名称   | 必填 |  类型  |         描述        |
| ----- | -------- | ---- | ------ | ------------------- |
| phone | 手机号码 | 是   | string |                     |

请求示例：http://47.52.101.29/app1/user/get_sms_code

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": []
}
```

response 说明:

| 字段 |  名称  |                 说明                |
| ---- | ------ | ----------------------------------- |
| code | 状态码 | 0:正常                              |
| msg  | 消息   | 请求正常为"ok",否则为详细的错误信息 |




### 编辑详情

uri: app1/user/modify_profile

params:

|  变量  | 名称 | 必填 |  类型  |                   描述                  |
| ------ | ---- | ---- | ------ | --------------------------------------- |
| name   | 昵称 | 否   | string |                                         |
| sex    | 性别 | 否   | int    | 0:外星人 1:男 2:女                      |
| avatar | 头像 | 否   | string | 先调用传图接口上传新头像，返回的URL地址 |


response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {}
}
```

response 说明:

|      字段     |   名称   |                 说明                |
|---------------|----------|-------------------------------------|
| code          | 状态码   | 0:正常                              |
| msg           | 消息     | 请求正常为"ok",否则为详细的错误信息 |

### 重置密码

uri: app1/user/reset_password

params:

|   变量   |    名称    | 必填 |  类型  |   描述  |
| -------- | ---------- | ---- | ------ | ------- |
| phone    | 手机号     | 是   | string |         |
| sms_code | 短信验证码 | 是   | string | 4个数字 |
| key      | 密码       | 是   | string |         |


response:

response 说明:

|       字段       |   名称   |                 说明                |
| ---------------- | -------- | ----------------------------------- |
| code             | 状态码   | 0:正常                              |
| msg              | 消息     | 请求正常为"ok",否则为详细的错误信息 |