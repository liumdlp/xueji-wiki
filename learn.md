## 学习(learn)

+ [响应状态码](#响应状态码表)
+ 方法列表
    + [记录](#记录)


### 响应状态码表

|  code  |       说明       |
| ------ | ---------------- |
| 333401 | 书籍不存在       |
| 333402 | 记录失败         |
| 333403 | 起止页码非法     |
| 333404 | 复习计划创建失败 |


### 记录

uri: app1/learn/log

params:

|   变量   |     名称     | 必填 |  类型  |               描述               |
| -------- | ------------ | ---- | ------ | -------------------------------- |
| bid      | 书籍ID       | 是   | int    | 默认：0                          |
| btime    | 学习开始时间 | 是   | int    | unixtimestamp                    |
| etime    | 学习结束时间 | 是   | int    | unixtimestamp                    |
| bpage    | 开始页码     | 是   | int    | 默认为1                          |
| epage    | 结束页码     | 是   | int    |                                  |
| review   | 复习计划开关 | 否   | int    | 0:不添加复习计划（默认）  1:添加 |
| reminder | 备注         | 否   | string | 150字max                         |


请求示例：

```shell
curl -X POST \
  http://47.52.101.29/app1/learn/log \
  -H 'content-type: application/x-www-form-urlencoded' \
  -d 'token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoiMSJ9.NOIs16yZ06eG53KuE68AjBnL5j_VpGaHfcG0Lo00f4M&bid=1&btime=1517226600&etime=1517237400&bpage=10&epage=11&review=1&reminder=%E8%AE%B0%E5%BE%97%E5%A5%BD%E5%A5%BD%E5%A4%8D%E4%B9%A0%E7%AC%AC%E4%B8%89%E8%A1%8C'
```

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "learn_id": 6,
        "review": {
            "step1": "2018-01-30 05:10:00",
            "step2": "2018-01-30 05:50:00",
            "step3": "2018-01-30 22:50:00",
            "step4": "2018-01-31 22:50:00",
            "step5": "2018-02-03 22:50:00",
            "step6": "2018-02-05 22:50:00",
            "step7": "2018-02-13 22:50:00",
            "step8": "2018-02-28 22:50:00",
            "step9": "2018-03-30 22:50:00",
            "learn_id": 6,
            "book_id": 1,
            "reminder": "记得好好复习第三行",
            "status": 0,
            "user_id": 1,
            "id": 4
        }
    }
}
```

<a name="add_book_resp">response 说明：</a>

|          字段         |        名称       |                         说明                        |
| --------------------- | ----------------- | --------------------------------------------------- |
| code                  | 状态码            | 0:正常,其余见[响应状态码表](#响应状态码表)          |
| msg                   | 消息              | 请求正常为"ok",否则为详细错误信息                   |
| data.learn_id         | 学习记录id        |                                                     |
| data.review.id        | 复习纪录id        |                                                     |
| data.review.step[1-9] | 第[1-9]次复习时间 |                                                     |
| data.review.book_id   | 学习的书籍id      |                                                     |
| data.review.reminder  | 复习备注          |                                                     |
| data.review.status    | 复习阶段          | 0:未开始 1: 已完成第一阶段  ... 9:已完成所有9个阶段 |
| data.review.user_id   | 用户id            |                                                     |
