## 首页(book)

+ [响应状态码](#响应状态码表)
+ 方法列表
	+ [主页](#主页)
    + [我的](#我的)
    + [我的(详情)](#我的详情)


### 响应状态码表

|  code  |    说明    |
| ------ | ---------- |
| 333501 | 分类不存在 |


### 主页

uri: app1/main/index

params:

| 变量 |   名称   | 必填 | 类型 |   描述   |
| ---- | -------- | ---- | ---- | -------- |
| page | 页码     | 否   | int  | 默认：1  |
| num  | 单页条数 | 否   | int  | 默认：20 |


请求示例：http://47.52.101.29/app1/main/index?page=1&num=20

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "count": 2,
        "list": [
            {
                "id": 3,
                "name": "php",
                "user_id": 1,
                "ctime": 1513569517,
                "utime": 1513569517,
                "is_deleted": 0,
                "sort": 1,
                "book_list": [
                    {
                        "id": 7,
                        "title": "三体",
                        "cover_img": "https://img1.doubanio.com/mpic/s2768378.jpg"
                    }
                ],
                "book_count": 1
            },
            {
                "id": 2,
                "name": "日语",
                "user_id": 1,
                "ctime": 1513569372,
                "utime": 1513569372,
                "is_deleted": 0,
                "sort": 2,
                "book_list": [
                    {
                        "id": 3,
                        "title": "钢铁是怎样炼成的（教育部新编语文教材推荐阅读书系）",
                        "cover_img": "https://img1.doubanio.com/mpic/s29639427.jpg"
                    },
                    {
                        "id": 1,
                        "title": "围城",
                        "cover_img": "https://img3.doubanio.com/mpic/s1070222.jpg"
                    },
                    {
                        "id": 44,
                        "title": "高等数学下册讲义",
                        "cover_img": "/public/static/img/180102_001.jpg"
                    }
                ],
                "book_count": 3
            }
        ],
        "recent_learn": [
            {
                "id": 1,
                "title": "围城",
                "cover_img": "https://img3.doubanio.com/mpic/s1070222.jpg"
            },
            {
                "id": 2,
                "title": "PHP7内核剖析",
                "cover_img": "https://img3.doubanio.com/mpic/s29607420.jpg"
            }
        ]
    }
}
```


response 说明：

|              字段             |    名称    |                 说明                 |
| ----------------------------- | ---------- | ------------------------------------ |
| code                          | 状态码     | 0:正常                               |
| msg                           | 消息       | 请求正常为"ok",否则为详细错误信息    |
| data.count                    | 总数       | 本次查询包含的分类条数               |
| data.list.id                  | 分类id     |                                      |
| data.list.name                | 分类名称   |                                      |
| data.list.uid                 | 用户id     |                                      |
| data.list.ctime               | 创建时间   | 创建该条分类的时间（unix timestamp） |
| data.list.utime               | 更新时间   | 该条目的最后更新时间                 |
| data.list.is_deleted          | 是否被删除 | 0:未删除,1:已删除                    |
| data.list.book_count          | 书籍数目   | 当前分类下所含书籍合计数目           |
| data.list.book_list           | 书籍列表   | 当前分类下包含的书籍列表             |
| data.list.book_list.id        | 书籍id     |                                      |
| data.list.book_list.title     | 书籍名称   |                                      |
| data.list.book_list.cover_img | 书籍封面   |                                      |
| data.recent_learn.id          | 书籍id     | 最近学习的书籍id                     |
| data.recent_learn.title       | 书籍名称   | 最近学习的书籍标题                   |
| data.recent_learn.cover_img   | 书籍封面   | 最近学习的书籍封面                   |



### 我的

uri: app1/main/my

params:

| 变量 | 名称 | 必填 |  类型  |           描述           |
| ---- | ---- | ---- | ------ | ------------------------ |
| date | 时间 | 否   | string | 格式yyyy-mm-dd, 默认当天 |

请求示例：http://47.52.101.29/app1/main/my

response:
```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "head": {
            "continuous_days": 0,
            "beg_long": "",
            "latest": "",
            "latest_long": "",
            "week_learned_flag": [
                {
                    "date": "2018-05-26",
                    "learned": false
                }
            ],
            "username": "刘先森",
            "avatar": "/static/123.png"
        },
        "week_goal": {
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
        "report": {
            "day": [
                {
                    "day": "2018-05-26",
                    "sum": {
                        "page_count": 0,
                        "time_count": 0
                    },
                    "book": []
                }
            ],
            "week": [
                {
                    "week": "2018-15",
                    "sum": {
                        "page_count": 188,
                        "time_count": 480
                    },
                    "book": [
                        {
                            "page_count": 89,
                            "time_count": 420,
                            "id": 1,
                            "book_color": "#1AADBD"
                        },
                        {
                            "page_count": 99,
                            "time_count": 60,
                            "id": 3,
                            "book_color": "#1AADBD"
                        }
                    ]
                }
            ],
            "month": [
                {
                    "month": "2018-04",
                    "sum": {
                        "page_count": 348,
                        "time_count": 840
                    },
                    "book": [
                        {
                            "page_count": 249,
                            "time_count": 780,
                            "id": 1,
                            "book_color": "#1AADBD"
                        },
                        {
                            "page_count": 99,
                            "time_count": 60,
                            "id": 3,
                            "book_color": "#1AADBD"
                        }
                    ]
                }
            ],
            "sum": {
                "sum": {
                    "page_count": 485,
                    "time_count": 4560
                },
                "book": [
                    {
                        "id": 1,
                        "page_count": 343,
                        "time_count": 4080,
                        "book_color": "#1AADBD"
                    },
                    {
                        "id": 3,
                        "page_count": 142,
                        "time_count": 480,
                        "book_color": "#1AADBD"
                    }
                ],
                "first5_time": [
                    {
                        "id": 1,
                        "book_color": "#1AADBD",
                        "title": "围城"
                    },
                    {
                        "id": 3,
                        "book_color": "#D3AA7E",
                        "title": "钢铁是怎样炼成的（教育部新编语文教材推荐阅读书系）"
                    }
                ],
                "first5_page": [
                    {
                        "id": 1,
                        "book_color": "#1AADBD",
                        "title": "围城"
                    },
                    {
                        "id": 3,
                        "book_color": "#D3AA7E",
                        "title": "钢铁是怎样炼成的（教育部新编语文教材推荐阅读书系）"
                    }
                ]
            },
            "max": {
                "time": {
                    "day": 0,
                    "week": 180,
                    "month": 3480
                },
                "page": {
                    "day": 0,
                    "week": 99,
                    "month": 348
                }
            }
        }
    }
}
```

response 说明：

|                     字段                    |          名称          |                说明               |
| ------------------------------------------- | ---------------------- | --------------------------------- |
| code                                        | 状态码                 | 0:正常                            |
| msg                                         | 消息                   | 请求正常为"ok",否则为详细错误信息 |
| **头部部分**                                | \-                     | \-                                |
| data.head{}                                 | 头部部分               |                                   |
| data.head.continuous_days                   | 连续学习天数           |                                   |
| data.head.beg_long                          | 本次连续学习开始日期   |                                   |
| data.head.latest                            | 最后一次学习时间       |                                   |
| data.head.latest_long                       | 最后一次学习时间       | 完整格式                          |
| data.head.username                          | 用户昵称               |                                   |
| data.head.avatar                            | 用户头像               |                                   |
| **头部部分 --> 一周学习情况**               | \-                     | \-                                |
| data.head.week_learned_flag[]               | 一周学习情况           | 顺序：周一到周日                  |
| data.head.week_learned_flag.date            | 日期                   |                                   |
| data.head.week_learned_flag.learned         | boolean,是否学习       | true: 当天有学习记录              |
| **周目标部分**                              | \-                     | \-                                |
| data.week_goal{}                            | 周目标部分             |                                   |
| data.week_goal.time.goal                    | 目标学习时间           | 单位:分钟                         |
| data.week_goal.time.done                    | 已学习时间             | 单位:分钟                         |
| data.week_goal.time.rate                    | 占百分比               | int                               |
| data.week_goal.pages.goal                   | 目标学习页数           |                                   |
| data.week_goal.pages.done                   | 已学习页数             |                                   |
| data.week_goal.pages.rate                   | 占百分比               | int                               |
| **数据报告**                                | \-                     | \-                                |
| **数据报告 --> 合计部分**                   | \-                     | \-                                |
| data.report.sum.sum.page_count              | 学习页数合计           | 从注册开始                        |
| data.report.sum.sum.time_count              | 学习时间合计           | 从注册开始，单位:分钟             |
| **数据报告 --> 合计部分 --> 书籍**          | \-                     | \-                                |
| data.report.sum.book.id                     | 书籍id                 |                                   |
| data.report.sum.book.book_color             | 书籍颜色               |                                   |
| data.report.sum.book.page_count             | 学习页数合计           |                                   |
| data.report.sum.book.time_count             | 学习时间合计           |                                   |
| **数据报告 --> 合计部分 --> 前5排序**       | \-                     | \-                                |
| data.report.sum.book.first5_time.id         | 学习时间前5的书籍id    |                                   |
| data.report.sum.book.first5_time.book_color | 书籍颜色               |                                   |
| data.report.sum.book.first5_time.title      | 书籍名称               |                                   |
| data.report.sum.book.first5_page.id         | 学习页书前5的书籍id    |                                   |
| data.report.sum.book.first5_page.book_color | 书籍颜色               |                                   |
| data.report.sum.book.first5_page.title      | 书籍名称               |                                   |
| **数据报告 --> 图表部分 --> 最大数**       | \-                     | \-                                |
| data.report.max.time.day                    | 本次查询日最大学习时间 |                                   |
| data.report.max.time.week                   | 本次查询周最大学习时间 |                                   |
| data.report.max.time.month                  | 本次查询月最大学习时间 |                                   |
| data.report.max.page.day                    | 本次查询日最大学习页数 |                                   |
| data.report.max.page.week                   | 本次查询周最大学习页数 |                                   |
| data.report.max.page.month                  | 本次查询月最大学习页数 |                                   |
| **数据报告 --> 分天计算**                   | \-                     | \-                                |
| data.report.day.day                         | 日期                   |                                   |
| data.report.day.sum.page_count              | 学习页数合计           | 当天学习页数合计                  |
| data.report.day.sum.time_count              | 学习时间合计           | 当天学习时间合计                  |
| **数据报告 --> 分天计算 --> 书籍**          | \-                     | \-                                |
| data.report.day.book.id                     | 书籍id                 |                                   |
| data.report.day.book.book_color             | 书籍颜色               |                                   |
| data.report.day.book.page_count             | 学习页数合计           | 当天单本书学习页数合计            |
| data.report.day.book.time_count             | 学习时间合计           | 当天单本书学习时间合计            |
| **数据报告 --> 分周**                       | \-                     | \-                                |
| data.report.week{}                          | \-                     | 结构同单天                        |
| data.report.week.week                       | 周序号                 | 例如: 2018-06 为2018年第6周       |
| **数据报告 --> 分月**                       | \-                     | \-                                |
| data.report.month{}                         | \-                     | 结构同单天                        |
| data.report.month.month                     | 月序号                 | 例如: 2018-02 为2018年2月         |
| **匹配信息部分，书籍详情&&分类详情**        | \-                     | \-                                |
| data.book.color                             | 书籍颜色               |                                   |
| data.category{"分类id":分类详情{}}          | 分类                   | 同[分类详情](category.md#列表)    |




### 我的(详情)

uri: app1/main/my_detail

params:

|    变量   |  名称  | 必填 |  类型  |              描述              |
| --------- | ------ | ---- | ------ | ------------------------------ |
| calc_type | 维度1  | 否   | string | BOOK:书籍(默认)  CATEGORY:分类 |
| cid       | 分类id | 否   | int    | 指定分类id                     |
| time_dim  | 维度2  | 否   | string | DAY:日(默认) WEEK:周 MONTH:月  |
| page      | 分页   | 否   | int    | 默认为0，步长位7(天周月)       |

请求示例：http://47.52.101.29/app1/main/my_detail?calc_type=CATEGORY&cid=2&time_dim=DAY&page=10

response:
```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "report": [

            // 日维度的分类
            {
                "day": "2018-04-14",
                "sum": {
                    "page_count": 0,
                    "time_count": 0
                },
                "category": []
            },
            ...

            // 周维度的书籍
            {
                "week": "2018-25",
                "sum": {
                    "page_count": 0,
                    "time_count": 0
                },
                "book": []
            },
            ...

            // 月维度的分类
            {
                "month": "2018-04",
                "sum": {
                    "page_count": 0,
                    "time_count": 0
                },
                "category": []
            },

        ],
        "max": {
            "time": 420,
            "page": 89
        },
        "btm_list": [
            {
                "category_id": 21,  // key = (category_id 或 book_id)
                "name": "数学",
                "pic": "",          // 分类无封面图片,此处为空
                "color": "#488F62",
                "day": [            // key = (day 或 week 或 month)
                    {
                        "time_count": 0,
                        "page_count": 0
                    },
                    {
                        "time_count": 180,
                        "page_count": 99
                    },
                    {
                        "time_count": 60,
                        "page_count": 30
                    },
                    {
                        "time_count": 0,
                        "page_count": 0
                    },
                    {
                        "time_count": 0,
                        "page_count": 0
                    },
                    {
                        "time_count": 0,
                        "page_count": 0
                    },
                    {
                        "time_count": 0,
                        "page_count": 0
                    }
                ]
            }
        ],
        "category_list": [
            {
                "id": 20,
                "name": "默认分类"
            }
        ]
    }
}
```