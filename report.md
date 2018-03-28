## 统计(report)

+ [响应状态码](#响应状态码表)
+ 方法列表
    + [连续学习时间周目标完成情况](#连续学习时间周目标完成情况)
    + [合计(书籍)](#合计书籍)
    + [周目标达成情况](#周目标达成情况)


### 响应状态码表

|  code  |      说明      |
| ------ | -------------- |
| 333801 | 用户无学习记录 |

### 连续学习时间周目标完成情况

uri: app1/report/continuous_days

params:

| 变量 | 名称 | 必填 |  类型  |                 描述                 |
| ---- | ---- | ---- | ------ | ------------------------------------ |
| date | 日期 | 否   | string | 查询该日期所在周情况，例如：20180318 |

请求示例：
http://47.52.101.29/app1/report/continuous_days?date=20180318

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "continuous": {
            "continuous_days": 1,
            "beg_long": "2018-03-18 15:19:23",
            "latest": 20180318,
            "latest_long": "2018-03-18 15:19:23"
        },
        "cur_week_stat": {
            "time": {
                "goal": 600,
                "done": 3120,
                "rate": 520
            },
            "pages": {
                "goal": 300,
                "done": 67,
                "rate": 22
            }
        }
    }
}
```

response 说明:

|               字段              |         名称         |                说明               |
| ------------------------------- | -------------------- | --------------------------------- |
| code                            | 状态码               | 0:正常                            |
| msg                             | 消息                 | 请求正常为"ok",否则为详细错误信息 |
| data.continuous.continuous_days | 连续学习天数         |                                   |
| data.continuous.beg_long        | 本次连续学习开始日期 |                                   |
| data.continuous.latest          | 最后一次学习时间     |                                   |
| data.continuous.latest_long     | 最后一次学习时间     | 完整格式                          |
| data.cur_week_stat.time.goal    | 目标学习时间         | 单位:分钟                         |
| data.cur_week_stat.time.done    | 已学习时间           | 单位:分钟                         |
| data.cur_week_stat.time.rate    | 占百分比             | int                               |
| data.cur_week_stat.pages.goal   | 目标学习页数         |                                   |
| data.cur_week_stat.pages.done   | 已学习页数           |                                   |
| data.cur_week_stat.pages.rate   | 占百分比             | int                               |


### 合计(书籍)

uri: app1/report/all_by_book

params:

|  变量 |   名称   | 必填 |  类型  |                       描述                       |
| ----- | -------- | ---- | ------ | ------------------------------------------------ |
| cid   | 分类id   | 否   | int    | 只展示该分类下的书籍，默认展示全部               |
| btime | 开始时间 | 否   | string | 筛选周期内的学习记录，开始时间，例如：20180202 |
| etime | 结束时间 | 否   | string | 结束时间                                         |

请求示例：
http://47.52.101.29/app1/report/all_by_book

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "report": {
            "sum": {
                "page_count": 80,
                "time_count": 3480
            },
            "book": [
                {
                    "id": 1,
                    "page_count": 75,
                    "time_count": 3300
                },
                {
                    "id": 3,
                    "page_count": 5,
                    "time_count": 180
                }
            ],
            "category": [
                {
                    "id": 2,
                    "page_count": 80,
                    "time_count": 3480
                }
            ],
            "day": [
                {
                    "day": "2018-02-11",
                    "sum": {
                        "page_count": 7,
                        "time_count": 0
                    },
                    "book": [
                        {
                            "page_count": 7,
                            "time_count": 0,
                            "id": 1
                        }
                    ],
                    "category": [
                        {
                            "page_count": 7,
                            "time_count": 0,
                            "id": 2
                        }
                    ]
                },
                {
                    "day": "2018-03-05",
                    "sum": {
                        "page_count": 4,
                        "time_count": 0
                    },
                    "book": [
                        {
                            "page_count": 4,
                            "time_count": 0,
                            "id": 3
                        }
                    ],
                    "category": [
                        {
                            "page_count": 4,
                            "time_count": 0,
                            "id": 2
                        }
                    ]
                },
                {
                    "day": "2018-03-11",
                    "sum": {
                        "page_count": 2,
                        "time_count": 360
                    },
                    "book": [
                        {
                            "page_count": 2,
                            "time_count": 360,
                            "id": 1
                        }
                    ],
                    "category": [
                        {
                            "page_count": 2,
                            "time_count": 360,
                            "id": 2
                        }
                    ]
                },
                {
                    "day": "2018-03-12",
                    "sum": {
                        "page_count": 55,
                        "time_count": 960
                    },
                    "book": [
                        {
                            "page_count": 55,
                            "time_count": 960,
                            "id": 1
                        }
                    ],
                    "category": [
                        {
                            "page_count": 55,
                            "time_count": 960,
                            "id": 2
                        }
                    ]
                },
                {
                    "day": "2018-03-18",
                    "sum": {
                        "page_count": 12,
                        "time_count": 2160
                    },
                    "book": [
                        {
                            "page_count": 11,
                            "time_count": 1980,
                            "id": 1
                        },
                        {
                            "page_count": 1,
                            "time_count": 180,
                            "id": 3
                        }
                    ],
                    "category": [
                        {
                            "page_count": 12,
                            "time_count": 2160,
                            "id": 2
                        }
                    ]
                }
            ],
            "week": [
                {
                    "week": "2018-06",
                    "sum": {
                        "page_count": 7,
                        "time_count": 0
                    },
                    "book": [
                        {
                            "page_count": 7,
                            "time_count": 0,
                            "id": 1
                        }
                    ],
                    "category": [
                        {
                            "page_count": 7,
                            "time_count": 0,
                            "id": 2
                        }
                    ]
                },
                {
                    "week": "2018-10",
                    "sum": {
                        "page_count": 6,
                        "time_count": 360
                    },
                    "book": [
                        {
                            "page_count": 4,
                            "time_count": 0,
                            "id": 3
                        },
                        {
                            "page_count": 2,
                            "time_count": 360,
                            "id": 1
                        }
                    ],
                    "category": [
                        {
                            "page_count": 6,
                            "time_count": 360,
                            "id": 2
                        }
                    ]
                },
                {
                    "week": "2018-11",
                    "sum": {
                        "page_count": 67,
                        "time_count": 3120
                    },
                    "book": [
                        {
                            "page_count": 66,
                            "time_count": 2940,
                            "id": 1
                        },
                        {
                            "page_count": 1,
                            "time_count": 180,
                            "id": 3
                        }
                    ],
                    "category": [
                        {
                            "page_count": 67,
                            "time_count": 3120,
                            "id": 2
                        }
                    ]
                }
            ],
            "month": [
                {
                    "month": "2018-02",
                    "sum": {
                        "page_count": 7,
                        "time_count": 0
                    },
                    "book": [
                        {
                            "page_count": 7,
                            "time_count": 0,
                            "id": 1
                        }
                    ],
                    "category": [
                        {
                            "page_count": 7,
                            "time_count": 0,
                            "id": 2
                        }
                    ]
                },
                {
                    "month": "2018-03",
                    "sum": {
                        "page_count": 73,
                        "time_count": 3480
                    },
                    "book": [
                        {
                            "page_count": 5,
                            "time_count": 180,
                            "id": 3
                        },
                        {
                            "page_count": 68,
                            "time_count": 3300,
                            "id": 1
                        }
                    ],
                    "category": [
                        {
                            "page_count": 73,
                            "time_count": 3480,
                            "id": 2
                        }
                    ]
                }
            ]
        },
        "book": {
            "1": {
                "id": 1,
                "title": "围城",
                "isbn": 9787020024759,
                "cover_img": "https://img3.doubanio.com/mpic/s1070222.jpg",
                "author_first": "钱锺书",
                "author_all": "[\"\\u94b1\\u953a\\u4e66\"]",
                "publisher": "人民文学出版社",
                "pubdate": "1991-2",
                "douban_id": 1008145,
                "pages": 0,
                "ctime": 0,
                "user_id": null
            },
            "3": {
                "id": 3,
                "title": "钢铁是怎样炼成的（教育部新编语文教材推荐阅读书系）",
                "isbn": 9787535497239,
                "cover_img": "https://img1.doubanio.com/mpic/s29639427.jpg",
                "author_first": "尼古拉·奥斯特洛夫斯基",
                "author_all": "[\"\\u5c3c\\u53e4\\u62c9\\u00b7\\u5965\\u65af\\u7279\\u6d1b\\u592b\\u65af\\u57fa\"]",
                "publisher": "长江文艺出版社",
                "pubdate": "2018-1",
                "douban_id": 27604699,
                "pages": 0,
                "ctime": 0,
                "user_id": null
            }
        },
        "category": {
            "2": {
                "id": 2,
                "name": "日语",
                "user_id": 1,
                "ctime": 1513569372,
                "utime": 1513569372,
                "is_deleted": 0,
                "sort": 2
            }
        }
    }
}
```

response 说明:

|                 字段                |     名称     |                    说明                    |
| ----------------------------------- | ------------ | :----------------------------------------- |
| code                                | 状态码       | 0:正常,其余见[响应状态码表](#响应状态码表) |
| msg                                 | 消息         | 请求正常为"ok",否则为详细错误信息          |
| 匹配信息部分，书籍详情&&分类详情    | \-           | \-                                         |
| data.report.book                    | 书籍         | 同书籍详情                                 |
| data.report.category                | 分类         | 同分类详情                                 |
| 合计部分                            | \-           | \-                                         |
| data.report.sum.page_count          | 学习页数合计 | 从注册开始                                 |
| data.report.sum.time_count          | 学习时间合计 | 从注册开始，单位:分钟                      |
| data.report.book.id                 | 书籍id       |                                            |
| data.report.book.page_count         | 学习页数合计 |                                            |
| data.report.book.time_count         | 学习时间合计 |                                            |
| data.report.category.id             | 分类id       | 指定分类id会出现                           |
| data.report.category.page_count     | 学习页数合计 |                                            |
| data.report.category.time_count     | 学习时间合计 |                                            |
| 分天计算                            | \-           | \-                                         |
| data.report.day.day                 | 日期         |                                            |
| data.report.day.sum.page_count      | 学习页数合计 | 当天学习页数合计                           |
| data.report.day.sum.time_count      | 学习时间合计 | 当天学习时间合计                           |
| data.report.day.book.id             | 书籍id       |                                            |
| data.report.day.book.page_count     | 学习页数合计 | 当天单本书学习页数合计                     |
| data.report.day.book.time_count     | 学习时间合计 | 当天单本书学习时间合计                     |
| data.report.day.category.id         | 分类id       | 当天单分类学习页数合计                     |
| data.report.day.category.page_count | 学习页数合计 | 当天单分类学习页数合计                     |
| data.report.day.category.time_count | 学习时间合计 | 当天单分类学习时间合计                     |
| 分周部分                            | \-           | \-                                         |
| data.report.week.*                  |              | 结构同单天，例如：2018-06 为2018年第6周    |
| 分月部分                            | \-           | \-                                         |
| data.report.month.*                 |              | 结构同单天，例如：2018-02为2018年2月份     |



### 周目标达成情况

uri: app1/report/week_report

params:

|  变量 |   名称   | 必填 |  类型  |                      描述                      |
| ----- | -------- | ---- | ------ | ---------------------------------------------- |
| btime | 开始时间 | 否   | string | 筛选周期内的学习记录，开始时间，例如：20180301 |
| etime | 结束时间 | 否   | string | 结束时间                                       |

请求示例：
http://47.52.101.29/app1/report/week_report?btime=20180301&etime=20180401

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "report": {
            "2018-09": {
                "time": {
                    "goal": 0,
                    "done": 0,
                    "rate": 0
                },
                "pages": {
                    "goal": 0,
                    "done": 0,
                    "rate": 0
                }
            },
            "2018-10": {
                "time": {
                    "goal": 600,
                    "done": 360,
                    "rate": 60
                },
                "pages": {
                    "goal": 300,
                    "done": 6,
                    "rate": 2
                }
            },
            "2018-11": {
                "time": {
                    "goal": 600,
                    "done": 3120,
                    "rate": 520
                },
                "pages": {
                    "goal": 300,
                    "done": 67,
                    "rate": 22
                }
            },
            "2018-12": {
                "time": {
                    "goal": 0,
                    "done": 0,
                    "rate": 0
                },
                "pages": {
                    "goal": 0,
                    "done": 0,
                    "rate": 0
                }
            },
            "2018-13": {
                "time": {
                    "goal": 0,
                    "done": 0,
                    "rate": 0
                },
                "pages": {
                    "goal": 0,
                    "done": 0,
                    "rate": 0
                }
            }
        }
    }
}
```

response 说明:

|                字段                |     名称     |                说明               |
| ---------------------------------- | ------------ | --------------------------------- |
| code                               | 状态码       | 0:正常                            |
| msg                                | 消息         | 请求正常为"ok",否则为详细错误信息 |
| data.report.(年-周序号).time.goal  | 目标学习时间 | 单位:分钟                         |
| data.report.(年-周序号).time.done  | 已学习时间   | 单位:分钟                         |
| data.report.(年-周序号).time.rate  | 占百分比     | int                               |
| data.report.(年-周序号).pages.goal | 目标学习页数 |                                   |
| data.report.(年-周序号).pages.done | 已学习页数   |                                   |
| data.report.(年-周序号).pages.rate | 占百分比     | int                               |