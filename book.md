## 书籍(book)

+ [响应状态码](#响应状态码表)
+ 方法列表
	+ [isbn添加](#isbn添加)
	+ [自定义添加](#自定义添加)
	+ [详情](#详情)



### 响应状态码表

|  code  |        说明        |
| ------ | ------------------ |
| 333201 | 书籍不存在         |
| 333202 | 分类不存在         |
| 333203 | 自定义书籍添加失败 |
| 333204 | 加入分类失败       |

### isbn添加

uri: app1/book/add

params:

| 变量 |  名称  | 必填 | 类型 |        描述        |
| ---- | ------ | ---- | ---- | ------------------ |
| isbn | ISBN码 | 是   | int  | 默认：0            |
| cid  | 分类id | 是   | int  | 书籍加入的分类的id |


请求示例：http://47.52.101.29/app1/book/add?isbn=9787020033430

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "id": 39,
        "title": "哈利·波特与魔法石",
        "isbn": 9787020033430,
        "cover_img": "https://img3.doubanio.com/mpic/s1990480.jpg",
        "author_first": "[英] J. K. 罗琳",
        "author_all": "[\"[\\u82f1] J. K. \\u7f57\\u7433\"]",
        "publisher": "人民文学出版社",
        "pubdate": "2000-9",
        "douban_id": 1041007,
        "pages": 0,
        "user_id": 0,
        "ctime": 0,
    }
}
```

<a name="add_book_resp">response 说明：</a>

|        字段       |   名称   |                     说明                     |
| ----------------- | -------- | -------------------------------------------- |
| code              | 状态码   | 0:正常,333201:书籍不存在,333204:加入分类失败 |
| msg               | 消息     | 请求正常为"ok",否则为详细错误信息            |
| data.id           | 书籍id   |                                              |
| data.title        | 书名     |                                              |
| data.isbn         | ISBN码   |                                              |
| data.cover_img    | 封面     | 封面URL地址                                  |
| data.author_first | 作者     | 多作者情况下，取第一位作者                   |
| data.author_all   | 作者     | 全部作者，json格式                           |
| data.publisher    | 出版社   |                                              |
| data.pubdate      | 出版时间 |                                              |
| data.douban_id    | 豆瓣id   | 对应豆瓣api的ID                              |
| data.pages        | 页书     | 书籍总页书                                   |
| data.user_id      | 用户id   | 自定义书籍为用户id，豆瓣扫码添加的书籍为0    |
| data.ctime        | 创建时间 | 改书籍录入时间(自定义和豆瓣api)              |



### 自定义添加

uri: app1/book/add_custom

params:

|    变量   |   名称   | 必填 |  类型  |               描述               |
| --------- | -------- | ---- | ------ | -------------------------------- |
| title     | 标题     | 是   | string | 书籍名称                         |
| cid       | 分类id   | 是   | int    | 加入的分类id                     |
| img       | 封面图片 | 否   | string | 书籍封面图片地址                 |
| author    | 作者     | 否   | string | json格式数组，第一作者放在第一个 |
| publisher | 出版商   | 否   | string |                                  |
| pubdate   | 出版时间 | 否   | string |                                  |
| pages     | 页数     | 否   | int    | 默认为0                          |

请求示例：

```
curl -X POST http://47.52.101.29/app1/book/add_custom -H 'content-type: application/x-www-form-urlencoded' -d 'token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxfQ.-QqHe1NOuVz8hpMDRm5CZfWT6SWh1R38mwNkjCOj34o&title=%E9%AB%98%E7%AD%89%E6%95%B0%E5%AD%A6%E4%B8%8B%E5%86%8C%E8%AE%B2%E4%B9%89&img=%2Fpublic%2Fstatic%2Fimg%2F180102_001.jpg&author=%5B%22%E4%BA%8E%E5%8A%A0%E4%BA%94%22%2C%22%E4%BA%8E%E5%8A%A0%E5%85%AD%22%5D&publisher=%E5%8C%97%E4%BA%AC%E6%9C%89%E7%94%B5%E5%87%BA%E7%89%88%E7%A4%BE&pubdate=2018-01-12&pages=530&cid=2'
```

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "id": 44
    }
}
```

response 说明：

|   字段  |   名称   |                      说明                     |
| ------- | -------- | --------------------------------------------- |
| code    | 状态码   | 333203:自定义书籍添加失败,333204:加入分类失败 |
| msg     | 响应信息 |                                               |
| data.id | 书籍id   | 新增书籍id                                    |


### 详情

uri: app1/book/detail

params:

| 变量 |  名称  | 必填 | 类型 | 描述 |
| ---- | ------ | ---- | ---- | ---- |
| id   | 书籍ID | 是   | int        ||

请求示例：http://47.52.101.29/app1/book/detail?id=1

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
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
        "user_id": 0,
        "ctime": 0
    }
}
```

response 说明：
同 <a href="#add_book_resp">isbn添加</a>


