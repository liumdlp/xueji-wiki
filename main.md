## 首页(book)

+ [响应状态码](#响应状态码表)
+ 方法列表
	+ [主页](#主页)
    + [我的](#我的)


### 响应状态码表

| code | 说明 |
| ---- | ---- |
| \-   | \-   |


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

| 变量 | 名称 | 必填 | 类型 | 描述 |
| ---- | ---- | ---- | ---- | ---- |
| \-   | \-   | \-   | \-   | \-   |

请求示例：http://47.52.101.29/app1/main/my

response:
```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "head": {
            "continuous_days": 1,
            "beg_long": "2018-05-02 14:51:02",
            "latest": 20180502,
            "latest_long": "2018-05-02 14:51:02",
            "week_learned_flag": [
                {
                    "date": "2018-04-30",
                    "learned": false
                },
                {
                    "date": "2018-05-01",
                    "learned": false
                },
                {
                    "date": "2018-05-02",
                    "learned": true
                },
                {
                    "date": "2018-05-03",
                    "learned": false
                },
                {
                    "date": "2018-05-04",
                    "learned": false
                },
                {
                    "date": "2018-05-05",
                    "learned": false
                },
                {
                    "date": "2018-05-06",
                    "learned": false
                }
            ]
        },
        "week_goal": {
            "time": {
                "goal": 0,
                "done": 120,
                "rate": 0
            },
            "pages": {
                "goal": 0,
                "done": 19,
                "rate": 0
            }
        },
        "report": {
            "sum": {
                "page_count": 466,
                "time_count": 4440
            },
            "book": [
                {
                    "id": 1,
                    "page_count": 343,
                    "time_count": 4080
                }
            ],
            "category": [
                {
                    "id": 2,
                    "page_count": 466,
                    "time_count": 4440
                }
            ],
            "day": [
                {
                    "day": "2018-01-05",
                    "sum": {
                        "page_count": 19,
                        "time_count": 0
                    },
                    "book": [
                        {
                            "page_count": 19,
                            "time_count": 0,
                            "id": 1
                        }
                    ],
                    "category": [
                        {
                            "page_count": 19,
                            "time_count": 0,
                            "id": 2
                        }
                    ]
                },
            ],
            "week": [
                {
                    "week": "2018-01",
                    "sum": {
                        "page_count": 19,
                        "time_count": 0
                    },
                    "book": [
                        {
                            "page_count": 19,
                            "time_count": 0,
                            "id": 1
                        }
                    ],
                    "category": [
                        {
                            "page_count": 19,
                            "time_count": 0,
                            "id": 2
                        }
                    ]
                }
            ],
            "month": [
                {
                    "month": "2018-01",
                    "sum": {
                        "page_count": 19,
                        "time_count": 0
                    },
                    "book": [
                        {
                            "page_count": 19,
                            "time_count": 0,
                            "id": 1
                        }
                    ],
                    "category": [
                        {
                            "page_count": 19,
                            "time_count": 0,
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
                "created_by": null,
                "color": "#1AADBD"
            }
        }
    }
}
```

response 说明：

|                 字段                 |         名称         |                   说明                  |
| ------------------------------------ | -------------------- | --------------------------------------- |
| code                                 | 状态码               | 0:正常                                  |
| msg                                  | 消息                 | 请求正常为"ok",否则为详细错误信息       |
| **头部部分**                         | \-                   | \-                                      |
| data.head{}                          | 头部部分             |                                         |
| data.head.continuous_days            | 连续学习天数         |                                         |
| data.head.beg_long                   | 本次连续学习开始日期 |                                         |
| data.head.latest                     | 最后一次学习时间     |                                         |
| data.head.latest_long                | 最后一次学习时间     | 完整格式                                |
| **头部部分 --> 一周学习情况**        | \-                   | \-                                      |
| data.head.week_learned_flag[]        | 一周学习情况         | 顺序：周一到周日                        |
| data.head.week_learned_flag.date     | 日期                 |                                         |
| data.head.week_learned_flag.learned  | boolean,是否学习     | true: 当天有学习记录                    |
| **周目标部分**                       | \-                   | \-                                      |
| data.week_goal{}                     | 周目标部分           |                                         |
| data.week_goal.time.goal             | 目标学习时间         | 单位:分钟                               |
| data.week_goal.time.done             | 已学习时间           | 单位:分钟                               |
| data.week_goal.time.rate             | 占百分比             | int                                     |
| data.week_goal.pages.goal            | 目标学习页数         |                                         |
| data.week_goal.pages.done            | 已学习页数           |                                         |
| data.week_goal.pages.rate            | 占百分比             | int                                     |
| **合计部分**                         | \-                   | \-                                      |
| data.report.sum.page_count           | 学习页数合计         | 从注册开始                              |
| data.report.sum.time_count           | 学习时间合计         | 从注册开始，单位:分钟                   |
| **合计部分 --> 书籍**                | \-                   | \-                                      |
| data.report.book.id                  | 书籍id               |                                         |
| data.report.book.page_count          | 学习页数合计         |                                         |
| data.report.book.time_count          | 学习时间合计         |                                         |
| **合计部分 --> 分类**                | \-                   | \-                                      |
| data.report.category.id              | 分类id               | 指定分类id会出现                        |
| data.report.category.page_count      | 学习页数合计         |                                         |
| data.report.category.time_count      | 学习时间合计         |                                         |
| **分天计算**                         | \-                   | \-                                      |
| data.report.day.day                  | 日期                 |                                         |
| data.report.day.sum.page_count       | 学习页数合计         | 当天学习页数合计                        |
| data.report.day.sum.time_count       | 学习时间合计         | 当天学习时间合计                        |
| **分天计算 --> 书籍**                | \-                   | \-                                      |
| data.report.day.book.id              | 书籍id               |                                         |
| data.report.day.book.page_count      | 学习页数合计         | 当天单本书学习页数合计                  |
| data.report.day.book.time_count      | 学习时间合计         | 当天单本书学习时间合计                  |
| **分天计算 --> 分类**                | \-                   | \-                                      |
| data.report.day.category.id          | 分类id               | 当天单分类学习页数合计                  |
| data.report.day.category.page_count  | 学习页数合计         | 当天单分类学习页数合计                  |
| data.report.day.category.time_count  | 学习时间合计         | 当天单分类学习时间合计                  |
| **分周部分**                         | \-                   | \-                                      |
| data.report.week{}                   |                      | 结构同单天，例如：2018-06 为2018年第6周 |
| **分月部分**                         | \-                   | \-                                      |
| data.report.month{}                  |                      | 结构同单天，例如：2018-02为2018年2月份  |
| **匹配信息部分，书籍详情&&分类详情** | \-                   | \-                                      |
| data.book                            | 书籍                 | 同[书籍详情](book.md#详情)              |
| data.book.color                      | 书籍颜色             |                                         |
| data.category                        | 分类                 | 同[分类详情](category.md#列表)          |