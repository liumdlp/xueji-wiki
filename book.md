## 书籍(book)

+ [响应状态码](#响应状态码表)
+ 方法列表
	+ [isbn添加](#isbn添加)
	+ [TODO：自定义添加](#TODO自定义添加)
	+ [详情](#详情)



### 响应状态码表

|  code  |    说明    |
| ------ | ---------- |
| 333201 | 书籍不存在 |
| 333202 | 分类不存在 |

### isbn添加

uri: app1/book/add

params:

| 变量 |  名称  | 必填 |   类型  |   描述  |
| ---- | ------ | ---- | ------- | ------- |
| isbn | ISBN码 | 是   | int(13) | 默认：0 |

请求示例：http://47.52.101.29/app1/book/add_book?isbn=9787020033430

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
        "douban_id": 1041007
    }
}
```

<a name="add_book_resp">response 说明：</a>

| 字段                | 名称    | 说明                  |
| ----------------- | ----- | ------------------- |
| code              | 状态码   | 0:正常,333201:书籍不存在   |
| msg               | 消息    | 请求正常为"ok",否则为详细错误信息 |
| data.id           | 书籍id  |                     |
| data.title        | 书名    |                     |
| data.isbn         | ISBN码 |                     |
| data.cover_img    | 封面    | 封面URL地址             |
| data.author_first | 作者    | 多作者情况下，取第一位作者       |
| data.author_all   | 作者    | 全部作者，json格式         |
| data.publisher    | 出版社   |                     |
| data.pubdate      | 出版时间  |                     |
| data.douban_id    | 豆瓣id  | 对应豆瓣api的ID          |



### TODO：自定义添加

uri: app1/book/add_custom

params:

| 变量   | 名称   | 必填   | 类型   | 描述   |
| ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |

请求示例：

response:

```json
{
}
```

response 说明：

| 字段   | 名称   | 说明   |
| ---- | ---- | ---- |
|      |      |      |



### 详情

uri: app1/book/detail

params:

| 变量   | 名称   | 必填   | 类型   | 描述   |
| ---- | ---- | ---- | ---- | ---- |
|id|书籍ID|是|int||

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
        "douban_id": 1008145
    }
}
```

response 说明：
同 <a href="#add_book_resp">isbn添加</a>


