## 用户(user)

### TODO：登录

uri: app1/user/login

params:

| 变量		| 名称		| 必填	| 类型	  	| 描述   		|
| --------- | ---------	| -----	| ---------	| -------------	|
| id    	| 用户id		| 否		| int		| 默认：1 ,指定要登录的用户id,测试环境可用|
| token 	| 口令  		| 是		| string	| 用户id=1的token:cd678b5f206c51658d7d5dffd82e6980|

请求示例：
正式环境:
http://47.52.101.29/app1/user/login?token=cd678b5f206c51658d7d5dffd82e6980
测试环境:
http://47.52.101.29/app1/user/login?id=1

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": [
        {
        	"token": "cd678b5f206c51658d7d5dffd82e6980", // 正式环境没有这个属性
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
| data.token 		 | token	| 该用户的token，线上接口无该条目		|
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
| data.ctime    | 创建时间 | 类型为unix timestamp                |
| data.utime    | 更新时间 | 类型为unix timestamp                |
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

|      字段     |   名称   |                 说明                |
|---------------|----------|-------------------------------------|
| code          | 状态码   | 0:正常                              |
| msg           | 消息     | 请求正常为"ok",否则为详细的错误信息 |
| data.token 		 | token	| 该用户的token，线上接口无该条目		|
| data.user.id       | ID       |                                     |
| data.user.name     | 昵称     |                                     |
| data.user.ctime    | 创建时间 | 类型为unix timestamp                |
| data.user.utime    | 更新时间 | 类型为unix timestamp                |
| data.user.signture | 签名     | 方便测试，临时token==signture                                    |
| data.user.status   | 状态     | 0:正常                              |
| data.user.sex      | 性别     | 0:外星人,1:男,2:女                  |
| data.user.avatar   | 头像     |                                     |
