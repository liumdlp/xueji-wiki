## 上传(upload)

+ [响应状态码](#响应状态码表)
+ 方法列表
	+ [传图](#传图)


### 响应状态码表

|  code  |     说明     |
| ------ | ------------ |
| 333601 | 图片上传失败 |


### 传图

uri: app1/upload/index

params:

| 变量 | 名称 | 必填 | 类型 | 描述 |
| ---- | ---- | ---- | ---- | ---- |
| img  | 图片 | 是   | file |      |

请求示例：
```
curl -X POST \
  http://47.52.101.29/app1/upload/index \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoiMSJ9.NOIs16yZ06eG53KuE68AjBnL5j_VpGaHfcG0Lo00f4M \
  -F img=@phone1.png
```

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "name": "1MQ5Hnzkhj7.jpg",
        "url": "http://47.52.101.29/static/upload/img/201802/08/1MQ5Hnzkhj7.jpg",
        "size": 8842
    }
}
```


response 说明：

|    字段   |   名称   |                说明               |
| --------- | -------- | --------------------------------- |
| code      | 状态码   | 0:正常                            |
| msg       | 消息     | 请求正常为"ok",否则为详细错误信息 |
| data.name | 文件名   |                                   |
| data.url  | 访问地址 |                                   |
| data.size | 分类名称 | 单位:Byte                         |
