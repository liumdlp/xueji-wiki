## 首页(book)

+ [响应状态码](#响应状态码表)
+ 方法列表
	+ [主页](#主页)


### 响应状态码表

| code | 说明 |
| ---- | ---- |
|      |      |


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
        "count": 3,
        "list": [
            {
                "id": 4,
                "name": "考研",
                "user_id": 1,
                "ctime": 1513655026,
                "utime": 1513655026,
                "is_deleted": 0,
                "sort": 0,
                "book_list": [
                    {
                        "id": 2,
                        "title": "PHP7内核剖析",
                        "cover_img": "https://img3.doubanio.com/mpic/s29607420.jpg"
                    }
                ],
                "book_count": 1
            },
            {
                "id": 3,
                "name": "php",
                "user_id": 1,
                "ctime": 1513569517,
                "utime": 1513569517,
                "is_deleted": 0,
                "sort": 1,
                "book_list": [],
                "book_count": 0
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
                        "id": 7,
                        "title": "三体",
                        "cover_img": "https://img1.doubanio.com/mpic/s2768378.jpg"
                    }
                ],
                "book_count": 3
            }
        ],
        "recent_learn": {
            "1": {
                "id": 1,
                "title": "围城",
                "cover_img": "https://img3.doubanio.com/mpic/s1070222.jpg"
            }
        }
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
