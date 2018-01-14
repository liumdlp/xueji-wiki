## 分类(category)

+ [响应状态码](#响应状态码表)
+ 方法列表
	+ [列表](#列表)
	+ [添加](#添加)
	+ [插入&更新书籍](#插入更新书籍)
	+ [排序](#排序)




### 响应状态码表

|  code  |     说明     |
| ------ | ------------ |
| 333101 | 列表不存在   |
| 333102 | 书籍查找错误 |
| 333103 | 分类排序失败 |
| 333104 | 无新数据     |


### 列表

uri: app1/category/list

params:

| 变量 |   名称   | 必填 | 类型 |   描述   |
| ---- | -------- | ---- | ---- | -------- |
| page | 页码     | 否   | int  | 默认：1  |
| num  | 单页条数 | 否   | int  | 默认：20 |

请求示例：http://47.52.101.29/app1/category/list?page=1&num=20

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "count": 4,
        "list": [
            {
                "id": 2,
                "name": "日语",
                "user_id": 1,
                "ctime": 1513569372,
                "utime": 1513569372,
                "is_deleted": 0,
                "sort": 2,
                "book_count": 2,
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
                    }
                ]
            },
            {
                "id": 5,
                "name": "默认分类",
                "user_id": 1,
                "ctime": 1515658090,
                "utime": 1515658090,
                "is_deleted": 0,
                "sort": 3,
                "book_count": 0,
                "book_list": []
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
| data.count                    | 总数       | 本次查询包含的用户分类条数           |
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


### 添加

uri: app1/category/add

params:

| 变量   | 名称   | 必填   | 类型     | 描述   |
| ---- | ---- | ---- | ------ | ---- |
| name | 分类名  | 是    | string |      |

请求示例：http://47.52.101.29/app1/category/add?name=%E8%80%83%E7%A0%94

response:

```json
{
    "code": 0,
    "msg": "分类添加成功!",
    "data": {
        "id": 4
    }
}
```

response 说明：

| 字段      | 名称   | 说明                  |
| ------- | ---- | ------------------- |
| code    | 状态码  | 0:正常                |
| msg     | 消息   | 请求正常为"ok",否则为详细错误信息 |
| data.id | 分类id | 新创建的分类id            |



### 插入&更新书籍

uri: app1/category/upd_book

params:

| 变量   | 名称      | 必填   | 类型   | 描述   |
| ---- | ------- | ---- | ---- | ---- |
| isbn | 书籍isbn码 | 是    | int  |      |
| cid  | 分类id    | 是    | int  |      |

请求示例：http://47.52.101.29/app1/category/upd_book?isbn=9787536692930&cid=2

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "category_id": 2,
        "book": {
            "id": 7,
            "title": "三体",
            "isbn": 9787536692930,
            "cover_img": "https://img1.doubanio.com/mpic/s2768378.jpg",
            "author_first": "刘慈欣",
            "author_all": "[\"\\u5218\\u6148\\u6b23\"]",
            "publisher": "重庆出版社",
            "pubdate": "2008-1",
            "douban_id": 2567698
        }
    }
}
```

response 说明：

|          字段          |    名称    |                                说明                                |
| ---------------------- | ---------- | ------------------------------------------------------------------ |
| code                   | 状态码     | 0:正常,333101:id对应列表不存在,333102:书籍查找错误,333104:无新数据 |
| msg                    | 消息       | 请求正常为"ok",否则为详细错误信息                                  |
| data.category_id       | 分类id     | 书籍添加到分类id                                                   |
| data.book.id           | 书籍id     |                                                                    |
| data.book.title        | 书籍标题   |                                                                    |
| data.book.isbn         | 书籍isbn   |                                                                    |
| data.book.cover_img    | 书籍封面图 |                                                                    |
| data.book.author_first | 作者       | 多作者情况下，取第一位作者                                         |
| data.book.author_all   | 作者       | 全部作者，json格式                                                 |
| data.book.publisher    | 出版社     |                                                                    |
| data.book.pubdate      | 出版时间   |                                                                    |
| data.book.douban_id    | 豆瓣id     | 对应的豆瓣api的id                                                  |


### 排序
uri: app1/category/sort

params:

| 变量 | 名称 | 必填 |  类型 |       描述       |
| ---- | ---- | ---- | ----- | ---------------- |
| sort | 分类 | 是   | []int | 分类id的排序数组 |

请求示例：http://47.52.101.29/app1/category/sort?sort=[4,3,2]

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": []
}
```

response 说明：

| 字段 |  名称  |                说明               |
| ---- | ------ | --------------------------------- |
| code | 状态码 | 0:正常,333103:分类排序失败        |
| msg  | 消息   | 请求正常为"ok",否则为详细错误信息 |