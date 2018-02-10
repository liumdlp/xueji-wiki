## 复习(review)

+ [响应状态码](#响应状态码表)
+ 方法列表
    + [详情](#详情)
    + [列表(指定天数)](#列表指定天数)


### 响应状态码表

|  code  |      说明      |
| ------ | -------------- |
| 333701 | 复习计划不存在 |
| 333702 | 时间格式错误   |



### 详情

uri: app1/review/detail

params:

| 变量 |    名称    | 必填 | 类型 | 描述 |
| ---- | ---------- | ---- | ---- | ---- |
| rid  | 复习计划id | 是   | int  |      |


请求示例：http://47.52.101.29/app1/review/detail?rid=3


response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "id": 3,
        "learn_id": 7,
        "book_id": 1,
        "reminder": "记得好好复习第3行",
        "status": 0,
        "step1": "2018-01-29 15:10:00",
        "step2": "2018-01-29 15:50:00",
        "step3": "2018-01-30 14:50:00",
        "step4": "2018-01-31 14:50:00",
        "step5": "2018-02-03 14:50:00",
        "step6": "2018-02-05 14:50:00",
        "step7": "2018-02-13 14:50:00",
        "step8": "2018-02-28 14:50:00",
        "step9": "2018-03-30 14:50:00",
        "user_id": 1
    }
}
```

response 说明:

|      字段      |        名称       |                         说明                        |
| -------------- | ----------------- | --------------------------------------------------- |
| code           | 状态码            | 0:正常,其余见[响应状态码表](#响应状态码表)          |
| msg            | 消息              | 请求正常为"ok",否则为详细错误信息                   |
| data.id        | 复习纪录id        |                                                     |
| data.learn_id  | 学习记录id        |                                                     |
| data.book_id   | 学习的书籍id      |                                                     |
| data.reminder  | 复习备注          |                                                     |
| data.step[1-9] | 第[1-9]次复习时间 |                                                     |
| data.status    | 复习阶段          | 0:未开始 1: 已完成第一阶段  ... 9:已完成所有9个阶段 |
| data.user_id   | 用户id            |                                                     |



### 列表(指定天数)

uri: app1/review/range

params:

|  变量 |   名称   | 必填 | 类型 |                     描述                    |
| ----- | -------- | ---- | ---- | ------------------------------------------- |
| bdate | 开始日期 | 是   | int  | 例如20180201                                |
| range | 查询长度 | 是   | int  | 从开始日期开始要查询多少天，默认为一星期(7) |


请求示例：http://47.52.101.29/app1/review/range?bdate=20180201&range=7


response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "20180201": [],
        "20180202": [
            {
                "book": {
                    "id": 1,
                    "title": "围城",
                    "cover_img": "https://img3.doubanio.com/mpic/s1070222.jpg"
                },
                "learn": {
                    "id": 7,
                    "reminder": "记得好好复习第3行",
                    "beg_page": 10,
                    "end_page": 11
                },
                "review": {
                    "id": 3,
                    "step": 5,
                    "time": "2018-02-03 14:50:00",
                    "hm": "14:50"
                }
            },
            {
                "book": {
                    "id": 1,
                    "title": "围城",
                    "cover_img": "https://img3.doubanio.com/mpic/s1070222.jpg"
                },
                "learn": {
                    "id": 8,
                    "reminder": " 又学习了一条",
                    "beg_page": 92,
                    "end_page": 93
                },
                "review": {
                    "id": 4,
                    "step": 5,
                    "time": "2018-02-03 14:50:00",
                    "hm": "14:50"
                }
            }
        ],
        "20180204": [],
        "20180207": [
            {
                "book": {
                    "id": 1,
                    "title": "围城",
                    "cover_img": "https://img3.doubanio.com/mpic/s1070222.jpg"
                },
                "learn": {
                    "id": 7,
                    "reminder": "记得好好复习第3行",
                    "beg_page": 10,
                    "end_page": 11
                },
                "review": {
                    "id": 3,
                    "step": 6,
                    "time": "2018-02-05 14:50:00",
                    "hm": "14:50"
                }
            },
            {
                "book": {
                    "id": 1,
                    "title": "围城",
                    "cover_img": "https://img3.doubanio.com/mpic/s1070222.jpg"
                },
                "learn": {
                    "id": 8,
                    "reminder": " 又学习了一条",
                    "beg_page": 92,
                    "end_page": 93
                },
                "review": {
                    "id": 4,
                    "step": 6,
                    "time": "2018-02-05 14:50:00",
                    "hm": "14:50"
                }
            }
        ],
        "20180211": [],
        "20180216": [],
        "20180222": []
    }
}
```

response 说明:

|           字段           |     名称     |                    说明                    |
| ------------------------ | ------------ | ------------------------------------------ |
| code                     | 状态码       | 0:正常,其余见[响应状态码表](#响应状态码表) |
| msg                      | 消息         | 请求正常为"ok",否则为详细错误信息          |
| data.日期.book           | 书籍信息     |                                            |
| data.日期.book.id        | 书籍id       |                                            |
| data.日期.book.title     | 书名         |                                            |
| data.日期.book.cover_img | 封面图片     |                                            |
| data.日期.learn          | 学习记录     |                                            |
| data.日期.learn.id       | 学习记录id   |                                            |
| data.日期.learn.reminder | 复习备注     |                                            |
| data.日期.learn.beg_page | 学习开始页码 |                                            |
| data.日期.learn.end_page | 学习结束页码 |                                            |
| data.日期.review         | 复习记录     |                                            |
| data.日期.review.id      | 复习id       |                                            |
| data.日期.review.step    | 复习阶段     |                                            |
| data.日期.review.time    | 复习提醒时间 | 也是复习开始时间                           |
| data.日期.review.hm      | 时间         | 截取的   小时:分钟                         |
