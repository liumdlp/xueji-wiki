## 统计(report)

+ [响应状态码](#响应状态码表)
+ 方法列表
    + [周目标完成情况](#周目标完成情况)
    + [个人全部统计(书籍)](#个人全部统计书籍)


### 响应状态码表

|  code  |      说明      |
| ------ | -------------- |
| 333801 | 用户无学习记录 |
|        |                |

### 周目标完成情况

uri: app1/report/week_stat

params:

| 变量 | 名称 | 必填 |  类型  |                 描述                 |
| ---- | ---- | ---- | ------ | ------------------------------------ |
| date | 日期 | 否   | string | 查询该日期所在周情况，例如：20180318 |

请求示例：
http://47.52.101.29/app1/report/week_stat?date=20180318

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
            "page": {
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
| data.cur_week_stat.page.goal    | 目标学习页数         |                                   |
| data.cur_week_stat.page.done    | 已学习页数           |                                   |
| data.cur_week_stat.page.rate    | 占百分比             | int                               |


### 个人全部统计(书籍)

uri: app1/report/all_by_book

params:

| 变量 | 名称 | 必填 | 类型 | 描述 |
| ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |

请求示例：
http://47.52.101.29/app1/report/all_by_book

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
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
            "2": {
                "id": 2,
                "title": "PHP7内核剖析",
                "isbn": 9787121328107,
                "cover_img": "https://img3.doubanio.com/mpic/s29607420.jpg",
                "author_first": "秦朋",
                "author_all": "[\"\\u79e6\\u670b\"]",
                "publisher": "电子工业出版社",
                "pubdate": "2017-10-1",
                "douban_id": 27197032,
                "pages": 0,
                "ctime": 0,
                "user_id": null
            }
        },
        "pack": {
            "sum": {
                "page_count": 93,
                "time_count": 3480
            },
            "book": {
                "0": {
                    "page_count": -2,
                    "time_count": 0
                },
                "1": {
                    "page_count": 75,
                    "time_count": 3300
                },
                "2": {
                    "page_count": 19,
                    "time_count": 0
                },
                "5": {
                    "page_count": 1,
                    "time_count": 180
                }
            },
            "day": {
                "2018-01-05": {
                    "list": {
                        "2": {
                            "page_count": 19,
                            "time_count": 0
                        }
                    },
                    "sum": {
                        "page_count": 19,
                        "time_count": 0
                    }
                },
                "2018-02-11": {
                    "list": {
                        "1": {
                            "page_count": 7,
                            "time_count": 0
                        }
                    },
                    "sum": {
                        "page_count": 7,
                        "time_count": 0
                    }
                },
                "2018-03-05": {
                    "list": [
                        {
                            "page_count": -2,
                            "time_count": 0
                        }
                    ],
                    "sum": {
                        "page_count": -2,
                        "time_count": 0
                    }
                },
                "2018-03-11": {
                    "list": {
                        "1": {
                            "page_count": 2,
                            "time_count": 360
                        }
                    },
                    "sum": {
                        "page_count": 2,
                        "time_count": 360
                    }
                },
                "2018-03-12": {
                    "list": {
                        "1": {
                            "page_count": 55,
                            "time_count": 960
                        }
                    },
                    "sum": {
                        "page_count": 55,
                        "time_count": 960
                    }
                },
                "2018-03-18": {
                    "list": {
                        "1": {
                            "page_count": 11,
                            "time_count": 1980
                        },
                        "5": {
                            "page_count": 1,
                            "time_count": 180
                        }
                    },
                    "sum": {
                        "page_count": 12,
                        "time_count": 2160
                    }
                }
            },
            "week": {
                "2018-01": {
                    "list": {
                        "2": {
                            "page_count": 19,
                            "time_count": 0
                        }
                    },
                    "sum": {
                        "page_count": 19,
                        "time_count": 0
                    }
                },
                "2018-06": {
                    "list": {
                        "1": {
                            "page_count": 7,
                            "time_count": 0
                        }
                    },
                    "sum": {
                        "page_count": 7,
                        "time_count": 0
                    }
                },
                "2018-10": {
                    "list": [
                        {
                            "page_count": -2,
                            "time_count": 0
                        },
                        {
                            "page_count": 2,
                            "time_count": 360
                        }
                    ],
                    "sum": {
                        "page_count": 0,
                        "time_count": 360
                    }
                },
                "2018-11": {
                    "list": {
                        "1": {
                            "page_count": 66,
                            "time_count": 2940
                        },
                        "5": {
                            "page_count": 1,
                            "time_count": 180
                        }
                    },
                    "sum": {
                        "page_count": 67,
                        "time_count": 3120
                    }
                }
            },
            "month": {
                "2018-01": {
                    "list": {
                        "2": {
                            "page_count": 19,
                            "time_count": 0
                        }
                    },
                    "sum": {
                        "page_count": 19,
                        "time_count": 0
                    }
                },
                "2018-02": {
                    "list": {
                        "1": {
                            "page_count": 7,
                            "time_count": 0
                        }
                    },
                    "sum": {
                        "page_count": 7,
                        "time_count": 0
                    }
                },
                "2018-03": {
                    "list": {
                        "0": {
                            "page_count": -2,
                            "time_count": 0
                        },
                        "1": {
                            "page_count": 68,
                            "time_count": 3300
                        },
                        "5": {
                            "page_count": 1,
                            "time_count": 180
                        }
                    },
                    "sum": {
                        "page_count": 67,
                        "time_count": 3480
                    }
                }
            }
        }
    }
}
```

response 说明:

|                字段                |     名称     |                    说明                    |
| ---------------------------------- | ------------ | :----------------------------------------- |
| code                               | 状态码       | 0:正常,其余见[响应状态码表](#响应状态码表) |
| msg                                | 消息         | 请求正常为"ok",否则为详细错误信息          |
| data.book                          | 书籍         | 同书籍详情                                 |
| data.pack.sum.page_count           | 学习页数合计 | 从注册开始                                 |
| data.pack.sum.time_count           | 学习时间合计 | 从注册开始，单位:分钟                      |
| data.pack.book.(书籍id).page_count | 学习页数合计 | 当前书籍，key为书籍id                      |
| data.pack.book.(书籍id).time_count | 学习时间合计 | 当前书籍，key为书籍id                      |
| data.pack.day.(日期).page_count    |              |                                            |
| data.pack.day.(日期).time_count    |              |                                            |
| data.pack.week.(第几周).page_count |              | 年-周序号                                  |
| data.pack.week.(第几周).time_count |              |                                            |
| data.pack.month.(月份).page_count  |              |                                            |
| data.pack.month.(月份).time_count  |              |                                            |

