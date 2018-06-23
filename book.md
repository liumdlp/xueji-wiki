## 书籍(book)

+ [响应状态码](#响应状态码表)
+ 方法列表
    + [添加](#添加)
	+ [详情](#详情)
    + [移除](#移除)
    + [详情(带分类)](#详情带分类)




### 响应状态码表

|  code  |        说明        |
| ------ | ------------------ |
| 333201 | 书籍不存在         |
| 333202 | 分类不存在         |
| 333203 | 自定义书籍添加失败 |
| 333204 | 加入分类失败       |
| 333205 | 书籍添加失败       |
| 333206 | 书籍移除失败       |

### 添加

uri: app1/book/add

params:

|    变量   |     名称     | 必填 |  类型  |                       描述                      |
| --------- | ------------ | ---- | ------ | ----------------------------------------------- |
| type      | 添加方式     | 是   | string | isbn: 通过isbn号添加书籍,custom: 添加自定义书籍 |
| add       | 是否加入分类 | 否   | string | Y: 加入分类 N: (默认)不加入分类                 |
| cid       | 分类id       | 否   | int    | 书籍加入的分类的id，不传则加入默认分类          |
| isbn      | ISBN码       | 否   | int    | 默认：0, **当type=="isbn"时必填**               |
| title     | 标题         | 否   | string | 书籍名称  **当type=="custom"时必填**            |
| img       | 封面图片     | 否   | string | 书籍封面图片地址                                |
| author    | 作者         | 否   | string | json格式数组，第一作者放在第一个                |
| publisher | 出版商       | 否   | string |                                                 |
| pubdate   | 出版时间     | 否   | string |                                                 |
| pages     | 页数         | 否   | int    | 默认为0                                         |



请求示例：http://47.52.101.29/app1/book/add?isbn=9787020033430

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "id": 46,
        "title": "哈利·波特与凤凰社",
        "isbn": 9787020043279,
        "cover_img": "https://img3.doubanio.com/view/subject/m/public/s1822013.jpg",
        "author_first": "[英] J. K. 罗琳",
        "author_all": "[\"[\\u82f1] J. K. \\u7f57\\u7433\"]",
        "publisher": "人民文学出版社",
        "pubdate": "2003-9",
        "douban_id": 1013129,
        "pages": 575,
        "ctime": 1528272404,
        "created_by": 1
    }
}
```

<a name="add_book_resp">response 说明：</a>

|        字段       |   名称   |                               说明                               |
| ----------------- | -------- | ---------------------------------------------------------------- |
| code              | 状态码   | 0:正常,333201:书籍不存在,333204:加入分类失败                     |
| msg               | 消息     | 请求正常为"ok",否则为详细错误信息                                |
| data.id           | 书籍id   |                                                                  |
| data.title        | 书名     |                                                                  |
| data.isbn         | ISBN码   |                                                                  |
| data.cover_img    | 封面     | 封面URL地址                                                      |
| data.author_first | 作者     | 多作者情况下，取第一位作者                                       |
| data.author_all   | 作者     | 全部作者，json格式                                               |
| data.publisher    | 出版社   |                                                                  |
| data.pubdate      | 出版时间 |                                                                  |
| data.douban_id    | 豆瓣id   | 对应豆瓣api的ID                                                  |
| data.pages        | 页书     | 书籍总页书                                                       |
| data.created_by   | 用户id   | 自定义书籍为用户id，豆瓣扫码添加的书籍为第一次扫这本书的用户的id |
| data.ctime        | 创建时间 | 改书籍录入时间(自定义和豆瓣api)                                  |



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
        "created_by": 0,
        "ctime": 0
    }
}
```

response 说明：
同 <a href="#add_book_resp">添加</a>

### 移除

uri: app1/book/remove

params:

| 变量 |  名称  | 必填 | 类型 | 描述 |
| ---- | ------ | ---- | ---- | ---- |
| id   | 书籍ID | 是   | int        ||

请求示例：http://47.52.101.29/app1/book/remove?id=50

response:

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "book_id": 50
    }
}
```

response 说明：

|     字段     |     名称     |                说明               |
| ------------ | ------------ | --------------------------------- |
| code         | 状态码       |                                   |
| msg          | 消息         | 请求正常为"ok",否则为详细错误信息 |
| data.book_id | 被删除书籍id |                                   |



### 详情(带分类)

uri: app1/book/detail

params:

| 变量 |  名称  | 必填 | 类型 | 描述 |
| ---- | ------ | ---- | ---- | ---- |
| id   | 书籍ID | 是   | int        ||

请求示例：http://47.52.101.29/app1/book/my_detail?id=1

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
        "created_by": 0,
        "ctime": 0
    }
}
```

response 说明：
同 <a href="#add_book_resp">添加</a>