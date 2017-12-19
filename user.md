## 用户(user)

### TODO：登录

uri: app1/user/login

params:

| 变量    | 名称   | 必填   | 类型     | 描述   |
| ----- | ---- | ---- | ------ | ---- |
| id    | 用户id | 是    | int    | 默认：1 |
| token | 口令   | 是    | string |      |

请求示例：http://47.52.101.29/app1/user/login?id=1&token=sssssssssssss

response:

```json
{
    "code": 0,
    "msg": "[uid = 1]登录成功",
    "data": [
        {
            "user": {
                "id": 1,
                "openid": "openid1",
                "name": "刘先森",
                "ctime": 0,
                "utime": 0,
                "signture": "cd678b5f206c51658d7d5dffd82e6980",
                "status": 0
            }
        }
    ]
}
```

response 说明：

| 字段                 | 名称     | 说明                                  |
| ------------------ | ------ | ----------------------------------- |
| code               | 状态码    | 0:正常,333002:token校验失败。未上线前非必填，空着也可以 |
| msg                | 消息     | 请求正常为"ok",否则为详细错误信息                 |
| data.user.id       | 用户ID   |                                     |
| data.user.openid   | OPENID | 测试属性，后期移除                           |
| data.user.name     | 用户名    |                                     |
| data.user.ctime    | 创建时间   | 创建时间，unix timestamp，bigint(13)      |
| data.user.utime    | 更新时间   | 更新时间，unix timestamp，bigint(13)      |
| data.user.signture | 令牌     |                                     |
| data.status        | 账号状态   | 0:正常                                |



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

| 字段   | 名称   | 说明                  |
| ---- | ---- | ------------------- |
| code | 状态码  | 0:正常                |
| msg  | 消息   | 请求正常为"ok",否则为详细错误信息 |




