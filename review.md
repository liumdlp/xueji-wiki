## 复习(review)

+ [响应状态码](#响应状态码表)
+ 方法列表
    + [详情](#详情)
    + [列表(指定天数)](#列表指定天数)
    + [标记复习完成](#标记复习完成)


### 响应状态码表

|  code  |       说明       |
| ------ | ---------------- |
| 333701 | 复习计划不存在   |
| 333702 | 时间格式错误     |
| 333703 | 非法复习阶段     |
| 333704 | 复习条目不存在   |
| 333705 | 已经复习过该阶段 |
| 333706 | 复习信息记录失败 |




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

|      字段      |            名称           |                         说明                        |
| -------------- | ------------------------- | --------------------------------------------------- |
| code           | 状态码                    | 0:正常,其余见[响应状态码表](#响应状态码表)          |
| msg            | 消息                      | 请求正常为"ok",否则为详细错误信息                   |
| data.id        | 复习纪录id                |                                                     |
| data.learn_id  | 学习记录id                |                                                     |
| data.book_id   | 学习的书籍id              |                                                     |
| data.reminder  | 复习备注                  |                                                     |
| data.step[1-9] | 第[1-9]次复习时间         |                                                     |
| data.status    | (已合并至learn表)复习阶段 | 0:未开始 1: 已完成第一阶段  ... 9:已完成所有9个阶段 |
| data.user_id   | 用户id                    |                                                     |



### 列表(指定天数)

uri: app1/review/range

params:

|  变量 |   名称   | 必填 | 类型 |                     描述                    |
| ----- | -------- | ---- | ---- | ------------------------------------------- |
| bdate | 开始日期 | 否   | int  | 例如20180206，默认当前周                                |
| range | 查询长度 | 否   | int  | 从开始日期开始要查询多少天，默认为一星期(7) |


请求示例：http://47.52.101.29/app1/review/range?bdate=20180206&range=7


response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": [
        {
            "date": "2018-04-15 00:00:00",
            "week_seq": 0,
            "review_count": 0,
            "content": []
        },
        {
            "date": "2018-04-16 00:00:00",
            "week_seq": 1,
            "review_count": 0,
            "content": []
        },
        {
            "date": "2018-04-17 00:00:00",
            "week_seq": 2,
            "review_count": 0,
            "content": []
        },
        {
            "date": "2018-04-18 00:00:00",
            "week_seq": 3,
            "review_count": 0,
            "content": []
        },
        {
            "date": "2018-04-19 00:00:00",
            "week_seq": 4,
            "review_count": 0,
            "content": []
        },
        {
            "date": "2018-04-20 00:00:00",
            "week_seq": 5,
            "review_count": 0,
            "content": []
        },
        {
            "date": "2018-04-21 00:00:00",
            "week_seq": 6,
            "review_count": 1,
            "content": [
                {
                    "bookid": 1,
                    "booktitle": "围城",
                    "bookcover_img": "https://img3.doubanio.com/mpic/s1070222.jpg",
                    "learnid": 32,
                    "learnreminder": "2018/4/7 12:00:00 ~ 2018/4/7 15:00:00 学习围城(id=1) p20~100 并加入复习计划",
                    "learnbeg_page": 20,
                    "learnend_page": 100,
                    "reviewid": 23,
                    "reviewstep": 7,
                    "reviewtime": "2018-04-22 15:00:00",
                    "reviewhm": "15:00",
                    "review": {
                        "id": 23,
                        "step": [
                            "2018-04-07 15:20:00",
                            "2018-04-07 16:00:00",
                            "2018-04-08 15:00:00",
                            "2018-04-09 15:00:00",
                            "2018-04-12 15:00:00",
                            "2018-04-14 15:00:00",
                            "2018-04-22 15:00:00",
                            "2018-05-07 15:00:00",
                            "2018-06-06 15:00:00"
                        ]
                    }
                }
            ]
        }
    ]
}
```

response 说明:

|             字段             |     名称     |                    说明                    |
| ---------------------------- | ------------ | ------------------------------------------ |
| code                         | 状态码       | 0:正常,其余见[响应状态码表](#响应状态码表) |
| msg                          | 消息         | 请求正常为"ok",否则为详细错误信息          |
| data[].date                  | 日期         |   YYYY-mm-dd HH:ii:ss                                         |
| data[].week_seq              | 星期几       | int, 0（表示星期天）到 6（表示星期六）     |
| data[].review_count          | 复习条数     | 当前日期需要复习的条数                     |
| data[].content.bookid        | 书籍id       |                                            |
| data[].content.booktitle     | 书名         |                                            |
| data[].content.bookcover_img | 封面图片     |                                            |
| data[].content.learnid       | 学习记录id   |                                            |
| data[].content.learnreminder | 复习备注     |                                            |
| data[].content.learnbeg_page | 学习开始页码 |                                            |
| data[].content.learnend_page | 学习结束页码 |                                            |
| data[].content.reviewid      | 复习纪录id   |                                            |
| data[].content.reviewstep    | 复习阶段     |                                            |
| data[].content.reviewtime    | 复习提醒时间 | 也是复习开始时间                           |
| data[].content.reviewhm      | 时间         | 截取的   小时:分钟                         |
| data[].content.review.id     | 复习计划id   |                                            |
| data[].content.review.step   | 复习步骤     | 0-8共9步骤                                 |




### 标记复习完成

uri: app1/review/done

params:

| 变量 |    名称    | 必填 | 类型 |    描述   |
| ---- | ---------- | ---- | ---- | --------- |
| id   | 复习计划id | 是   | int  | review.id |
| step | 复习阶段   | 是   | int  | 0-9       |


请求示例：http://47.52.101.29/app1/review/done?id=2&step=1


response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": []
}
```

response 说明:

| 字段 |  名称  |                    说明                    |
| ---- | ------ | ------------------------------------------ |
| code | 状态码 | 0:正常,其余见[响应状态码表](#响应状态码表) |
| msg  | 消息   | 请求正常为"ok",否则为详细错误信息          |